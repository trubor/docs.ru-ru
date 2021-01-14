---
title: Установка .NET в Linux с использованием пакета Snap — .NET
description: В этом разделе описывается установка пакета SDK для .NET или среды выполнения .NET в Linux с использованием пакета Snap.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 741933b5ca6f01d73b388675fe7f8a43c4efb0f9
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970936"
---
# <a name="install-the-net-sdk-or-the-net-runtime-with-snap"></a><span data-ttu-id="580ae-103">Установка пакета SDK для .NET или среды выполнения .NET с использованием пакета Snap</span><span class="sxs-lookup"><span data-stu-id="580ae-103">Install the .NET SDK or the .NET Runtime with Snap</span></span>

<span data-ttu-id="580ae-104">Для установки пакета SDK для .NET или среды выполнения .NET можно использовать пакет Snap.</span><span class="sxs-lookup"><span data-stu-id="580ae-104">Use a Snap package to install the .NET SDK or .NET Runtime.</span></span> <span data-ttu-id="580ae-105">Пакеты Snap — это отличная альтернатива диспетчеру пакетов, встроенному в дистрибутив Linux.</span><span class="sxs-lookup"><span data-stu-id="580ae-105">Snaps are a great alternative to the package manager built into your Linux distribution.</span></span> <span data-ttu-id="580ae-106">В этой статье описано, как установить .NET с использованием пакета [Snap](https://snapcraft.io/dotnet-sdk).</span><span class="sxs-lookup"><span data-stu-id="580ae-106">This article describes how to install .NET through [Snap](https://snapcraft.io/dotnet-sdk).</span></span>

<span data-ttu-id="580ae-107">Snap-пакет — это пакет приложения и его зависимостей, которые работают без изменений во многих разных дистрибутивах Linux.</span><span class="sxs-lookup"><span data-stu-id="580ae-107">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="580ae-108">Snap-пакеты можно найти и установить с помощью Snap Store.</span><span class="sxs-lookup"><span data-stu-id="580ae-108">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="580ae-109">Дополнительные сведения о Snap см. в [этой статье](https://snapcraft.io/docs/getting-started).</span><span class="sxs-lookup"><span data-stu-id="580ae-109">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

> [!CAUTION]
> <span data-ttu-id="580ae-110">Пакеты Snap не поддерживаются в WSL2 в Windows 10.</span><span class="sxs-lookup"><span data-stu-id="580ae-110">Snap packages aren't supported in WSL2 on Windows 10.</span></span> <span data-ttu-id="580ae-111">В качестве альтернативы можно использовать [скрипт `dotnet-install`](linux-scripted-manual.md#scripted-install) или диспетчер пакетов для соответствующего дистрибутива WSL2.</span><span class="sxs-lookup"><span data-stu-id="580ae-111">As an alternative, use the [`dotnet-install` script](linux-scripted-manual.md#scripted-install) or the package manager for the particular WSL2 distribution.</span></span> <span data-ttu-id="580ae-112">Такой способ не рекомендуется, но вы можете попытаться включить пакет Snap с помощью [неподдерживаемого возможного решения, описываемого на форумах snapcraft](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033).</span><span class="sxs-lookup"><span data-stu-id="580ae-112">It's not recommended but you can try to enable snap with an [unsupported workaround from the snapcraft forums](https://forum.snapcraft.io/t/running-snaps-on-wsl2-insiders-only-for-now/13033).</span></span>

## <a name="net-releases"></a><span data-ttu-id="580ae-113">Выпуски .NET</span><span class="sxs-lookup"><span data-stu-id="580ae-113">.NET releases</span></span>

<span data-ttu-id="580ae-114">В пакете Snap доступны только поддерживаемые (✔️) версии пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="580ae-114">Only ✔️ supported versions of .NET SDK are available through Snap.</span></span> <span data-ttu-id="580ae-115">Все версии среды выполнения .NET доступны в пакете Snap, начиная с версии 2.1.</span><span class="sxs-lookup"><span data-stu-id="580ae-115">All versions of the .NET Runtime are available through snap starting with version 2.1.</span></span> <span data-ttu-id="580ae-116">В следующей таблице перечислены выпуски .NET (и .NET Core):</span><span class="sxs-lookup"><span data-stu-id="580ae-116">The following table lists the .NET (and .NET Core) releases:</span></span>

| <span data-ttu-id="580ae-117">✔️ Поддерживается</span><span class="sxs-lookup"><span data-stu-id="580ae-117">✔️ Supported</span></span> | <span data-ttu-id="580ae-118">❌ Не поддерживается</span><span class="sxs-lookup"><span data-stu-id="580ae-118">❌ Unsupported</span></span> |
|-------------|---------------|
| <span data-ttu-id="580ae-119">5,0</span><span class="sxs-lookup"><span data-stu-id="580ae-119">5.0</span></span>         | <span data-ttu-id="580ae-120">3.0</span><span class="sxs-lookup"><span data-stu-id="580ae-120">3.0</span></span>           |
| <span data-ttu-id="580ae-121">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="580ae-121">3.1 (LTS)</span></span>   | <span data-ttu-id="580ae-122">2.2</span><span class="sxs-lookup"><span data-stu-id="580ae-122">2.2</span></span>           |
| <span data-ttu-id="580ae-123">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="580ae-123">2.1 (LTS)</span></span>   | <span data-ttu-id="580ae-124">2,0</span><span class="sxs-lookup"><span data-stu-id="580ae-124">2.0</span></span>           |
|             | <span data-ttu-id="580ae-125">1,1</span><span class="sxs-lookup"><span data-stu-id="580ae-125">1.1</span></span>           |
|             | <span data-ttu-id="580ae-126">1.0</span><span class="sxs-lookup"><span data-stu-id="580ae-126">1.0</span></span>           |

<span data-ttu-id="580ae-127">Дополнительные сведения о жизненном цикле выпусков .NET см. в разделе [Политика поддержки .NET Core и .NET 5](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="580ae-127">For more information about the life cycle of .NET releases, see [.NET Core and .NET 5 Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="sdk-or-runtime"></a><span data-ttu-id="580ae-128">Пакет SDK или среда выполнения</span><span class="sxs-lookup"><span data-stu-id="580ae-128">SDK or Runtime</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install-the-sdk"></a><span data-ttu-id="580ae-129">Установка пакета SDK</span><span class="sxs-lookup"><span data-stu-id="580ae-129">Install the SDK</span></span>

<span data-ttu-id="580ae-130">Пакеты Snap для пакета SDK для .NET публикуются с одним и тем же идентификатором: `dotnet-sdk`.</span><span class="sxs-lookup"><span data-stu-id="580ae-130">Snap packages for the .NET SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="580ae-131">Конкретную версию пакета SDK можно установить, указав канал.</span><span class="sxs-lookup"><span data-stu-id="580ae-131">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="580ae-132">Пакет SDK содержит соответствующую среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="580ae-132">The SDK includes the corresponding runtime.</span></span> <span data-ttu-id="580ae-133">В следующей таблице перечислены каналы.</span><span class="sxs-lookup"><span data-stu-id="580ae-133">The following table lists the channels:</span></span>

| <span data-ttu-id="580ae-134">Версия .NET</span><span class="sxs-lookup"><span data-stu-id="580ae-134">.NET version</span></span> | <span data-ttu-id="580ae-135">Пакет Snap или канал</span><span class="sxs-lookup"><span data-stu-id="580ae-135">Snap package or channel</span></span>  |
|--------------|--------------------------|
| <span data-ttu-id="580ae-136">5,0</span><span class="sxs-lookup"><span data-stu-id="580ae-136">5.0</span></span>          | <span data-ttu-id="580ae-137">`5.0` или `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="580ae-137">`5.0` or `latest/stable`</span></span> |
| <span data-ttu-id="580ae-138">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="580ae-138">3.1 (LTS)</span></span>    | <span data-ttu-id="580ae-139">`3.1` или `lts/stable`</span><span class="sxs-lookup"><span data-stu-id="580ae-139">`3.1` or `lts/stable`</span></span>    |
| <span data-ttu-id="580ae-140">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="580ae-140">2.1 (LTS)</span></span>    | `2.1`                    |

<span data-ttu-id="580ae-141">Выполните команду `snap install`, чтобы установить Snap-пакет пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="580ae-141">Use the `snap install` command to install a .NET SDK snap package.</span></span> <span data-ttu-id="580ae-142">Используйте параметр `--channel`, чтобы указать, какую версию следует установить.</span><span class="sxs-lookup"><span data-stu-id="580ae-142">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="580ae-143">Если этот параметр отсутствует, используйте `latest/stable`.</span><span class="sxs-lookup"><span data-stu-id="580ae-143">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="580ae-144">В этом примере указан `5.0`:</span><span class="sxs-lookup"><span data-stu-id="580ae-144">In this example, `5.0` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=5.0
```

<span data-ttu-id="580ae-145">Затем зарегистрируйте команду `dotnet` для системы, выполнив команду `snap alias`:</span><span class="sxs-lookup"><span data-stu-id="580ae-145">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="580ae-146">Эта команда имеет следующий формат: `sudo snap alias {package}.{command} {alias}`.</span><span class="sxs-lookup"><span data-stu-id="580ae-146">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="580ae-147">Вы можете выбрать любое имя `{alias}`.</span><span class="sxs-lookup"><span data-stu-id="580ae-147">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="580ae-148">Например, вы можете присвоить команде имя после установки конкретной версии с помощью Snap-пакета: `sudo snap alias dotnet-sdk.dotnet dotnet50`.</span><span class="sxs-lookup"><span data-stu-id="580ae-148">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet50`.</span></span> <span data-ttu-id="580ae-149">При использовании команды `dotnet50` вы вызываете эту конкретную версию .NET.</span><span class="sxs-lookup"><span data-stu-id="580ae-149">When you use the command `dotnet50`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="580ae-150">Выбор другого псевдонима несовместим с инструкциями из большинства учебников и примеров, так как в них требуется использовать команду `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="580ae-150">But choosing a different alias is incompatible with most tutorials and examples as they expect a `dotnet` command to be used.</span></span>

## <a name="install-the-runtime"></a><span data-ttu-id="580ae-151">Установка среды выполнения</span><span class="sxs-lookup"><span data-stu-id="580ae-151">Install the runtime</span></span>

<span data-ttu-id="580ae-152">Пакеты Snap для среды выполнения .NET публикуются с собственными идентификаторами пакета.</span><span class="sxs-lookup"><span data-stu-id="580ae-152">Snap packages for the .NET Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="580ae-153">В следующей таблице перечислены идентификаторы пакетов:</span><span class="sxs-lookup"><span data-stu-id="580ae-153">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="580ae-154">Версия .NET</span><span class="sxs-lookup"><span data-stu-id="580ae-154">.NET version</span></span>      | <span data-ttu-id="580ae-155">Snap-пакет</span><span class="sxs-lookup"><span data-stu-id="580ae-155">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="580ae-156">5,0</span><span class="sxs-lookup"><span data-stu-id="580ae-156">5.0</span></span>               | `dotnet-runtime-50` |
| <span data-ttu-id="580ae-157">3.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="580ae-157">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="580ae-158">3.0</span><span class="sxs-lookup"><span data-stu-id="580ae-158">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="580ae-159">2.2</span><span class="sxs-lookup"><span data-stu-id="580ae-159">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="580ae-160">2.1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="580ae-160">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="580ae-161">Выполните команду `snap install`, чтобы установить Snap-пакет среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="580ae-161">Use the `snap install` command to install a .NET Runtime snap package.</span></span> <span data-ttu-id="580ae-162">В этом примере устанавливается .NET 5.0:</span><span class="sxs-lookup"><span data-stu-id="580ae-162">In this example, .NET 5.0 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-50 --classic
```

<span data-ttu-id="580ae-163">Затем зарегистрируйте команду `dotnet` для системы, выполнив команду `snap alias`:</span><span class="sxs-lookup"><span data-stu-id="580ae-163">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-50.dotnet dotnet
```

<span data-ttu-id="580ae-164">Эта команда имеет следующий формат: `sudo snap alias {package}.{command} {alias}`.</span><span class="sxs-lookup"><span data-stu-id="580ae-164">The command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="580ae-165">Вы можете выбрать любое имя `{alias}`.</span><span class="sxs-lookup"><span data-stu-id="580ae-165">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="580ae-166">Например, вы можете присвоить команде имя после установки конкретной версии с помощью Snap-пакета: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`.</span><span class="sxs-lookup"><span data-stu-id="580ae-166">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-50.dotnet dotnet50`.</span></span> <span data-ttu-id="580ae-167">При использовании команды `dotnet50` вы вызываете эту конкретную версию .NET.</span><span class="sxs-lookup"><span data-stu-id="580ae-167">When you use the command `dotnet50`, you'll invoke a specific version of .NET.</span></span> <span data-ttu-id="580ae-168">Выбор другого псевдонима несовместим с инструкциями из большинства учебников и примеров, так как в них требуется команда `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="580ae-168">But choosing a different alias is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

## <a name="tlsssl-certificate-errors"></a><span data-ttu-id="580ae-169">Ошибки сертификатов TLS/SSL</span><span class="sxs-lookup"><span data-stu-id="580ae-169">TLS/SSL Certificate errors</span></span>

<span data-ttu-id="580ae-170">При установке .NET с помощью пакета Snap возможно, что на некоторых дистрибутивах нельзя найти сертификаты TLS/SSL .NET, а во время выполнения `restore` может отобразиться сообщение об ошибке:</span><span class="sxs-lookup"><span data-stu-id="580ae-170">When .NET is installed through Snap, it's possible that on some distros the .NET TLS/SSL certificates may not be found and you may receive an error during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="580ae-171">Чтобы устранить эту проблему, задайте несколько переменных среды:</span><span class="sxs-lookup"><span data-stu-id="580ae-171">To resolve this problem, set a few environment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="580ae-172">Расположение сертификата зависит от дистрибутива.</span><span class="sxs-lookup"><span data-stu-id="580ae-172">The certificate location will vary by distro.</span></span> <span data-ttu-id="580ae-173">Ниже приведены расположения для дистрибутивов, в которых возникла проблема.</span><span class="sxs-lookup"><span data-stu-id="580ae-173">Here are the locations for the distros where the issue has been experienced.</span></span>

| <span data-ttu-id="580ae-174">Distribution</span><span class="sxs-lookup"><span data-stu-id="580ae-174">Distribution</span></span> | <span data-ttu-id="580ae-175">Расположение</span><span class="sxs-lookup"><span data-stu-id="580ae-175">Location</span></span>                                            |
|--------------|-----------------------------------------------------|
| <span data-ttu-id="580ae-176">**Fedora**</span><span class="sxs-lookup"><span data-stu-id="580ae-176">**Fedora**</span></span>   | `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem` |
| <span data-ttu-id="580ae-177">**OpenSUSE**</span><span class="sxs-lookup"><span data-stu-id="580ae-177">**OpenSUSE**</span></span> | `/etc/ssl/ca-bundle.pem`                            |
| <span data-ttu-id="580ae-178">**Solus**</span><span class="sxs-lookup"><span data-stu-id="580ae-178">**Solus**</span></span>    | `/etc/ssl/certs/ca-certificates.crt`                |

## <a name="next-steps"></a><span data-ttu-id="580ae-179">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="580ae-179">Next steps</span></span>

- [<span data-ttu-id="580ae-180">Включение заполнения клавишей TAB для .NET CLI</span><span class="sxs-lookup"><span data-stu-id="580ae-180">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="580ae-181">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="580ae-181">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
