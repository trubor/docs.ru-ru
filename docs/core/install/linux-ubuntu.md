---
title: Установка .NET в Ubuntu — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в Ubuntu.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 14e5e9548d4aa09a586e2038f3e35a489ee65cd2
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970774"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-ubuntu"></a><span data-ttu-id="4182e-103">Установка пакета SDK для .NET или среды выполнения .NET в Ubuntu</span><span class="sxs-lookup"><span data-stu-id="4182e-103">Install the .NET SDK or the .NET Runtime on Ubuntu</span></span>

<span data-ttu-id="4182e-104">.NET поддерживается в Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="4182e-104">.NET is supported on Ubuntu.</span></span> <span data-ttu-id="4182e-105">В этой статье описано, как установить .NET в Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="4182e-105">This article describes how to install .NET on Ubuntu.</span></span> <span data-ttu-id="4182e-106">Если поддержка какой-либо версии Ubuntu прекращается, то .NET также перестает поддерживать ее.</span><span class="sxs-lookup"><span data-stu-id="4182e-106">When an Ubuntu version falls out of support, .NET is no longer supported with that version.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="4182e-107">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="4182e-107">Supported distributions</span></span>

<span data-ttu-id="4182e-108">В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET и версий Ubuntu, в которых они поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="4182e-108">The following table is a list of currently supported .NET releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="4182e-109">Эти версии поддерживаются до того же времени, что и версия [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или [Ubuntu](https://wiki.ubuntu.com/Releases).</span><span class="sxs-lookup"><span data-stu-id="4182e-109">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="4182e-110">Значок ✔️ означает, что версия Ubuntu или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="4182e-110">A ✔️ indicates that the version of Ubuntu or .NET is still supported.</span></span>
- <span data-ttu-id="4182e-111">Значок ❌ означает, что версия Ubuntu или версия .NET в таком выпуске Ubuntu не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="4182e-111">A ❌ indicates that the version of Ubuntu or .NET isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="4182e-112">Если значок ✔️ стоит как напротив версии Ubuntu, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="4182e-112">When both a version of Ubuntu and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="4182e-113">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="4182e-113">Ubuntu</span></span>                   | <span data-ttu-id="4182e-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4182e-114">.NET Core 2.1</span></span> | <span data-ttu-id="4182e-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="4182e-115">.NET Core 3.1</span></span> | <span data-ttu-id="4182e-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="4182e-116">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="4182e-117">✔️ [20.10](#2010-)</span><span class="sxs-lookup"><span data-stu-id="4182e-117">✔️ [20.10](#2010-)</span></span>       | <span data-ttu-id="4182e-118">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="4182e-118">✔️ 2.1</span></span>        | <span data-ttu-id="4182e-119">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="4182e-119">✔️ 3.1</span></span>        | <span data-ttu-id="4182e-120">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="4182e-120">✔️ 5.0</span></span> |
| <span data-ttu-id="4182e-121">✔️ [20.04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="4182e-121">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="4182e-122">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="4182e-122">✔️ 2.1</span></span>        | <span data-ttu-id="4182e-123">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="4182e-123">✔️ 3.1</span></span>        | <span data-ttu-id="4182e-124">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="4182e-124">✔️ 5.0</span></span> |
| <span data-ttu-id="4182e-125">❌ [19.10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="4182e-125">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="4182e-126">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="4182e-126">✔️ 2.1</span></span>        | <span data-ttu-id="4182e-127">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="4182e-127">✔️ 3.1</span></span>        | <span data-ttu-id="4182e-128">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="4182e-128">✔️ 5.0</span></span> |
| <span data-ttu-id="4182e-129">❌ [19.04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="4182e-129">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="4182e-130">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="4182e-130">✔️ 2.1</span></span>        | <span data-ttu-id="4182e-131">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="4182e-131">✔️ 3.1</span></span>        | <span data-ttu-id="4182e-132">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="4182e-132">❌ 5.0</span></span> |
| <span data-ttu-id="4182e-133">❌ [18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="4182e-133">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="4182e-134">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="4182e-134">✔️ 2.1</span></span>        | <span data-ttu-id="4182e-135">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="4182e-135">❌ 3.1</span></span>        | <span data-ttu-id="4182e-136">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="4182e-136">❌ 5.0</span></span> |
| <span data-ttu-id="4182e-137">✔️ [18.04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="4182e-137">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="4182e-138">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="4182e-138">✔️ 2.1</span></span>        | <span data-ttu-id="4182e-139">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="4182e-139">✔️ 3.1</span></span>        | <span data-ttu-id="4182e-140">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="4182e-140">✔️ 5.0</span></span> |
| <span data-ttu-id="4182e-141">❌ [17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="4182e-141">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="4182e-142">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="4182e-142">✔️ 2.1</span></span>        | <span data-ttu-id="4182e-143">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="4182e-143">❌ 3.1</span></span>        | <span data-ttu-id="4182e-144">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="4182e-144">❌ 5.0</span></span> |
| <span data-ttu-id="4182e-145">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="4182e-145">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="4182e-146">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="4182e-146">✔️ 2.1</span></span>        | <span data-ttu-id="4182e-147">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="4182e-147">❌ 3.1</span></span>        | <span data-ttu-id="4182e-148">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="4182e-148">❌ 5.0</span></span> |
| <span data-ttu-id="4182e-149">❌ [16.10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="4182e-149">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="4182e-150">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="4182e-150">❌ 2.1</span></span>        | <span data-ttu-id="4182e-151">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="4182e-151">❌ 3.1</span></span>        | <span data-ttu-id="4182e-152">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="4182e-152">❌ 5.0</span></span> |
| <span data-ttu-id="4182e-153">✔️ [16.04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="4182e-153">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="4182e-154">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="4182e-154">✔️ 2.1</span></span>        | <span data-ttu-id="4182e-155">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="4182e-155">✔️ 3.1</span></span>        | <span data-ttu-id="4182e-156">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="4182e-156">✔️ 5.0</span></span> |

<span data-ttu-id="4182e-157">Следующие версии .NET больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="4182e-157">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="4182e-158">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="4182e-158">The downloads for these still remain published:</span></span>

- <span data-ttu-id="4182e-159">3.0</span><span class="sxs-lookup"><span data-stu-id="4182e-159">3.0</span></span>
- <span data-ttu-id="4182e-160">2.2</span><span class="sxs-lookup"><span data-stu-id="4182e-160">2.2</span></span>
- <span data-ttu-id="4182e-161">2.0</span><span class="sxs-lookup"><span data-stu-id="4182e-161">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="4182e-162">Удалите предварительные версии</span><span class="sxs-lookup"><span data-stu-id="4182e-162">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="2010-"></a><span data-ttu-id="4182e-163">20.10 ✔️</span><span class="sxs-lookup"><span data-stu-id="4182e-163">20.10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="2004-"></a><span data-ttu-id="4182e-164">20.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="4182e-164">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1910-"></a><span data-ttu-id="4182e-165">19.10 ❌</span><span class="sxs-lookup"><span data-stu-id="4182e-165">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="4182e-166">19.04 ❌</span><span class="sxs-lookup"><span data-stu-id="4182e-166">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="4182e-167">18.10 ❌</span><span class="sxs-lookup"><span data-stu-id="4182e-167">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="4182e-168">18.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="4182e-168">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1710-"></a><span data-ttu-id="4182e-169">17.10 ❌</span><span class="sxs-lookup"><span data-stu-id="4182e-169">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="4182e-170">17.04 ❌</span><span class="sxs-lookup"><span data-stu-id="4182e-170">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="4182e-171">16.10 ❌</span><span class="sxs-lookup"><span data-stu-id="4182e-171">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="4182e-172">16.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="4182e-172">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="4182e-173">Установка других версий</span><span class="sxs-lookup"><span data-stu-id="4182e-173">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="use-apt-to-update-net"></a><span data-ttu-id="4182e-174">Обновление .NET с помощью APT</span><span class="sxs-lookup"><span data-stu-id="4182e-174">Use APT to update .NET</span></span>

<span data-ttu-id="4182e-175">Если для .NET доступен новый выпуск исправлений, можете выполнить обновление с помощью APT и следующих команд:</span><span class="sxs-lookup"><span data-stu-id="4182e-175">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="4182e-176">Устранение неполадок с APT</span><span class="sxs-lookup"><span data-stu-id="4182e-176">APT troubleshooting</span></span>

<span data-ttu-id="4182e-177">В этом разделе описаны распространенные ошибки, которые могут возникнуть при использовании APT для установки .NET.</span><span class="sxs-lookup"><span data-stu-id="4182e-177">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="4182e-178">Не удалось найти пакет</span><span class="sxs-lookup"><span data-stu-id="4182e-178">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="4182e-179">Ошибка обнаружения \\. Не удалось установить некоторые пакеты</span><span class="sxs-lookup"><span data-stu-id="4182e-179">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="4182e-180">Ошибка получения</span><span class="sxs-lookup"><span data-stu-id="4182e-180">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="dependencies"></a><span data-ttu-id="4182e-181">Зависимости</span><span class="sxs-lookup"><span data-stu-id="4182e-181">Dependencies</span></span>

<span data-ttu-id="4182e-182">Если для установки используется диспетчер пакетов, эти библиотеки устанавливаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="4182e-182">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="4182e-183">Но если вы устанавливаете .NET вручную или публикуете автономное приложение, вам потребуется установить эти библиотеки:</span><span class="sxs-lookup"><span data-stu-id="4182e-183">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="4182e-184">libc6</span><span class="sxs-lookup"><span data-stu-id="4182e-184">libc6</span></span>
- <span data-ttu-id="4182e-185">libgcc1</span><span class="sxs-lookup"><span data-stu-id="4182e-185">libgcc1</span></span>
- <span data-ttu-id="4182e-186">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="4182e-186">libgssapi-krb5-2</span></span>
- <span data-ttu-id="4182e-187">libicu52 (для 14.x)</span><span class="sxs-lookup"><span data-stu-id="4182e-187">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="4182e-188">libicu55 (для 16.x)</span><span class="sxs-lookup"><span data-stu-id="4182e-188">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="4182e-189">libicu60 (для 18.x)</span><span class="sxs-lookup"><span data-stu-id="4182e-189">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="4182e-190">libicu66 (для 20.x)</span><span class="sxs-lookup"><span data-stu-id="4182e-190">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="4182e-191">libssl1.0.0 (для 14.x, 16.x)</span><span class="sxs-lookup"><span data-stu-id="4182e-191">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="4182e-192">libssl1.1 (для 18.x, 20.x)</span><span class="sxs-lookup"><span data-stu-id="4182e-192">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="4182e-193">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="4182e-193">libstdc++6</span></span>
- <span data-ttu-id="4182e-194">zlib1g</span><span class="sxs-lookup"><span data-stu-id="4182e-194">zlib1g</span></span>

<span data-ttu-id="4182e-195">Для приложений .NET, использующих сборку *System.Drawing.Common*, необходима также следующая зависимость:</span><span class="sxs-lookup"><span data-stu-id="4182e-195">For .NET apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="4182e-196">libgdiplus (версия 6.0.1 или выше)</span><span class="sxs-lookup"><span data-stu-id="4182e-196">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="4182e-197">Вы можете установить последнюю версию *libgdiplus*, добавив в систему репозиторий Mono.</span><span class="sxs-lookup"><span data-stu-id="4182e-197">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="4182e-198">Для получения дополнительной информации см. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="4182e-198">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4182e-199">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="4182e-199">Next steps</span></span>

- [<span data-ttu-id="4182e-200">Включение заполнения клавишей TAB для .NET CLI</span><span class="sxs-lookup"><span data-stu-id="4182e-200">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="4182e-201">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4182e-201">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
