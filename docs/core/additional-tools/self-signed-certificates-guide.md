---
title: Общие сведения о создании самозаверяющих сертификатов
description: Обзор средства Microsoft dotnet dev-certs, добавляющего функции для проектов .NET Core и ASP.NET Core, а также другие параметры для использования самозаверяющих сертификатов.
author: angee
ms.date: 11/19/2020
ms.openlocfilehash: 738af3fc091e415399a53015a40748ad6116a2b4
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873020"
---
# <a name="generate-self-signed-certificates-with-the-net-cli"></a>Создание самозаверяющих сертификатов с помощью интерфейса командной строки .NET

При использовании самозаверяющих сертификатов существуют различные способы их создания и использования в сценариях разработки и тестирования.  В этом руководстве вы узнаете, как использовать самозаверяющие сертификаты с `dotnet dev-certs`, а также о других параметрах, таких как `PowerShell` и `OpenSSL`.

Затем можно проверить, что сертификат будет загружен, с помощью примера, такого как [приложение ASP.NET Core](https://github.com/dotnet/dotnet-docker/blob/main/samples/run-aspnetcore-https-development.md), размещенное в контейнере.

## <a name="prerequisites"></a>Предварительные требования

В этом примере можно использовать .NET Core 3.1 или .NET 5.

Для `dotnet dev-certs` следует убедиться в том, что установлена соответствующая версия .NET:

* [Установка .NET в Windows](../install/windows.md)
* [Установка .NET в Linux](../install/linux.md)
* [Установка .NET в macOS](../install/macos.md)

Для работы с этим примером требуется [Docker 17.06](https://docs.docker.com/release-notes/docker-ce) или [клиент Docker](https://www.docker.com/products/docker) более поздней версии.

## <a name="prepare-sample-app"></a>Подготовка примера приложения

Необходимо подготовить пример приложения в зависимости от среды выполнения, которую вы хотите использовать для тестирования, либо [.NET Core 3.1](#net-core-31-sample-app), либо [.NET 5](#net-5-sample-app).

В рамках этого руководства вы будете использовать [пример приложения](https://hub.docker.com/_/microsoft-dotnet-samples) и внесете необходимые изменения.

### <a name="net-core-31-sample-app"></a>Пример приложения .NET Core 3.1

Получение примера приложения.

```console
git clone https://github.com/dotnet/dotnet-docker/
```

Перейдите в репозиторий локально и откройте рабочую область в редакторе.

> [!NOTE]
> Если вы хотите использовать параметры dotnet publish для *обрезки* развертывания, следует убедиться, что соответствующие зависимости включены для поддержки SSL-сертификатов.
Обновите файл [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/aspnetapp/aspnetapp.csproj), чтобы убедиться в том, что в контейнер включены соответствующие сборки. Дополнительные сведения см. в статье, посвященной обновлению файла CSPROJ для [поддержки SSL-сертификатов](../deploying/trim-self-contained.md#support-for-ssl-certificates) при использовании усечения для автономных развертываний.

Убедитесь, что `aspnetapp.csproj` включает соответствующую целевую платформу:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>.netcoreapp3.1</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

Измените Dockerfile, чтобы среда выполнения указывала на .NET Core 3.1:

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

Убедитесь, что вы указали на пример приложения.

```console
cd .\dotnet-docker\samples\aspnetapp
```

Создайте контейнер для локального тестирования.

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

### <a name="net-5-sample-app"></a>Пример приложения .NET 5

В рамках этого руководства [пример aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) следует проверить на предмет использования .NET 5.

Проверьте пример приложения [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/Dockerfile) на предмет использования .NET 5.

В зависимости от ОС узла может потребоваться обновить среду выполнения ASP.NET. Например, изменение с `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` на `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` в Dockerfile поможет выбрать соответствующую среду выполнения Windows.

Например, это поможет при тестировании сертификатов в Windows:

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

Если вы тестируете сертификаты в Linux, можно использовать существующий Dockerfile.

Убедитесь, что `aspnetapp.csproj` включает соответствующую целевую платформу:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

> [!NOTE]
> Если вы хотите использовать параметры `dotnet publish` для *обрезки* развертывания, убедитесь, что соответствующие зависимости включены для поддержки SSL-сертификатов.
Обновите файл [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/main/samples/aspnetapp/aspnetapp/aspnetapp.csproj), чтобы убедиться в том, что в контейнер включены соответствующие сборки. Дополнительные сведения см. в статье, посвященной обновлению файла CSPROJ для [поддержки SSL-сертификатов](../deploying/trim-self-contained.md#support-for-ssl-certificates) при использовании усечения для автономных развертываний.

Убедитесь, что вы указали на пример приложения.

```console
cd .\dotnet-docker\samples\aspnetapp
```

Создайте контейнер для локального тестирования.

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

## <a name="create-a-self-signed-certificate"></a>Создание самозаверяющего сертификата.

Самозаверяющий сертификат можно создать:

- [С помощью dotnet dev-certs](#with-dotnet-dev-certs)
- [С помощью PowerShell](#with-powershell)
- [С помощью OpenSSL](#with-openssl)

### <a name="with-dotnet-dev-certs"></a>С помощью dotnet dev-certs

Для работы с самозаверяющими сертификатами можно использовать `dotnet dev-certs`. В этом примере используется консоль PowerShell.

```console
dotnet dev-certs https -ep $env:USERPROFILE\.aspnet\https\aspnetapp.pfx -p crypticpassword
dotnet dev-certs https --trust
```

> [!NOTE]
> Имя сертификата, в данном случае *aspnetapp*.pfx, должно совпадать с именем сборки проекта. `crypticpassword` используется в качестве замены пароля на ваш выбор. Если консоль возвращает сообщение "Допустимый HTTPS-сертификат уже существует", то в вашем хранилище уже есть доверенный сертификат. Его можно экспортировать с помощью консоли MMC.

Настройте секреты приложения для сертификата:

```console
dotnet user-secrets -p aspnetapp\aspnetapp.csproj set "Kestrel:Certificates:Development:Password" "crypticpassword"
```

> [!NOTE]
> Примечание. Пароль должен совпадать с паролем, используемым для сертификата.

Запустите образ контейнера с ASP.NET Core, настроенным для HTTPS:

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -v $env:APPDATA\microsoft\UserSecrets\:C:\Users\ContainerUser\AppData\Roaming\microsoft\UserSecrets -v $env:USERPROFILE\.aspnet\https:C:\Users\ContainerUser\AppData\Roaming\ASP.NET\Https mcr.microsoft.com/dotnet/samples:aspnetapp
```

После запуска приложения перейдите по адресу `https://localhost:8001` в веб-браузере.

#### <a name="clean-up"></a>Очистка

Если секреты и сертификаты не используются, обязательно очистите их.

```console
dotnet user-secrets remove "Kestrel:Certificates:Development:Password" -p aspnetapp\aspnetapp.csproj
dotnet dev-certs https --clean
```

### <a name="with-powershell"></a>С помощью PowerShell

Для создания самозаверяющих сертификатов можно использовать PowerShell. [Клиент PKI](/powershell/module/pkiclient/new-selfsignedcertificate?preserve-view=true&view=win10-ps) можно использовать для создания самозаверяющего сертификата.

```powershell
$cert = New-SelfSignedCertificate -DnsName @("contoso.com", "www.contoso.com") -CertStoreLocation "cert:\LocalMachine\My"
```

Сертификат будет создан, однако в целях тестирования следует поместить его в хранилище сертификатов для тестирования в браузере.

```powershell
$certKeyPath = "c:\certs\contoso.com.pfx"
$password = ConvertTo-SecureString 'password' -AsPlainText -Force
$cert | Export-PfxCertificate -FilePath $certKeyPath -Password $password
$rootCert = $(Import-PfxCertificate -FilePath $certKeyPath -CertStoreLocation 'Cert:\LocalMachine\Root' -Password $password)
```

На этом этапе сертификаты должны быть доступны для просмотра с помощью [оснастки консоли управления](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).

Вы можете запустить образец контейнера в подсистеме Windows для Linux (WSL):

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> Обратите внимание, что при подключении тома путь к файлу может обрабатываться по-разному на основе узла.  Например, в WSL мы можем заменить */c/certs* на */mnt/c/certs*.

Если вы используете контейнер, созданный ранее для Windows, команда run должна выглядеть следующим образом:

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

Когда приложение откроется, перейдите по адресу contoso.com:8001 в браузере.

Убедитесь, что записи узла обновлены, чтобы `contoso.com` отвечал на соответствующий IP-адрес (например, 127.0.0.1). Если сертификат не распознан, убедитесь, что сертификат, загружаемый вместе с контейнером, также является доверенным для узла, а также что для `contoso.com` имеются соответствующие записи SAN/DNS.

#### <a name="clean-up"></a>Очистка

```powershell
$cert | Remove-Item
Get-ChildItem $certFilePath | Remove-Item
$rootCert | Remove-item
```

### <a name="with-openssl"></a>С помощью OpenSSL

Для создания самозаверяющих сертификатов можно использовать [OpenSSL](https://www.openssl.org/). В этом примере будет использоваться WSL/Ubuntu и оболочка bash с `OpenSSL`.

При этом будут созданы файлы CRT и KEY.

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

Чтобы получить PFX-файл, используйте следующую команду:

```bash
openssl pkcs12 -export -out $PARENT.pfx -inkey $PARENT.key -in $PARENT.crt
```

> [!NOTE]
> В примере. aspnetcore 3.1 будет использоваться `.pfx` и пароль. Начиная со среды выполнения `.net 5` Kestrel также может принимать `.crt` и файлы `.key` с кодировкой PEM.

В зависимости от ОС узла сертификат должен быть доверенным. На узле Linux "доверие" сертификат отличается и зависит от дистрибутива.

Ниже приведен пример использования PowerShell в Windows.

```powershell
Import-Certificate -FilePath $certFilePath -CertStoreLocation 'Cert:\LocalMachine\Root'
```

Для .NET Core 3.1 выполните следующую команду в WSL:

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/path/to/certs/:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

Начиная с .NET 5 Kestrel может принимать `.crt` и `.key` файлы с кодировкой PEM. Пример можно запустить с помощью следующей команды для .NET 5:

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=/https/contoso.com.key -v /c/path/to/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> Обратите внимание, что в WSL путь подключения тома может быть разным в зависимости от конфигурации.

Для .NET Core 3.1 в Windows выполните следующую команду в `Powershell`:

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

Для .NET 5 в Windows выполните следующую команду в PowerShell:

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=c:\https\contoso.com.key -v c:\certs:C:\https aspnetapp:my-sample
```

Когда приложение откроется, перейдите по адресу contoso.com:8001 в браузере.

Убедитесь, что записи узла обновлены, чтобы `contoso.com` отвечал на соответствующий IP-адрес (например, 127.0.0.1). Если сертификат не распознан, убедитесь, что сертификат, загружаемый вместе с контейнером, также является доверенным для узла, а также что для `contoso.com` имеются соответствующие записи SAN/DNS.

#### <a name="clean-up"></a>Очистка

Не забудьте очистить самозаверяющие сертификаты после завершения тестирования.

```powershell
Get-ChildItem $certFilePath | Remove-Item
```
