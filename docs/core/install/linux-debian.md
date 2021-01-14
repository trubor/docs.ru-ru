---
title: Установка .NET в Debian — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в Debian.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 913d8bffdd6c0b5e88a70dae0ec4c8d732e80cc0
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970841"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-debian"></a><span data-ttu-id="95a46-103">Установка пакета SDK для .NET или среды выполнения .NET в Debian</span><span class="sxs-lookup"><span data-stu-id="95a46-103">Install the .NET SDK or the .NET Runtime on Debian</span></span>

<span data-ttu-id="95a46-104">В этой статье описано, как установить .NET в Debian.</span><span class="sxs-lookup"><span data-stu-id="95a46-104">This article describes how to install .NET on Debian.</span></span> <span data-ttu-id="95a46-105">Если поддержка какой-либо версии Debian прекращается, то .NET также перестает поддерживать ее.</span><span class="sxs-lookup"><span data-stu-id="95a46-105">When a Debian version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="95a46-106">Но с помощью этих инструкций вы сможете запустить .NET даже в неподдерживаемых версиях.</span><span class="sxs-lookup"><span data-stu-id="95a46-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="95a46-107">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="95a46-107">Supported distributions</span></span>

<span data-ttu-id="95a46-108">В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET и версий Debian, в которых они поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="95a46-108">The following table is a list of currently supported .NET releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="95a46-109">Эти версии поддерживаются до того же времени, что и версия [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или [Debian](https://wiki.debian.org/DebianReleases).</span><span class="sxs-lookup"><span data-stu-id="95a46-109">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="95a46-110">Значок ✔️ означает, что версия Debian или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="95a46-110">A ✔️ indicates that the version of Debian or .NET is still supported.</span></span>
- <span data-ttu-id="95a46-111">Значок ❌ означает, что версия Debian или версия .NET в таком выпуске Debian не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="95a46-111">A ❌ indicates that the version of Debian or .NET isn't supported on that Debian release.</span></span>
- <span data-ttu-id="95a46-112">Если значок ✔️ стоит как напротив версии Debian, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="95a46-112">When both a version of Debian and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="95a46-113">Debian</span><span class="sxs-lookup"><span data-stu-id="95a46-113">Debian</span></span>                   | <span data-ttu-id="95a46-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="95a46-114">.NET Core 2.1</span></span> | <span data-ttu-id="95a46-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="95a46-115">.NET Core 3.1</span></span> | <span data-ttu-id="95a46-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="95a46-116">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="95a46-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="95a46-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="95a46-118">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="95a46-118">✔️ 2.1</span></span>        | <span data-ttu-id="95a46-119">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="95a46-119">✔️ 3.1</span></span>        | <span data-ttu-id="95a46-120">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="95a46-120">✔️ 5.0</span></span> |
| <span data-ttu-id="95a46-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="95a46-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="95a46-122">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="95a46-122">✔️ 2.1</span></span>        | <span data-ttu-id="95a46-123">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="95a46-123">✔️ 3.1</span></span>        | <span data-ttu-id="95a46-124">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="95a46-124">✔️ 5.0</span></span> |
| <span data-ttu-id="95a46-125">❌ [8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="95a46-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="95a46-126">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="95a46-126">✔️ 2.1</span></span>        | <span data-ttu-id="95a46-127">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="95a46-127">❌ 3.1</span></span>        | <span data-ttu-id="95a46-128">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="95a46-128">❌ 5.0</span></span> |

<span data-ttu-id="95a46-129">Следующие версии .NET больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="95a46-129">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="95a46-130">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="95a46-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="95a46-131">3.0</span><span class="sxs-lookup"><span data-stu-id="95a46-131">3.0</span></span>
- <span data-ttu-id="95a46-132">2.2</span><span class="sxs-lookup"><span data-stu-id="95a46-132">2.2</span></span>
- <span data-ttu-id="95a46-133">2.0</span><span class="sxs-lookup"><span data-stu-id="95a46-133">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="95a46-134">Удалите предварительные версии</span><span class="sxs-lookup"><span data-stu-id="95a46-134">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="debian-10-"></a><span data-ttu-id="95a46-135">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="95a46-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="95a46-136">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="95a46-136">Debian 9 ✔️</span></span>

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

## <a name="debian-8-"></a><span data-ttu-id="95a46-137">Debian 8 ❌</span><span class="sxs-lookup"><span data-stu-id="95a46-137">Debian 8 ❌</span></span>

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

## <a name="how-to-install-other-versions"></a><span data-ttu-id="95a46-138">Установка других версий</span><span class="sxs-lookup"><span data-stu-id="95a46-138">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="use-apt-to-update-net"></a><span data-ttu-id="95a46-139">Обновление .NET с помощью APT</span><span class="sxs-lookup"><span data-stu-id="95a46-139">Use APT to update .NET</span></span>

<span data-ttu-id="95a46-140">Если для .NET доступен новый выпуск исправлений, можете выполнить обновление с помощью APT и следующих команд:</span><span class="sxs-lookup"><span data-stu-id="95a46-140">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="95a46-141">Устранение неполадок с APT</span><span class="sxs-lookup"><span data-stu-id="95a46-141">APT troubleshooting</span></span>

<span data-ttu-id="95a46-142">В этом разделе описаны распространенные ошибки, которые могут возникнуть при использовании APT для установки .NET.</span><span class="sxs-lookup"><span data-stu-id="95a46-142">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="95a46-143">Не удалось найти пакет</span><span class="sxs-lookup"><span data-stu-id="95a46-143">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="95a46-144">Ошибка обнаружения \\. Не удалось установить некоторые пакеты</span><span class="sxs-lookup"><span data-stu-id="95a46-144">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="95a46-145">Ошибка получения</span><span class="sxs-lookup"><span data-stu-id="95a46-145">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="dependencies"></a><span data-ttu-id="95a46-146">Зависимости</span><span class="sxs-lookup"><span data-stu-id="95a46-146">Dependencies</span></span>

<span data-ttu-id="95a46-147">Если для установки используется диспетчер пакетов, эти библиотеки устанавливаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="95a46-147">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="95a46-148">Но если вы устанавливаете .NET Core вручную или публикуете автономное приложение, вам потребуется установить эти библиотеки:</span><span class="sxs-lookup"><span data-stu-id="95a46-148">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="95a46-149">libc6</span><span class="sxs-lookup"><span data-stu-id="95a46-149">libc6</span></span>
- <span data-ttu-id="95a46-150">libgcc1</span><span class="sxs-lookup"><span data-stu-id="95a46-150">libgcc1</span></span>
- <span data-ttu-id="95a46-151">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="95a46-151">libgssapi-krb5-2</span></span>
- <span data-ttu-id="95a46-152">libicu52 (для 8.x)</span><span class="sxs-lookup"><span data-stu-id="95a46-152">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="95a46-153">libicu57 (для 9.x)</span><span class="sxs-lookup"><span data-stu-id="95a46-153">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="95a46-154">libicu63 (для 10.x)</span><span class="sxs-lookup"><span data-stu-id="95a46-154">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="95a46-155">libicu67 (для 11.x)</span><span class="sxs-lookup"><span data-stu-id="95a46-155">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="95a46-156">libssl1.0.0 (для 8.x)</span><span class="sxs-lookup"><span data-stu-id="95a46-156">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="95a46-157">libssl1.1 (для 9.x-11.x)</span><span class="sxs-lookup"><span data-stu-id="95a46-157">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="95a46-158">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="95a46-158">libstdc++6</span></span>
- <span data-ttu-id="95a46-159">zlib1g</span><span class="sxs-lookup"><span data-stu-id="95a46-159">zlib1g</span></span>

<span data-ttu-id="95a46-160">Для приложений .NET Core, использующих сборку *System.Drawing.Common*, необходима также следующая зависимость:</span><span class="sxs-lookup"><span data-stu-id="95a46-160">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="95a46-161">libgdiplus (версия 6.0.1 или выше)</span><span class="sxs-lookup"><span data-stu-id="95a46-161">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="95a46-162">Вы можете установить последнюю версию *libgdiplus*, добавив в систему репозиторий Mono.</span><span class="sxs-lookup"><span data-stu-id="95a46-162">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="95a46-163">Для получения дополнительной информации см. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="95a46-163">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="95a46-164">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="95a46-164">Next steps</span></span>

- [<span data-ttu-id="95a46-165">Включение заполнения клавишей TAB для .NET CLI</span><span class="sxs-lookup"><span data-stu-id="95a46-165">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="95a46-166">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="95a46-166">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
