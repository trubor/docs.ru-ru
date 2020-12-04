---
title: Установка .NET в Ubuntu — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в Ubuntu.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 22ce3379e028f065528e1f507a2d8c1ae598f0e8
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031854"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-ubuntu"></a><span data-ttu-id="7fd0b-103">Установка пакета SDK для .NET или среды выполнения .NET в Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7fd0b-103">Install the .NET SDK or the .NET Runtime on Ubuntu</span></span>

<span data-ttu-id="7fd0b-104">.NET поддерживается в Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="7fd0b-104">.NET is supported on Ubuntu.</span></span> <span data-ttu-id="7fd0b-105">В этой статье описано, как установить .NET в Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="7fd0b-105">This article describes how to install .NET on Ubuntu.</span></span> <span data-ttu-id="7fd0b-106">Если поддержка какой-либо версии Ubuntu прекращается, то .NET также перестает поддерживать ее.</span><span class="sxs-lookup"><span data-stu-id="7fd0b-106">When an Ubuntu version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="7fd0b-107">Но с помощью этих инструкций вы сможете запустить .NET даже в неподдерживаемых версиях.</span><span class="sxs-lookup"><span data-stu-id="7fd0b-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="7fd0b-108">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="7fd0b-108">Supported distributions</span></span>

<span data-ttu-id="7fd0b-109">В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET и версий Ubuntu, в которых они поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="7fd0b-109">The following table is a list of currently supported .NET releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="7fd0b-110">Эти версии поддерживаются до того же времени, что и версия [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или [Ubuntu](https://wiki.ubuntu.com/Releases).</span><span class="sxs-lookup"><span data-stu-id="7fd0b-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="7fd0b-111">Значок ✔️ означает, что версия Ubuntu или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="7fd0b-111">A ✔️ indicates that the version of Ubuntu or .NET is still supported.</span></span>
- <span data-ttu-id="7fd0b-112">Значок ❌ означает, что версия Ubuntu или версия .NET в таком выпуске Ubuntu не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="7fd0b-112">A ❌ indicates that the version of Ubuntu or .NET isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="7fd0b-113">Если значок ✔️ стоит как напротив версии Ubuntu, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="7fd0b-113">When both a version of Ubuntu and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="7fd0b-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="7fd0b-114">Ubuntu</span></span>                   | <span data-ttu-id="7fd0b-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-115">.NET Core 2.1</span></span> | <span data-ttu-id="7fd0b-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-116">.NET Core 3.1</span></span> | <span data-ttu-id="7fd0b-117">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="7fd0b-117">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="7fd0b-118">✔️ [20.10](#2010-)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-118">✔️ [20.10](#2010-)</span></span>       | <span data-ttu-id="7fd0b-119">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-119">✔️ 2.1</span></span>        | <span data-ttu-id="7fd0b-120">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-120">✔️ 3.1</span></span>        | <span data-ttu-id="7fd0b-121">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="7fd0b-121">✔️ 5.0</span></span> |
| <span data-ttu-id="7fd0b-122">✔️ [20.04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-122">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="7fd0b-123">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-123">✔️ 2.1</span></span>        | <span data-ttu-id="7fd0b-124">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-124">✔️ 3.1</span></span>        | <span data-ttu-id="7fd0b-125">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="7fd0b-125">✔️ 5.0</span></span> |
| <span data-ttu-id="7fd0b-126">❌ [19.10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-126">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="7fd0b-127">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-127">✔️ 2.1</span></span>        | <span data-ttu-id="7fd0b-128">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-128">✔️ 3.1</span></span>        | <span data-ttu-id="7fd0b-129">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="7fd0b-129">✔️ 5.0</span></span> |
| <span data-ttu-id="7fd0b-130">❌ [19.04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-130">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="7fd0b-131">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-131">✔️ 2.1</span></span>        | <span data-ttu-id="7fd0b-132">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-132">✔️ 3.1</span></span>        | <span data-ttu-id="7fd0b-133">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="7fd0b-133">❌ 5.0</span></span> |
| <span data-ttu-id="7fd0b-134">❌ [18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-134">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="7fd0b-135">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-135">✔️ 2.1</span></span>        | <span data-ttu-id="7fd0b-136">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-136">❌ 3.1</span></span>        | <span data-ttu-id="7fd0b-137">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="7fd0b-137">❌ 5.0</span></span> |
| <span data-ttu-id="7fd0b-138">✔️ [18.04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-138">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="7fd0b-139">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-139">✔️ 2.1</span></span>        | <span data-ttu-id="7fd0b-140">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-140">✔️ 3.1</span></span>        | <span data-ttu-id="7fd0b-141">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="7fd0b-141">✔️ 5.0</span></span> |
| <span data-ttu-id="7fd0b-142">❌ [17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-142">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="7fd0b-143">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-143">✔️ 2.1</span></span>        | <span data-ttu-id="7fd0b-144">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-144">❌ 3.1</span></span>        | <span data-ttu-id="7fd0b-145">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="7fd0b-145">❌ 5.0</span></span> |
| <span data-ttu-id="7fd0b-146">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-146">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="7fd0b-147">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-147">✔️ 2.1</span></span>        | <span data-ttu-id="7fd0b-148">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-148">❌ 3.1</span></span>        | <span data-ttu-id="7fd0b-149">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="7fd0b-149">❌ 5.0</span></span> |
| <span data-ttu-id="7fd0b-150">❌ [16.10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-150">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="7fd0b-151">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-151">❌ 2.1</span></span>        | <span data-ttu-id="7fd0b-152">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-152">❌ 3.1</span></span>        | <span data-ttu-id="7fd0b-153">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="7fd0b-153">❌ 5.0</span></span> |
| <span data-ttu-id="7fd0b-154">✔️ [16.04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-154">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="7fd0b-155">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-155">✔️ 2.1</span></span>        | <span data-ttu-id="7fd0b-156">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-156">✔️ 3.1</span></span>        | <span data-ttu-id="7fd0b-157">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="7fd0b-157">✔️ 5.0</span></span> |

<span data-ttu-id="7fd0b-158">Следующие версии .NET больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="7fd0b-158">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="7fd0b-159">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="7fd0b-159">The downloads for these still remain published:</span></span>

- <span data-ttu-id="7fd0b-160">3.0</span><span class="sxs-lookup"><span data-stu-id="7fd0b-160">3.0</span></span>
- <span data-ttu-id="7fd0b-161">2.2</span><span class="sxs-lookup"><span data-stu-id="7fd0b-161">2.2</span></span>
- <span data-ttu-id="7fd0b-162">2.0</span><span class="sxs-lookup"><span data-stu-id="7fd0b-162">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="7fd0b-163">Удалите предварительные версии</span><span class="sxs-lookup"><span data-stu-id="7fd0b-163">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="7fd0b-164">Установка других версий</span><span class="sxs-lookup"><span data-stu-id="7fd0b-164">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2010-"></a><span data-ttu-id="7fd0b-165">20.10 ✔️</span><span class="sxs-lookup"><span data-stu-id="7fd0b-165">20.10 ✔️</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7fd0b-166">.NET Core 2.1 пока недоступна в веб-канале пакетов.</span><span class="sxs-lookup"><span data-stu-id="7fd0b-166">.NET Core 2.1 isn't yet available in the package feed.</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="2004-"></a><span data-ttu-id="7fd0b-167">20.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="7fd0b-167">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1910-"></a><span data-ttu-id="7fd0b-168">19.10 ❌</span><span class="sxs-lookup"><span data-stu-id="7fd0b-168">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="7fd0b-169">19.04 ❌</span><span class="sxs-lookup"><span data-stu-id="7fd0b-169">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="7fd0b-170">18.10 ❌</span><span class="sxs-lookup"><span data-stu-id="7fd0b-170">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="7fd0b-171">18.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="7fd0b-171">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1710-"></a><span data-ttu-id="7fd0b-172">17.10 ❌</span><span class="sxs-lookup"><span data-stu-id="7fd0b-172">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="7fd0b-173">17.04 ❌</span><span class="sxs-lookup"><span data-stu-id="7fd0b-173">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="7fd0b-174">16.10 ❌</span><span class="sxs-lookup"><span data-stu-id="7fd0b-174">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="7fd0b-175">16.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="7fd0b-175">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="7fd0b-176">Обновление пакета SDK или среды выполнения с помощью APT</span><span class="sxs-lookup"><span data-stu-id="7fd0b-176">APT update SDK or runtime</span></span>

<span data-ttu-id="7fd0b-177">Если для .NET доступен новый выпуск исправлений, можете выполнить обновление с помощью APT и следующих команд:</span><span class="sxs-lookup"><span data-stu-id="7fd0b-177">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="7fd0b-178">Устранение неполадок с APT</span><span class="sxs-lookup"><span data-stu-id="7fd0b-178">APT troubleshooting</span></span>

<span data-ttu-id="7fd0b-179">В этом разделе описаны распространенные ошибки, которые могут возникнуть при использовании APT для установки .NET.</span><span class="sxs-lookup"><span data-stu-id="7fd0b-179">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="7fd0b-180">Не удалось найти пакет</span><span class="sxs-lookup"><span data-stu-id="7fd0b-180">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="7fd0b-181">Ошибка обнаружения \\. Не удалось установить некоторые пакеты</span><span class="sxs-lookup"><span data-stu-id="7fd0b-181">Unable to locate \\ Some packages could not be installed</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="7fd0b-182">Ошибка получения</span><span class="sxs-lookup"><span data-stu-id="7fd0b-182">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="7fd0b-183">Snap-пакеты</span><span class="sxs-lookup"><span data-stu-id="7fd0b-183">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="7fd0b-184">Зависимости</span><span class="sxs-lookup"><span data-stu-id="7fd0b-184">Dependencies</span></span>

<span data-ttu-id="7fd0b-185">Если для установки используется диспетчер пакетов, эти библиотеки устанавливаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="7fd0b-185">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="7fd0b-186">Но если вы устанавливаете .NET вручную или публикуете автономное приложение, вам потребуется установить эти библиотеки:</span><span class="sxs-lookup"><span data-stu-id="7fd0b-186">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="7fd0b-187">libc6</span><span class="sxs-lookup"><span data-stu-id="7fd0b-187">libc6</span></span>
- <span data-ttu-id="7fd0b-188">libgcc1</span><span class="sxs-lookup"><span data-stu-id="7fd0b-188">libgcc1</span></span>
- <span data-ttu-id="7fd0b-189">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="7fd0b-189">libgssapi-krb5-2</span></span>
- <span data-ttu-id="7fd0b-190">libicu52 (для 14.x)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-190">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="7fd0b-191">libicu55 (для 16.x)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-191">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="7fd0b-192">libicu60 (для 18.x)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-192">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="7fd0b-193">libicu66 (для 20.x)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-193">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="7fd0b-194">libssl1.0.0 (для 14.x, 16.x)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-194">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="7fd0b-195">libssl1.1 (для 18.x, 20.x)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-195">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="7fd0b-196">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="7fd0b-196">libstdc++6</span></span>
- <span data-ttu-id="7fd0b-197">zlib1g</span><span class="sxs-lookup"><span data-stu-id="7fd0b-197">zlib1g</span></span>

<span data-ttu-id="7fd0b-198">Для приложений .NET, использующих сборку *System.Drawing.Common*, необходима также следующая зависимость:</span><span class="sxs-lookup"><span data-stu-id="7fd0b-198">For .NET apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="7fd0b-199">libgdiplus (версия 6.0.1 или выше)</span><span class="sxs-lookup"><span data-stu-id="7fd0b-199">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="7fd0b-200">Вы можете установить последнюю версию *libgdiplus*, добавив в систему репозиторий Mono.</span><span class="sxs-lookup"><span data-stu-id="7fd0b-200">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="7fd0b-201">Для получения дополнительной информации см. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="7fd0b-201">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="7fd0b-202">Установка с помощью скрипта</span><span class="sxs-lookup"><span data-stu-id="7fd0b-202">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="7fd0b-203">Установка вручную</span><span class="sxs-lookup"><span data-stu-id="7fd0b-203">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="7fd0b-204">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="7fd0b-204">Next steps</span></span>

- [<span data-ttu-id="7fd0b-205">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="7fd0b-205">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
