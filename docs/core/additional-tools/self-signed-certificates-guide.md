---
title: Общие сведения о создании самозаверяющих сертификатов
description: Обзор средства Microsoft dotnet dev-certs, добавляющего функции для проектов .NET Core и ASP.NET Core, а также другие параметры для использования самозаверяющих сертификатов.
author: angee
ms.date: 11/19/2020
ms.openlocfilehash: d1675abb7d584b72d981f9db739e02269abe662c
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189145"
---
# <a name="generate-self-signed-certificates-with-the-net-cli"></a><span data-ttu-id="e2626-103">Создание самозаверяющих сертификатов с помощью интерфейса командной строки .NET</span><span class="sxs-lookup"><span data-stu-id="e2626-103">Generate self-signed certificates with the .NET CLI</span></span>

<span data-ttu-id="e2626-104">При использовании самозаверяющих сертификатов существуют различные способы их создания и использования в сценариях разработки и тестирования.</span><span class="sxs-lookup"><span data-stu-id="e2626-104">When using self-signed certificates, there are different ways to create and use them for development and testing scenarios.</span></span>  <span data-ttu-id="e2626-105">В этом руководстве вы узнаете, как использовать самозаверяющие сертификаты с `dotnet dev-certs`, а также о других параметрах, таких как `PowerShell` и `OpenSSL`.</span><span class="sxs-lookup"><span data-stu-id="e2626-105">In this guide, you'll cover using self-signed certificates with `dotnet dev-certs`, and other options like `PowerShell` and `OpenSSL`.</span></span>

<span data-ttu-id="e2626-106">Затем можно проверить, что сертификат будет загружен, с помощью примера, такого как [приложение ASP.NET Core](https://github.com/dotnet/dotnet-docker/blob/master/samples/run-aspnetcore-https-development.md), размещенное в контейнере.</span><span class="sxs-lookup"><span data-stu-id="e2626-106">You can then validate that the certificate will load using an example such as an [ASP.NET Core app](https://github.com/dotnet/dotnet-docker/blob/master/samples/run-aspnetcore-https-development.md) hosted in a container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e2626-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="e2626-107">Prerequisites</span></span>

<span data-ttu-id="e2626-108">В этом примере можно использовать .NET Core 3.1 или .NET 5.</span><span class="sxs-lookup"><span data-stu-id="e2626-108">In the sample, you can utilize either .NET Core 3.1 or .NET 5.</span></span>

<span data-ttu-id="e2626-109">Для `dotnet dev-certs` следует убедиться в том, что установлена соответствующая версия .NET:</span><span class="sxs-lookup"><span data-stu-id="e2626-109">For `dotnet dev-certs`, be sure to have the appropriate version of .NET installed:</span></span>

* [<span data-ttu-id="e2626-110">Установка .NET в Windows</span><span class="sxs-lookup"><span data-stu-id="e2626-110">Install .NET on Windows</span></span>](../install/windows.md)
* [<span data-ttu-id="e2626-111">Установка .NET в Linux</span><span class="sxs-lookup"><span data-stu-id="e2626-111">Install .NET on Linux</span></span>](../install/linux.md)
* [<span data-ttu-id="e2626-112">Установка .NET в macOS</span><span class="sxs-lookup"><span data-stu-id="e2626-112">Install .NET on macOS</span></span>](../install/macos.md)

<span data-ttu-id="e2626-113">Для работы с этим примером требуется [Docker 17.06](https://docs.docker.com/release-notes/docker-ce) или [клиент Docker](https://www.docker.com/products/docker) более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="e2626-113">This sample requires [Docker 17.06](https://docs.docker.com/release-notes/docker-ce) or later of the [Docker client](https://www.docker.com/products/docker).</span></span>

## <a name="prepare-sample-app"></a><span data-ttu-id="e2626-114">Подготовка примера приложения</span><span class="sxs-lookup"><span data-stu-id="e2626-114">Prepare sample app</span></span>

<span data-ttu-id="e2626-115">Необходимо подготовить пример приложения в зависимости от среды выполнения, которую вы хотите использовать для тестирования, либо [.NET Core 3.1](#net-core-31-sample-app), либо [.NET 5](#net-5-sample-app).</span><span class="sxs-lookup"><span data-stu-id="e2626-115">You'll need to prepare the sample app depending on which runtime you'd like to use for testing, either [.NET Core 3.1](#net-core-31-sample-app) or [.NET 5](#net-5-sample-app).</span></span>

<span data-ttu-id="e2626-116">В рамках этого руководства вы будете использовать [пример приложения](https://hub.docker.com/_/microsoft-dotnet-samples) и внесете необходимые изменения.</span><span class="sxs-lookup"><span data-stu-id="e2626-116">For this guide, you'll use a [sample app](https://hub.docker.com/_/microsoft-dotnet-samples) and make changes where appropriate.</span></span>

### <a name="net-core-31-sample-app"></a><span data-ttu-id="e2626-117">Пример приложения .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="e2626-117">.NET Core 3.1 sample app</span></span>

<span data-ttu-id="e2626-118">Получение примера приложения.</span><span class="sxs-lookup"><span data-stu-id="e2626-118">Get the sample app.</span></span>

```console
git clone https://github.com/dotnet/dotnet-docker/
```

<span data-ttu-id="e2626-119">Перейдите в репозиторий локально и откройте рабочую область в редакторе.</span><span class="sxs-lookup"><span data-stu-id="e2626-119">Navigate to the repository locally and open up the workspace in an editor.</span></span>

> [!NOTE]
> <span data-ttu-id="e2626-120">Если вы хотите использовать параметры dotnet publish для *обрезки* развертывания, следует убедиться, что соответствующие зависимости включены для поддержки SSL-сертификатов.</span><span class="sxs-lookup"><span data-stu-id="e2626-120">If you're looking to use dotnet publish parameters to *trim* the deployment, you should make sure that the appropriate dependencies are included for supporting SSL certificates.</span></span>
<span data-ttu-id="e2626-121">Обновите файл [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj), чтобы убедиться в том, что в контейнер включены соответствующие сборки.</span><span class="sxs-lookup"><span data-stu-id="e2626-121">Update the [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) to ensure that the appropriate assemblies are included in the container.</span></span> <span data-ttu-id="e2626-122">Дополнительные сведения см. в статье, посвященной обновлению файла CSPROJ для [поддержки SSL-сертификатов](../deploying/trim-self-contained.md#support-for-ssl-certificates) при использовании усечения для автономных развертываний.</span><span class="sxs-lookup"><span data-stu-id="e2626-122">For reference, check how to update the .csproj file to [support ssl certificates](../deploying/trim-self-contained.md#support-for-ssl-certificates) when using trimming for self-contained deployments.</span></span>

<span data-ttu-id="e2626-123">Убедитесь, что `aspnetapp.csproj` включает соответствующую целевую платформу:</span><span class="sxs-lookup"><span data-stu-id="e2626-123">Make sure the `aspnetapp.csproj` includes the appropriate target framework:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>.netcoreapp3.1</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

<span data-ttu-id="e2626-124">Измените Dockerfile, чтобы среда выполнения указывала на .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="e2626-124">Modify the Dockerfile to make sure the runtime points to .NET Core 3.1:</span></span>

```Dockerfile
# https://hub.docker.com/_/microsoft-dotnet-core
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /source

# copy csproj and restore as distinct layers
COPY *.sln .
COPY aspnetapp/*.csproj ./aspnetapp/
RUN dotnet restore

# copy everything else and build app
COPY aspnetapp/. ./aspnetapp/
WORKDIR /source/aspnetapp
RUN dotnet publish -c release -o /app --no-restore

# final stage/image
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT ["dotnet", "aspnetapp.dll"]
```

<span data-ttu-id="e2626-125">Убедитесь, что вы указали на пример приложения.</span><span class="sxs-lookup"><span data-stu-id="e2626-125">Make sure you're pointing to the sample app.</span></span>

```console
cd .\dotnet-docker\samples\aspnetapp
```

<span data-ttu-id="e2626-126">Создайте контейнер для локального тестирования.</span><span class="sxs-lookup"><span data-stu-id="e2626-126">Build the container for testing locally.</span></span>

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

### <a name="net-5-sample-app"></a><span data-ttu-id="e2626-127">Пример приложения .NET 5</span><span class="sxs-lookup"><span data-stu-id="e2626-127">.NET 5 sample app</span></span>

<span data-ttu-id="e2626-128">В рамках этого руководства [пример aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) следует проверить на предмет использования .NET 5.</span><span class="sxs-lookup"><span data-stu-id="e2626-128">For this guide, the [sample aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) should be checked for .NET 5.</span></span>

<span data-ttu-id="e2626-129">Проверьте пример приложения [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/Dockerfile) на предмет использования .NET 5.</span><span class="sxs-lookup"><span data-stu-id="e2626-129">Check sample app [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/Dockerfile) is using .NET 5.</span></span>

<span data-ttu-id="e2626-130">В зависимости от ОС узла может потребоваться обновить среду выполнения ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e2626-130">Depending on the host OS, the ASP.NET runtime may need to be updated.</span></span> <span data-ttu-id="e2626-131">Например, изменение с `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` на `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` в Dockerfile поможет выбрать соответствующую среду выполнения Windows.</span><span class="sxs-lookup"><span data-stu-id="e2626-131">For example, changing from `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` to `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` in the Dockerfile will help with targeting the appropriate Windows runtime.</span></span>

<span data-ttu-id="e2626-132">Например, это поможет при тестировании сертификатов в Windows:</span><span class="sxs-lookup"><span data-stu-id="e2626-132">For example, this will help with testing the certificates on Windows:</span></span>

```Dockerfile
# https://hub.docker.com/_/microsoft-dotnet
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /source

# copy csproj and restore as distinct layers
COPY *.sln .
COPY aspnetapp/*.csproj ./aspnetapp/
RUN dotnet restore -r win-x64

# copy everything else and build app
COPY aspnetapp/. ./aspnetapp/
WORKDIR /source/aspnetapp
RUN dotnet publish -c release -o /app -r win-x64 --self-contained false --no-restore

# final stage/image
# Uses the 2009 release; 2004, 1909, and 1809 are other choices
FROM mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT ["aspnetapp"]

```

<span data-ttu-id="e2626-133">Если вы тестируете сертификаты в Linux, можно использовать существующий Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="e2626-133">If we're testing the certificates on Linux, you can use the existing Dockerfile.</span></span>

<span data-ttu-id="e2626-134">Убедитесь, что `aspnetapp.csproj` включает соответствующую целевую платформу:</span><span class="sxs-lookup"><span data-stu-id="e2626-134">Make sure the `aspnetapp.csproj` includes the appropriate target framework:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

> [!NOTE]
> <span data-ttu-id="e2626-135">Если вы хотите использовать параметры `dotnet publish` для *обрезки* развертывания, убедитесь, что соответствующие зависимости включены для поддержки SSL-сертификатов.</span><span class="sxs-lookup"><span data-stu-id="e2626-135">If you want to use `dotnet publish` parameters to *trim* the deployment, make sure that the appropriate dependencies are included for supporting SSL certificates.</span></span>
<span data-ttu-id="e2626-136">Обновите файл [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj), чтобы убедиться в том, что в контейнер включены соответствующие сборки.</span><span class="sxs-lookup"><span data-stu-id="e2626-136">Update the [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) to ensure that the appropriate assemblies are included in the container.</span></span> <span data-ttu-id="e2626-137">Дополнительные сведения см. в статье, посвященной обновлению файла CSPROJ для [поддержки SSL-сертификатов](../deploying/trim-self-contained.md#support-for-ssl-certificates) при использовании усечения для автономных развертываний.</span><span class="sxs-lookup"><span data-stu-id="e2626-137">For reference, check how to update the .csproj file to [support ssl certificates](../deploying/trim-self-contained.md#support-for-ssl-certificates) when using trimming for self-contained deployments.</span></span>

<span data-ttu-id="e2626-138">Убедитесь, что вы указали на пример приложения.</span><span class="sxs-lookup"><span data-stu-id="e2626-138">Make sure you're pointing to the sample app.</span></span>

```console
cd .\dotnet-docker\samples\aspnetapp
```

<span data-ttu-id="e2626-139">Создайте контейнер для локального тестирования.</span><span class="sxs-lookup"><span data-stu-id="e2626-139">Build the container for testing locally.</span></span>

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

## <a name="create-a-self-signed-certificate"></a><span data-ttu-id="e2626-140">Создание самозаверяющего сертификата.</span><span class="sxs-lookup"><span data-stu-id="e2626-140">Create a self-signed certificate</span></span>

<span data-ttu-id="e2626-141">Самозаверяющий сертификат можно создать:</span><span class="sxs-lookup"><span data-stu-id="e2626-141">You can create a self-signed certificate:</span></span>

- [<span data-ttu-id="e2626-142">С помощью dotnet dev-certs</span><span class="sxs-lookup"><span data-stu-id="e2626-142">With dotnet dev-certs</span></span>](#with-dotnet-dev-certs)
- [<span data-ttu-id="e2626-143">С помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2626-143">With PowerShell</span></span>](#with-powershell)
- [<span data-ttu-id="e2626-144">С помощью OpenSSL</span><span class="sxs-lookup"><span data-stu-id="e2626-144">With OpenSSL</span></span>](#with-openssl)

### <a name="with-dotnet-dev-certs"></a><span data-ttu-id="e2626-145">С помощью dotnet dev-certs</span><span class="sxs-lookup"><span data-stu-id="e2626-145">With dotnet dev-certs</span></span>

<span data-ttu-id="e2626-146">Для работы с самозаверяющими сертификатами можно использовать `dotnet dev-certs`.</span><span class="sxs-lookup"><span data-stu-id="e2626-146">You can use `dotnet dev-certs` to work with self-signed certificates.</span></span> <span data-ttu-id="e2626-147">В этом примере используется консоль PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2626-147">This example uses a PowerShell console.</span></span>

```console
dotnet dev-certs https -ep $env:USERPROFILE\.aspnet\https\aspnetapp.pfx -p crypticpassword
dotnet dev-certs https --trust
```

> [!NOTE]
> <span data-ttu-id="e2626-148">Имя сертификата, в данном случае *aspnetapp*.pfx, должно совпадать с именем сборки проекта.</span><span class="sxs-lookup"><span data-stu-id="e2626-148">The certificate name, in this case *aspnetapp*.pfx must match the project assembly name.</span></span> <span data-ttu-id="e2626-149">`crypticpassword` используется в качестве замены пароля на ваш выбор.</span><span class="sxs-lookup"><span data-stu-id="e2626-149">`crypticpassword` is used as a stand-in for a password of your own choosing.</span></span> <span data-ttu-id="e2626-150">Если консоль возвращает сообщение "Допустимый HTTPS-сертификат уже существует", то в вашем хранилище уже есть доверенный сертификат.</span><span class="sxs-lookup"><span data-stu-id="e2626-150">If console returns "A valid HTTPS certificate is already present.", a trusted certificate already exists in your store.</span></span> <span data-ttu-id="e2626-151">Его можно экспортировать с помощью консоли MMC.</span><span class="sxs-lookup"><span data-stu-id="e2626-151">It can be exported using MMC Console.</span></span>

<span data-ttu-id="e2626-152">Настройте секреты приложения для сертификата:</span><span class="sxs-lookup"><span data-stu-id="e2626-152">Configure application secrets, for the certificate:</span></span>

```console
dotnet user-secrets -p aspnetapp\aspnetapp.csproj set "Kestrel:Certificates:Development:Password" "crypticpassword"
```

> [!NOTE]
> <span data-ttu-id="e2626-153">Примечание. Пароль должен совпадать с паролем, используемым для сертификата.</span><span class="sxs-lookup"><span data-stu-id="e2626-153">Note: The password must match the password used for the certificate.</span></span>

<span data-ttu-id="e2626-154">Запустите образ контейнера с ASP.NET Core, настроенным для HTTPS:</span><span class="sxs-lookup"><span data-stu-id="e2626-154">Run the container image with ASP.NET Core configured for HTTPS:</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -v $env:APPDATA\microsoft\UserSecrets\:C:\Users\ContainerUser\AppData\Roaming\microsoft\UserSecrets -v $env:USERPROFILE\.aspnet\https:C:\Users\ContainerUser\AppData\Roaming\ASP.NET\Https mcr.microsoft.com/dotnet/samples:aspnetapp
```

<span data-ttu-id="e2626-155">После запуска приложения перейдите по адресу `https://localhost:8001` в веб-браузере.</span><span class="sxs-lookup"><span data-stu-id="e2626-155">Once the application starts, navigate to `https://localhost:8001` in your web browser.</span></span>

#### <a name="clean-up"></a><span data-ttu-id="e2626-156">Очистка</span><span class="sxs-lookup"><span data-stu-id="e2626-156">Clean up</span></span>

<span data-ttu-id="e2626-157">Если секреты и сертификаты не используются, обязательно очистите их.</span><span class="sxs-lookup"><span data-stu-id="e2626-157">If the secrets and certificates are not in use, be sure to clean them up.</span></span>

```console
dotnet user-secrets remove "Kestrel:Certificates:Development:Password" -p aspnetapp\aspnetapp.csproj
dotnet dev-certs https --clean
```

### <a name="with-powershell"></a><span data-ttu-id="e2626-158">С помощью PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2626-158">With PowerShell</span></span>

<span data-ttu-id="e2626-159">Для создания самозаверяющих сертификатов можно использовать PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2626-159">You can use PowerShell to generate self-signed certificates.</span></span> <span data-ttu-id="e2626-160">[Клиент PKI](/powershell/module/pkiclient/new-selfsignedcertificate?preserve-view=true&view=win10-ps) можно использовать для создания самозаверяющего сертификата.</span><span class="sxs-lookup"><span data-stu-id="e2626-160">The [PKI Client](/powershell/module/pkiclient/new-selfsignedcertificate?preserve-view=true&view=win10-ps) can be used to generate a self-signed certificate.</span></span>

```powershell
$cert = New-SelfSignedCertificate -DnsName @("contoso.com", "www.contoso.com") -CertStoreLocation "cert:\LocalMachine\My"
```

<span data-ttu-id="e2626-161">Сертификат будет создан, однако в целях тестирования следует поместить его в хранилище сертификатов для тестирования в браузере.</span><span class="sxs-lookup"><span data-stu-id="e2626-161">The certificate will be generated, but for the purposes of testing, should be placed in a cert store for testing in a browser.</span></span>

```powershell
$certKeyPath = "c:\certs\contoso.com.pfx"
$password = ConvertTo-SecureString 'password' -AsPlainText -Force
$cert | Export-PfxCertificate -FilePath $certKeyPath -Password $password
$rootCert = $(Import-PfxCertificate -FilePath $certKeyPath -CertStoreLocation 'Cert:\LocalMachine\Root' -Password $password)
```

<span data-ttu-id="e2626-162">На этом этапе сертификаты должны быть доступны для просмотра с помощью [оснастки консоли управления](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="e2626-162">At this point, the certificates should be viewable from an [MMC snap-in](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

<span data-ttu-id="e2626-163">Вы можете запустить образец контейнера в подсистеме Windows для Linux (WSL):</span><span class="sxs-lookup"><span data-stu-id="e2626-163">You can run the sample container in Windows Subsystem for Linux (WSL):</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> <span data-ttu-id="e2626-164">Обратите внимание, что при подключении тома путь к файлу может обрабатываться по-разному на основе узла.</span><span class="sxs-lookup"><span data-stu-id="e2626-164">Note that with the volume mount the file path could be handled differently based on host.</span></span>  <span data-ttu-id="e2626-165">Например, в WSL мы можем заменить */c/certs* на */mnt/c/certs*.</span><span class="sxs-lookup"><span data-stu-id="e2626-165">For example, in WSL we may replace */c/certs* with */mnt/c/certs*.</span></span>

<span data-ttu-id="e2626-166">Если вы используете контейнер, созданный ранее для Windows, команда run должна выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="e2626-166">If you're using the container built earlier for Windows, the run command would look like the following:</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="e2626-167">Когда приложение откроется, перейдите по адресу contoso.com:8001 в браузере.</span><span class="sxs-lookup"><span data-stu-id="e2626-167">Once the application is up, navigate to contoso.com:8001 in a browser.</span></span>

<span data-ttu-id="e2626-168">Убедитесь, что записи узла обновлены, чтобы `contoso.com` отвечал на соответствующий IP-адрес (например, 127.0.0.1).</span><span class="sxs-lookup"><span data-stu-id="e2626-168">Be sure that the host entries are updated for `contoso.com` to answer on  the appropriate ip address (for example 127.0.0.1).</span></span> <span data-ttu-id="e2626-169">Если сертификат не распознан, убедитесь, что сертификат, загружаемый вместе с контейнером, также является доверенным для узла, а также что для `contoso.com` имеются соответствующие записи SAN/DNS.</span><span class="sxs-lookup"><span data-stu-id="e2626-169">If the certificate isn't recognized, make sure that the certificate that is loaded with the container is also trusted on the host, and that there's appropriate SAN / DNS entries for `contoso.com`.</span></span>

#### <a name="clean-up"></a><span data-ttu-id="e2626-170">Очистка</span><span class="sxs-lookup"><span data-stu-id="e2626-170">Clean up</span></span>

```powershell
$cert | Remove-Item
Get-ChildItem $certFilePath | Remove-Item
$rootCert | Remove-item
```

### <a name="with-openssl"></a><span data-ttu-id="e2626-171">С помощью OpenSSL</span><span class="sxs-lookup"><span data-stu-id="e2626-171">With OpenSSL</span></span>

<span data-ttu-id="e2626-172">Для создания самозаверяющих сертификатов можно использовать [OpenSSL](https://www.openssl.org/).</span><span class="sxs-lookup"><span data-stu-id="e2626-172">You can use [OpenSSL](https://www.openssl.org/) to create self-signed certificates.</span></span> <span data-ttu-id="e2626-173">В этом примере будет использоваться WSL/Ubuntu и оболочка bash с `OpenSSL`.</span><span class="sxs-lookup"><span data-stu-id="e2626-173">This example will use WSL / Ubuntu and a bash shell with `OpenSSL`.</span></span>

<span data-ttu-id="e2626-174">При этом будут созданы файлы CRT и KEY.</span><span class="sxs-lookup"><span data-stu-id="e2626-174">This will generate a .crt and a .key.</span></span>

```bash
PARENT="contoso.com"
openssl req \
-x509 \
-newkey rsa:4096 \
-sha256 \
-days 365 \
-nodes \
-keyout $PARENT.key \
-out $PARENT.crt \
-subj "/CN=${PARENT}" \
-extensions v3_ca \
-extensions v3_req \
-config <( \
  echo '[req]'; \
  echo 'default_bits= 4096'; \
  echo 'distinguished_name=req'; \
  echo 'x509_extension = v3_ca'; \
  echo 'req_extensions = v3_req'; \
  echo '[v3_req]'; \
  echo 'basicConstraints = CA:FALSE'; \
  echo 'keyUsage = nonRepudiation, digitalSignature, keyEncipherment'; \
  echo 'subjectAltName = @alt_names'; \
  echo '[ alt_names ]'; \
  echo "DNS.1 = www.${PARENT}"; \
  echo "DNS.2 = ${PARENT}"; \
  echo '[ v3_ca ]'; \
  echo 'subjectKeyIdentifier=hash'; \
  echo 'authorityKeyIdentifier=keyid:always,issuer'; \
  echo 'basicConstraints = critical, CA:TRUE, pathlen:0'; \
  echo 'keyUsage = critical, cRLSign, keyCertSign'; \
  echo 'extendedKeyUsage = serverAuth, clientAuth')

openssl x509 -noout -text -in $PARENT.crt
```

<span data-ttu-id="e2626-175">Чтобы получить PFX-файл, используйте следующую команду:</span><span class="sxs-lookup"><span data-stu-id="e2626-175">To get a .pfx, use the following command:</span></span>

```bash
openssl pkcs12 -export -out $PARENT.pfx -inkey $PARENT.key -in $PARENT.crt
```

> [!NOTE]
> <span data-ttu-id="e2626-176">В примере. aspnetcore 3.1 будет использоваться `.pfx` и пароль.</span><span class="sxs-lookup"><span data-stu-id="e2626-176">The .aspnetcore 3.1 example will use `.pfx` and a password.</span></span> <span data-ttu-id="e2626-177">Начиная со среды выполнения `.net 5` Kestrel также может принимать `.crt` и файлы `.key` с кодировкой PEM.</span><span class="sxs-lookup"><span data-stu-id="e2626-177">Starting with the `.net 5` runtime, Kestrel can also take `.crt` and PEM-encoded `.key` files.</span></span>

<span data-ttu-id="e2626-178">В зависимости от ОС узла сертификат должен быть доверенным.</span><span class="sxs-lookup"><span data-stu-id="e2626-178">Depending on the host os, the certificate will need to be trusted.</span></span> <span data-ttu-id="e2626-179">На узле Linux "доверие" сертификат отличается и зависит от дистрибутива.</span><span class="sxs-lookup"><span data-stu-id="e2626-179">On a Linux host, 'trusting' the certificate is different and distro dependent.</span></span>

<span data-ttu-id="e2626-180">Ниже приведен пример использования PowerShell в Windows.</span><span class="sxs-lookup"><span data-stu-id="e2626-180">For the purposes of this guide, here's an example in Windows using PowerShell:</span></span>

```powershell
Import-Certificate -FilePath $certFilePath -CertStoreLocation 'Cert:\LocalMachine\Root'
```

<span data-ttu-id="e2626-181">Для .NET Core 3.1 выполните следующую команду в WSL:</span><span class="sxs-lookup"><span data-stu-id="e2626-181">For .NET Core 3.1, run the following command in WSL:</span></span>

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/path/to/certs/:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

<span data-ttu-id="e2626-182">Начиная с .NET 5 Kestrel может принимать `.crt` и `.key` файлы с кодировкой PEM.</span><span class="sxs-lookup"><span data-stu-id="e2626-182">Starting with .NET 5, Kestrel can take the `.crt` and PEM-encoded `.key` files.</span></span> <span data-ttu-id="e2626-183">Пример можно запустить с помощью следующей команды для .NET 5:</span><span class="sxs-lookup"><span data-stu-id="e2626-183">You can run the sample with the following command for .NET 5:</span></span>

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=/https/contoso.com.key -v /c/path/to/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> <span data-ttu-id="e2626-184">Обратите внимание, что в WSL путь подключения тома может быть разным в зависимости от конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e2626-184">Note that in WSL, the volume mount path may change depending on the configuration.</span></span>

<span data-ttu-id="e2626-185">Для .NET Core 3.1 в Windows выполните следующую команду в `Powershell`:</span><span class="sxs-lookup"><span data-stu-id="e2626-185">For .NET Core 3.1 in Windows, run the following command in `Powershell`:</span></span>

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="e2626-186">Для .NET 5 в Windows выполните следующую команду в PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e2626-186">For .NET 5 in Windows, run the following command in PowerShell:</span></span>

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=c:\https\contoso.com.key -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="e2626-187">Когда приложение откроется, перейдите по адресу contoso.com:8001 в браузере.</span><span class="sxs-lookup"><span data-stu-id="e2626-187">Once the application is up, navigate to contoso.com:8001 in a browser.</span></span>

<span data-ttu-id="e2626-188">Убедитесь, что записи узла обновлены, чтобы `contoso.com` отвечал на соответствующий IP-адрес (например, 127.0.0.1).</span><span class="sxs-lookup"><span data-stu-id="e2626-188">Be sure that the host entries are updated for `contoso.com` to answer on  the appropriate ip address (for example 127.0.0.1).</span></span> <span data-ttu-id="e2626-189">Если сертификат не распознан, убедитесь, что сертификат, загружаемый вместе с контейнером, также является доверенным для узла, а также что для `contoso.com` имеются соответствующие записи SAN/DNS.</span><span class="sxs-lookup"><span data-stu-id="e2626-189">If the certificate isn't recognized, make sure that the certificate that is loaded with the container is also trusted on the host, and that there's appropriate SAN / DNS entries for `contoso.com`.</span></span>

#### <a name="clean-up"></a><span data-ttu-id="e2626-190">Очистка</span><span class="sxs-lookup"><span data-stu-id="e2626-190">Clean up</span></span>

<span data-ttu-id="e2626-191">Не забудьте очистить самозаверяющие сертификаты после завершения тестирования.</span><span class="sxs-lookup"><span data-stu-id="e2626-191">Be sure to clean up the self-signed certificates once done testing.</span></span>

```powershell
Get-ChildItem $certFilePath | Remove-Item
```
