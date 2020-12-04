---
title: Установка .NET в Fedora — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в Fedora.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: f7422941af7e39d69d286a0f79920b025c1bf9c0
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031908"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="f1513-103">Установка пакета SDK для .NET или среды выполнения .NET в Fedora</span><span class="sxs-lookup"><span data-stu-id="f1513-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="f1513-104">.NET поддерживается в Fedora.</span><span class="sxs-lookup"><span data-stu-id="f1513-104">.NET is supported on Fedora.</span></span> <span data-ttu-id="f1513-105">В этой статье описано, как установить .NET в Fedora.</span><span class="sxs-lookup"><span data-stu-id="f1513-105">This article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="f1513-106">Если поддержка какой-либо версии Fedora прекращается, то .NET также перестает поддерживать ее.</span><span class="sxs-lookup"><span data-stu-id="f1513-106">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="f1513-107">Но с помощью этих инструкций вы сможете запустить .NET даже в неподдерживаемых версиях.</span><span class="sxs-lookup"><span data-stu-id="f1513-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="f1513-108">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="f1513-108">Supported distributions</span></span>

<span data-ttu-id="f1513-109">В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET и версий Fedora, в которых они поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="f1513-109">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="f1513-110">Эти версии поддерживаются до того же времени, что и версия [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или [Fedora](https://fedoraproject.org/wiki/End_of_life).</span><span class="sxs-lookup"><span data-stu-id="f1513-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="f1513-111">Значок ✔️ означает, что версия Fedora или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="f1513-111">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="f1513-112">Значок ❌ означает, что версия Fedora или версия .NET в таком выпуске Fedora не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="f1513-112">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="f1513-113">Если значок ✔️ стоит как напротив версии Fedora, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="f1513-113">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="f1513-114">Fedora</span><span class="sxs-lookup"><span data-stu-id="f1513-114">Fedora</span></span>               | <span data-ttu-id="f1513-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f1513-115">.NET Core 2.1</span></span> | <span data-ttu-id="f1513-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="f1513-116">.NET Core 3.1</span></span> | <span data-ttu-id="f1513-117">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="f1513-117">.NET 5.0</span></span> |
|----------------------|---------------|---------------|----------|
| <span data-ttu-id="f1513-118">✔️ [33](#fedora-33-)</span><span class="sxs-lookup"><span data-stu-id="f1513-118">✔️ [33](#fedora-33-)</span></span> | <span data-ttu-id="f1513-119">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f1513-119">✔️ 2.1</span></span>        | <span data-ttu-id="f1513-120">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f1513-120">✔️ 3.1</span></span>        | <span data-ttu-id="f1513-121">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="f1513-121">✔️ 5.0</span></span> |
| <span data-ttu-id="f1513-122">✔️ [32](#fedora-32-)</span><span class="sxs-lookup"><span data-stu-id="f1513-122">✔️ [32](#fedora-32-)</span></span> | <span data-ttu-id="f1513-123">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f1513-123">✔️ 2.1</span></span>        | <span data-ttu-id="f1513-124">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f1513-124">✔️ 3.1</span></span>        | <span data-ttu-id="f1513-125">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="f1513-125">✔️ 5.0</span></span> |
| <span data-ttu-id="f1513-126">❌ [31](#fedora-31-)</span><span class="sxs-lookup"><span data-stu-id="f1513-126">❌ [31](#fedora-31-)</span></span> | <span data-ttu-id="f1513-127">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f1513-127">✔️ 2.1</span></span>        | <span data-ttu-id="f1513-128">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f1513-128">✔️ 3.1</span></span>        | <span data-ttu-id="f1513-129">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="f1513-129">❌ 5.0</span></span> |
| <span data-ttu-id="f1513-130">❌ [30](#fedora-30-)</span><span class="sxs-lookup"><span data-stu-id="f1513-130">❌ [30](#fedora-30-)</span></span> | <span data-ttu-id="f1513-131">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f1513-131">✔️ 2.1</span></span>        | <span data-ttu-id="f1513-132">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f1513-132">✔️ 3.1</span></span>        | <span data-ttu-id="f1513-133">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="f1513-133">❌ 5.0</span></span> |
| <span data-ttu-id="f1513-134">❌ [29](#fedora-29-)</span><span class="sxs-lookup"><span data-stu-id="f1513-134">❌ [29](#fedora-29-)</span></span> | <span data-ttu-id="f1513-135">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f1513-135">✔️ 2.1</span></span>        | <span data-ttu-id="f1513-136">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f1513-136">✔️ 3.1</span></span>        | <span data-ttu-id="f1513-137">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="f1513-137">❌ 5.0</span></span> |
| <span data-ttu-id="f1513-138">❌ [28](#fedora-28-)</span><span class="sxs-lookup"><span data-stu-id="f1513-138">❌ [28](#fedora-28-)</span></span> | <span data-ttu-id="f1513-139">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f1513-139">✔️ 2.1</span></span>        | <span data-ttu-id="f1513-140">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="f1513-140">❌ 3.1</span></span>        | <span data-ttu-id="f1513-141">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="f1513-141">❌ 5.0</span></span> |
| <span data-ttu-id="f1513-142">❌ [27](#fedora-27-)</span><span class="sxs-lookup"><span data-stu-id="f1513-142">❌ [27](#fedora-27-)</span></span> | <span data-ttu-id="f1513-143">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f1513-143">✔️ 2.1</span></span>        | <span data-ttu-id="f1513-144">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="f1513-144">❌ 3.1</span></span>        | <span data-ttu-id="f1513-145">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="f1513-145">❌ 5.0</span></span> |

<span data-ttu-id="f1513-146">Следующие версии .NET больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="f1513-146">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="f1513-147">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="f1513-147">The downloads for these still remain published:</span></span>

- <span data-ttu-id="f1513-148">3.0</span><span class="sxs-lookup"><span data-stu-id="f1513-148">3.0</span></span>
- <span data-ttu-id="f1513-149">2.2</span><span class="sxs-lookup"><span data-stu-id="f1513-149">2.2</span></span>
- <span data-ttu-id="f1513-150">2.0</span><span class="sxs-lookup"><span data-stu-id="f1513-150">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="f1513-151">Удалите предварительные версии</span><span class="sxs-lookup"><span data-stu-id="f1513-151">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="f1513-152">Установка других версий</span><span class="sxs-lookup"><span data-stu-id="f1513-152">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-33-"></a><span data-ttu-id="f1513-153">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="f1513-153">Fedora 33 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="f1513-154">.NET Core 3.1 предоставляется в репозиториях пакетов по умолчанию для Fedora 33.</span><span class="sxs-lookup"><span data-stu-id="f1513-154">.NET Core 3.1 is available in the default package repositories for Fedora 33.</span></span> <span data-ttu-id="f1513-155">Чтобы установить .NET Core 3.1, используйте команду `dnf install` с соответствующим пакетом, например `aspnetcore-runtime-3.1` или `dotnet-sdk-3.1`.</span><span class="sxs-lookup"><span data-stu-id="f1513-155">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="f1513-156">.NET 5.0 еще не предоставляется в репозиториях пакетов по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f1513-156">.NET 5.0 isn't yet available in the default package repositories.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/33/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-32-"></a><span data-ttu-id="f1513-157">Fedora 32 ✔️</span><span class="sxs-lookup"><span data-stu-id="f1513-157">Fedora 32 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="f1513-158">.NET Core 3.1 предоставляется в репозиториях пакетов по умолчанию для Fedora 32.</span><span class="sxs-lookup"><span data-stu-id="f1513-158">.NET Core 3.1 is available in the default package repositories for Fedora 32.</span></span> <span data-ttu-id="f1513-159">Чтобы установить .NET Core 3.1, используйте команду `dnf install` с соответствующим пакетом, например `aspnetcore-runtime-3.1` или `dotnet-sdk-3.1`.</span><span class="sxs-lookup"><span data-stu-id="f1513-159">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="f1513-160">.NET 5.0 еще не предоставляется в репозиториях пакетов по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f1513-160">.NET 5.0 isn't yet available in the default package repositories.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/32/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-31-"></a><span data-ttu-id="f1513-161">Fedora 31 ❌</span><span class="sxs-lookup"><span data-stu-id="f1513-161">Fedora 31 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a><span data-ttu-id="f1513-162">Fedora 30 ❌</span><span class="sxs-lookup"><span data-stu-id="f1513-162">Fedora 30 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a><span data-ttu-id="f1513-163">Fedora 29 ❌</span><span class="sxs-lookup"><span data-stu-id="f1513-163">Fedora 29 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a><span data-ttu-id="f1513-164">Fedora 28 ❌</span><span class="sxs-lookup"><span data-stu-id="f1513-164">Fedora 28 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a><span data-ttu-id="f1513-165">Fedora 27 ❌</span><span class="sxs-lookup"><span data-stu-id="f1513-165">Fedora 27 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="f1513-166">Устранение неполадок диспетчера пакетов</span><span class="sxs-lookup"><span data-stu-id="f1513-166">Troubleshoot the package manager</span></span>

<span data-ttu-id="f1513-167">В этом разделе описаны распространенные ошибки, которые могут возникнуть при использовании диспетчера пакетов для установки .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f1513-167">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="f1513-168">Не удалось найти пакет</span><span class="sxs-lookup"><span data-stu-id="f1513-168">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="f1513-169">Ошибка получения</span><span class="sxs-lookup"><span data-stu-id="f1513-169">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="f1513-170">Snap-пакеты</span><span class="sxs-lookup"><span data-stu-id="f1513-170">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="f1513-171">Зависимости</span><span class="sxs-lookup"><span data-stu-id="f1513-171">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="f1513-172">Установка с помощью скрипта</span><span class="sxs-lookup"><span data-stu-id="f1513-172">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="f1513-173">Установка вручную</span><span class="sxs-lookup"><span data-stu-id="f1513-173">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="f1513-174">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="f1513-174">Next steps</span></span>

- [<span data-ttu-id="f1513-175">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f1513-175">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
