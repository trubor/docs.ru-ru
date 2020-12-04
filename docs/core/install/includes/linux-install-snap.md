---
ms.openlocfilehash: 83808f2f3a05333ed5d9e3809cbc2fd6e230d02c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031785"
---

[<span data-ttu-id="7ca16-101">Платформа .NET Core доступна в Snap Store.</span><span class="sxs-lookup"><span data-stu-id="7ca16-101">.NET Core is available from the Snap Store.</span></span>](https://snapcraft.io/dotnet-sdk)

<span data-ttu-id="7ca16-102">Snap-пакет — это пакет приложения и его зависимостей, которые работают без изменений во многих разных дистрибутивах Linux.</span><span class="sxs-lookup"><span data-stu-id="7ca16-102">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="7ca16-103">Snap-пакеты можно найти и установить с помощью Snap Store.</span><span class="sxs-lookup"><span data-stu-id="7ca16-103">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="7ca16-104">Дополнительные сведения о Snap см. в [этой статье](https://snapcraft.io/docs/getting-started).</span><span class="sxs-lookup"><span data-stu-id="7ca16-104">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

<span data-ttu-id="7ca16-105">В Snap-пакете доступны только поддерживаемые версии .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7ca16-105">Only supported versions of .NET Core are available through Snap.</span></span>

### <a name="install-the-sdk"></a><span data-ttu-id="7ca16-106">Установка пакета SDK</span><span class="sxs-lookup"><span data-stu-id="7ca16-106">Install the SDK</span></span>

<span data-ttu-id="7ca16-107">Snap-пакеты пакета SDK для .NET публикуются с одним и тем же идентификатором: `dotnet-sdk`.</span><span class="sxs-lookup"><span data-stu-id="7ca16-107">Snap packages for .NET SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="7ca16-108">Конкретную версию пакета SDK можно установить, указав канал.</span><span class="sxs-lookup"><span data-stu-id="7ca16-108">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="7ca16-109">Пакет SDK содержит соответствующую среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="7ca16-109">The SDK includes the corresponding runtime.</span></span> <span data-ttu-id="7ca16-110">В следующей таблице перечислены каналы.</span><span class="sxs-lookup"><span data-stu-id="7ca16-110">The following table lists the channels:</span></span>

| <span data-ttu-id="7ca16-111">Версия .NET</span><span class="sxs-lookup"><span data-stu-id="7ca16-111">.NET version</span></span> | <span data-ttu-id="7ca16-112">Snap-пакет</span><span class="sxs-lookup"><span data-stu-id="7ca16-112">Snap package</span></span>             |
|--------------|--------------------------|
| <span data-ttu-id="7ca16-113">5,0</span><span class="sxs-lookup"><span data-stu-id="7ca16-113">5.0</span></span>          | <span data-ttu-id="7ca16-114">`5.0` или `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="7ca16-114">`5.0` or `latest/stable`</span></span> |
| <span data-ttu-id="7ca16-115">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="7ca16-115">3.1 (LTS)</span></span>    | <span data-ttu-id="7ca16-116">`3.1` или `lts/stable`</span><span class="sxs-lookup"><span data-stu-id="7ca16-116">`3.1` or `lts/stable`</span></span>    |
| <span data-ttu-id="7ca16-117">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="7ca16-117">2.1 (LTS)</span></span>    | `2.1`                    |

<span data-ttu-id="7ca16-118">Выполните команду `snap install`, чтобы установить Snap-пакет пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="7ca16-118">Use the `snap install` command to install a .NET SDK snap package.</span></span> <span data-ttu-id="7ca16-119">Используйте параметр `--channel`, чтобы указать, какую версию следует установить.</span><span class="sxs-lookup"><span data-stu-id="7ca16-119">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="7ca16-120">Если этот параметр отсутствует, используйте `latest/stable`.</span><span class="sxs-lookup"><span data-stu-id="7ca16-120">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="7ca16-121">В этом примере указан `5.0`:</span><span class="sxs-lookup"><span data-stu-id="7ca16-121">In this example, `5.0` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

<span data-ttu-id="7ca16-122">Затем зарегистрируйте команду `dotnet` для системы, выполнив команду `snap alias`:</span><span class="sxs-lookup"><span data-stu-id="7ca16-122">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="7ca16-123">Эта команда имеет следующий формат: `sudo snap alias {package}.{command} {alias}`.</span><span class="sxs-lookup"><span data-stu-id="7ca16-123">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="7ca16-124">Вы можете выбрать любое имя `{alias}`.</span><span class="sxs-lookup"><span data-stu-id="7ca16-124">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="7ca16-125">Например, вы можете присвоить команде имя после установки конкретной версии с помощью Snap-пакета: `sudo snap alias dotnet-sdk.dotnet dotnet50`.</span><span class="sxs-lookup"><span data-stu-id="7ca16-125">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet50`.</span></span> <span data-ttu-id="7ca16-126">При использовании команды `dotnet50` вы вызываете эту конкретную версию .NET.</span><span class="sxs-lookup"><span data-stu-id="7ca16-126">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="7ca16-127">Но это несовместимо с инструкциями из большинства учебников и примеров, так как для них необходимо, чтобы команда `dotnet` была доступна.</span><span class="sxs-lookup"><span data-stu-id="7ca16-127">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="7ca16-128">Установка среды выполнения</span><span class="sxs-lookup"><span data-stu-id="7ca16-128">Install the runtime</span></span>

<span data-ttu-id="7ca16-129">Snap-пакеты для среды выполнения .NET Core публикуются с собственными идентификаторами пакета.</span><span class="sxs-lookup"><span data-stu-id="7ca16-129">Snap packages for .NET Core Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="7ca16-130">В следующей таблице перечислены идентификаторы пакетов:</span><span class="sxs-lookup"><span data-stu-id="7ca16-130">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="7ca16-131">Версия .NET</span><span class="sxs-lookup"><span data-stu-id="7ca16-131">.NET version</span></span>      | <span data-ttu-id="7ca16-132">Snap-пакет</span><span class="sxs-lookup"><span data-stu-id="7ca16-132">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="7ca16-133">5,0</span><span class="sxs-lookup"><span data-stu-id="7ca16-133">5.0</span></span>               | `dotnet-runtime-50` |
| <span data-ttu-id="7ca16-134">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="7ca16-134">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="7ca16-135">3.0</span><span class="sxs-lookup"><span data-stu-id="7ca16-135">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="7ca16-136">2.2</span><span class="sxs-lookup"><span data-stu-id="7ca16-136">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="7ca16-137">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="7ca16-137">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="7ca16-138">Выполните команду `snap install`, чтобы установить Snap-пакет среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="7ca16-138">Use the `snap install` command to install a .NET Runtime snap package.</span></span> <span data-ttu-id="7ca16-139">В этом примере устанавливается .NET 5.0:</span><span class="sxs-lookup"><span data-stu-id="7ca16-139">In this example, .NET 5.0 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-50 --classic
```

<span data-ttu-id="7ca16-140">Затем зарегистрируйте команду `dotnet` для системы, выполнив команду `snap alias`:</span><span class="sxs-lookup"><span data-stu-id="7ca16-140">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

<span data-ttu-id="7ca16-141">Эта команда имеет следующий формат: `sudo snap alias {package}.{command} {alias}`.</span><span class="sxs-lookup"><span data-stu-id="7ca16-141">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="7ca16-142">Вы можете выбрать любое имя `{alias}`.</span><span class="sxs-lookup"><span data-stu-id="7ca16-142">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="7ca16-143">Например, вы можете присвоить команде имя после установки конкретной версии с помощью Snap-пакета: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`.</span><span class="sxs-lookup"><span data-stu-id="7ca16-143">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`.</span></span> <span data-ttu-id="7ca16-144">При использовании команды `dotnet50` вы вызываете эту конкретную версию .NET.</span><span class="sxs-lookup"><span data-stu-id="7ca16-144">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="7ca16-145">Но это несовместимо с инструкциями из большинства учебников и примеров, так как для них необходимо, чтобы команда `dotnet` была доступна.</span><span class="sxs-lookup"><span data-stu-id="7ca16-145">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="ssl-certificate-errors"></a><span data-ttu-id="7ca16-146">Ошибки SSL-сертификатов</span><span class="sxs-lookup"><span data-stu-id="7ca16-146">SSL Certificate errors</span></span>

<span data-ttu-id="7ca16-147">При установке .NET с помощью Snap-пакета возможно, что на некоторых дистрибутивах нельзя найти SSL-сертификаты .NET, а во время выполнения `restore` может отобразиться сообщение об ошибке:</span><span class="sxs-lookup"><span data-stu-id="7ca16-147">When .NET is installed through Snap, it's possible that on some distros the .NET SSL certificates may not be found and you may receive an error similar to the following during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="7ca16-148">Чтобы устранить эту проблему, задайте несколько переменных среды:</span><span class="sxs-lookup"><span data-stu-id="7ca16-148">To resolve this issue, set a few environment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="7ca16-149">Расположение сертификата зависит от дистрибутива.</span><span class="sxs-lookup"><span data-stu-id="7ca16-149">The certificate location will vary by distro.</span></span> <span data-ttu-id="7ca16-150">Ниже приведены расположения для дистрибутивов, в которых возникла проблема.</span><span class="sxs-lookup"><span data-stu-id="7ca16-150">Here are the locations for the distros where we have experienced the issue.</span></span>

* <span data-ttu-id="7ca16-151">Fedora — `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="7ca16-151">Fedora - `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span></span>
* <span data-ttu-id="7ca16-152">OpenSUSE — `/etc/ssl/ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="7ca16-152">OpenSUSE - `/etc/ssl/ca-bundle.pem`</span></span>
* <span data-ttu-id="7ca16-153">Solus — `/etc/ssl/certs/ca-certificates.crt`</span><span class="sxs-lookup"><span data-stu-id="7ca16-153">Solus - `/etc/ssl/certs/ca-certificates.crt`</span></span>
