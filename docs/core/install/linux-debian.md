---
title: Установка .NET в Debian — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в Debian.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 683d0a9c47edf3cf9c47426d659e778eeb6f84df
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031895"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-debian"></a><span data-ttu-id="c319e-103">Установка пакета SDK для .NET или среды выполнения .NET в Debian</span><span class="sxs-lookup"><span data-stu-id="c319e-103">Install the .NET SDK or the .NET Runtime on Debian</span></span>

<span data-ttu-id="c319e-104">В этой статье описано, как установить .NET в Debian.</span><span class="sxs-lookup"><span data-stu-id="c319e-104">This article describes how to install .NET on Debian.</span></span> <span data-ttu-id="c319e-105">Если поддержка какой-либо версии Debian прекращается, то .NET также перестает поддерживать ее.</span><span class="sxs-lookup"><span data-stu-id="c319e-105">When a Debian version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="c319e-106">Но с помощью этих инструкций вы сможете запустить .NET даже в неподдерживаемых версиях.</span><span class="sxs-lookup"><span data-stu-id="c319e-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="c319e-107">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="c319e-107">Supported distributions</span></span>

<span data-ttu-id="c319e-108">В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET и версий Debian, в которых они поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="c319e-108">The following table is a list of currently supported .NET releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="c319e-109">Эти версии поддерживаются до того же времени, что и версия [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или [Debian](https://wiki.debian.org/DebianReleases).</span><span class="sxs-lookup"><span data-stu-id="c319e-109">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="c319e-110">Значок ✔️ означает, что версия Debian или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c319e-110">A ✔️ indicates that the version of Debian or .NET is still supported.</span></span>
- <span data-ttu-id="c319e-111">Значок ❌ означает, что версия Debian или версия .NET в таком выпуске Debian не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c319e-111">A ❌ indicates that the version of Debian or .NET isn't supported on that Debian release.</span></span>
- <span data-ttu-id="c319e-112">Если значок ✔️ стоит как напротив версии Debian, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c319e-112">When both a version of Debian and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="c319e-113">Debian</span><span class="sxs-lookup"><span data-stu-id="c319e-113">Debian</span></span>                   | <span data-ttu-id="c319e-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c319e-114">.NET Core 2.1</span></span> | <span data-ttu-id="c319e-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c319e-115">.NET Core 3.1</span></span> | <span data-ttu-id="c319e-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="c319e-116">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="c319e-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="c319e-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="c319e-118">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="c319e-118">✔️ 2.1</span></span>        | <span data-ttu-id="c319e-119">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="c319e-119">✔️ 3.1</span></span>        | <span data-ttu-id="c319e-120">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="c319e-120">✔️ 5.0</span></span> |
| <span data-ttu-id="c319e-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="c319e-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="c319e-122">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="c319e-122">✔️ 2.1</span></span>        | <span data-ttu-id="c319e-123">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="c319e-123">✔️ 3.1</span></span>        | <span data-ttu-id="c319e-124">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="c319e-124">✔️ 5.0</span></span> |
| <span data-ttu-id="c319e-125">❌ [8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="c319e-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="c319e-126">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="c319e-126">✔️ 2.1</span></span>        | <span data-ttu-id="c319e-127">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="c319e-127">❌ 3.1</span></span>        | <span data-ttu-id="c319e-128">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="c319e-128">❌ 5.0</span></span> |

<span data-ttu-id="c319e-129">Следующие версии .NET больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="c319e-129">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="c319e-130">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="c319e-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="c319e-131">3.0</span><span class="sxs-lookup"><span data-stu-id="c319e-131">3.0</span></span>
- <span data-ttu-id="c319e-132">2.2</span><span class="sxs-lookup"><span data-stu-id="c319e-132">2.2</span></span>
- <span data-ttu-id="c319e-133">2.0</span><span class="sxs-lookup"><span data-stu-id="c319e-133">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="c319e-134">Удалите предварительные версии</span><span class="sxs-lookup"><span data-stu-id="c319e-134">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="c319e-135">Установка других версий</span><span class="sxs-lookup"><span data-stu-id="c319e-135">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="c319e-136">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="c319e-136">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="c319e-137">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="c319e-137">Debian 9 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-8-"></a><span data-ttu-id="c319e-138">Debian 8 ❌</span><span class="sxs-lookup"><span data-stu-id="c319e-138">Debian 8 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-debian.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/8/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="c319e-139">Обновление пакета SDK или среды выполнения с помощью APT</span><span class="sxs-lookup"><span data-stu-id="c319e-139">APT update SDK or runtime</span></span>

<span data-ttu-id="c319e-140">Если для .NET доступен новый выпуск исправлений, можете выполнить обновление с помощью APT и следующих команд:</span><span class="sxs-lookup"><span data-stu-id="c319e-140">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="c319e-141">Устранение неполадок с APT</span><span class="sxs-lookup"><span data-stu-id="c319e-141">APT troubleshooting</span></span>

<span data-ttu-id="c319e-142">В этом разделе описаны распространенные ошибки, которые могут возникнуть при использовании APT для установки .NET.</span><span class="sxs-lookup"><span data-stu-id="c319e-142">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="c319e-143">Не удалось найти пакет</span><span class="sxs-lookup"><span data-stu-id="c319e-143">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="c319e-144">Ошибка обнаружения \\. Не удалось установить некоторые пакеты</span><span class="sxs-lookup"><span data-stu-id="c319e-144">Unable to locate \\ Some packages could not be installed</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="c319e-145">Ошибка получения</span><span class="sxs-lookup"><span data-stu-id="c319e-145">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="c319e-146">Snap-пакеты</span><span class="sxs-lookup"><span data-stu-id="c319e-146">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="c319e-147">Зависимости</span><span class="sxs-lookup"><span data-stu-id="c319e-147">Dependencies</span></span>

<span data-ttu-id="c319e-148">Если для установки используется диспетчер пакетов, эти библиотеки устанавливаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="c319e-148">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="c319e-149">Но если вы устанавливаете .NET Core вручную или публикуете автономное приложение, вам потребуется установить эти библиотеки:</span><span class="sxs-lookup"><span data-stu-id="c319e-149">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="c319e-150">libc6</span><span class="sxs-lookup"><span data-stu-id="c319e-150">libc6</span></span>
- <span data-ttu-id="c319e-151">libgcc1</span><span class="sxs-lookup"><span data-stu-id="c319e-151">libgcc1</span></span>
- <span data-ttu-id="c319e-152">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="c319e-152">libgssapi-krb5-2</span></span>
- <span data-ttu-id="c319e-153">libicu52 (для 8.x)</span><span class="sxs-lookup"><span data-stu-id="c319e-153">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="c319e-154">libicu57 (для 9.x)</span><span class="sxs-lookup"><span data-stu-id="c319e-154">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="c319e-155">libicu63 (для 10.x)</span><span class="sxs-lookup"><span data-stu-id="c319e-155">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="c319e-156">libicu67 (для 11.x)</span><span class="sxs-lookup"><span data-stu-id="c319e-156">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="c319e-157">libssl1.0.0 (для 8.x)</span><span class="sxs-lookup"><span data-stu-id="c319e-157">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="c319e-158">libssl1.1 (для 9.x-11.x)</span><span class="sxs-lookup"><span data-stu-id="c319e-158">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="c319e-159">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="c319e-159">libstdc++6</span></span>
- <span data-ttu-id="c319e-160">zlib1g</span><span class="sxs-lookup"><span data-stu-id="c319e-160">zlib1g</span></span>

<span data-ttu-id="c319e-161">Для приложений .NET Core, использующих сборку *System.Drawing.Common*, необходима также следующая зависимость:</span><span class="sxs-lookup"><span data-stu-id="c319e-161">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="c319e-162">libgdiplus (версия 6.0.1 или выше)</span><span class="sxs-lookup"><span data-stu-id="c319e-162">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="c319e-163">Вы можете установить последнюю версию *libgdiplus*, добавив в систему репозиторий Mono.</span><span class="sxs-lookup"><span data-stu-id="c319e-163">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="c319e-164">Для получения дополнительной информации см. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="c319e-164">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="c319e-165">Установка с помощью скрипта</span><span class="sxs-lookup"><span data-stu-id="c319e-165">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="c319e-166">Установка вручную</span><span class="sxs-lookup"><span data-stu-id="c319e-166">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="c319e-167">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="c319e-167">Next steps</span></span>

- [<span data-ttu-id="c319e-168">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c319e-168">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
