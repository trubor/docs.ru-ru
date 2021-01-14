---
title: Установка .NET в Fedora — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в Fedora.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 9dd8c6264831e2a9382960be505639f1eba95151
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970828"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="9e503-103">Установка пакета SDK для .NET или среды выполнения .NET в Fedora</span><span class="sxs-lookup"><span data-stu-id="9e503-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="9e503-104">Платформа .NET поддерживается в Fedora. В этой статье описано, как установить .NET в Fedora.</span><span class="sxs-lookup"><span data-stu-id="9e503-104">.NET is supported on Fedora and this article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="9e503-105">Если поддержка какой-либо версии Fedora прекращается, то .NET также перестает поддерживать ее.</span><span class="sxs-lookup"><span data-stu-id="9e503-105">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="install-net-50"></a><span data-ttu-id="9e503-106">Установка .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="9e503-106">Install .NET 5.0</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="9e503-107">**Fedora 32**</span><span class="sxs-lookup"><span data-stu-id="9e503-107">**Fedora 32**</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/32/prod.repo
```

<span data-ttu-id="9e503-108">**Fedora 33**</span><span class="sxs-lookup"><span data-stu-id="9e503-108">**Fedora 33**</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/33/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="install-net-core-31"></a><span data-ttu-id="9e503-109">Установка .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="9e503-109">Install .NET Core 3.1</span></span>

<span data-ttu-id="9e503-110">Последней версией .NET, которая представлена в репозиториях пакетов по умолчанию для Fedora 33, является .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="9e503-110">The latest version of .NET available in the default package repositories for Fedora is .NET Core 3.1.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="supported-distributions"></a><span data-ttu-id="9e503-111">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="9e503-111">Supported distributions</span></span>

<span data-ttu-id="9e503-112">В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET и версий Fedora, в которых они поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="9e503-112">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="9e503-113">Эти версии поддерживаются до того же времени, что и версия [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или [Fedora](https://fedoraproject.org/wiki/End_of_life).</span><span class="sxs-lookup"><span data-stu-id="9e503-113">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="9e503-114">Значок ✔️ означает, что версия Fedora или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="9e503-114">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="9e503-115">Значок ❌ означает, что версия Fedora или версия .NET в таком выпуске Fedora не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="9e503-115">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="9e503-116">Если значок ✔️ стоит как напротив версии Fedora, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="9e503-116">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="9e503-117">Версия .NET</span><span class="sxs-lookup"><span data-stu-id="9e503-117">.NET Version</span></span>  | <span data-ttu-id="9e503-118">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-118">Fedora 33 ✔️</span></span> | <span data-ttu-id="9e503-119">32 ✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-119">32 ✔️</span></span> | <span data-ttu-id="9e503-120">31 ❌</span><span class="sxs-lookup"><span data-stu-id="9e503-120">31 ❌</span></span> | <span data-ttu-id="9e503-121">30 ❌</span><span class="sxs-lookup"><span data-stu-id="9e503-121">30 ❌</span></span> | <span data-ttu-id="9e503-122">29 ❌</span><span class="sxs-lookup"><span data-stu-id="9e503-122">29 ❌</span></span> | <span data-ttu-id="9e503-123">28 ❌</span><span class="sxs-lookup"><span data-stu-id="9e503-123">28 ❌</span></span> | <span data-ttu-id="9e503-124">27 ❌</span><span class="sxs-lookup"><span data-stu-id="9e503-124">27 ❌</span></span> |
| ------------  | ---------: | --: | --: | --: | --: | --: | --: |
| <span data-ttu-id="9e503-125">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="9e503-125">.NET 5.0</span></span>      | <span data-ttu-id="9e503-126">✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-126">✔️</span></span>        | <span data-ttu-id="9e503-127">✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-127">✔️</span></span> | ❌|❌ |❌ |❌  |❌ |
| <span data-ttu-id="9e503-128">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="9e503-128">.NET Core 3.1</span></span> | <span data-ttu-id="9e503-129">✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-129">✔️</span></span>        | <span data-ttu-id="9e503-130">✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-130">✔️</span></span> | <span data-ttu-id="9e503-131">✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-131">✔️</span></span>|<span data-ttu-id="9e503-132">✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-132">✔️</span></span> |<span data-ttu-id="9e503-133">✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-133">✔️</span></span> |❌  |❌ |
| <span data-ttu-id="9e503-134">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9e503-134">.NET Core 2.1</span></span> | <span data-ttu-id="9e503-135">✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-135">✔️</span></span>        | <span data-ttu-id="9e503-136">✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-136">✔️</span></span> | <span data-ttu-id="9e503-137">✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-137">✔️</span></span>|<span data-ttu-id="9e503-138">✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-138">✔️</span></span> |<span data-ttu-id="9e503-139">✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-139">✔️</span></span> |<span data-ttu-id="9e503-140">✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-140">✔️</span></span>  |<span data-ttu-id="9e503-141">✔️</span><span class="sxs-lookup"><span data-stu-id="9e503-141">✔️</span></span> |

<span data-ttu-id="9e503-142">Следующие версии .NET больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="9e503-142">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="9e503-143">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="9e503-143">The downloads for these still remain published:</span></span>

- <span data-ttu-id="9e503-144">3.0</span><span class="sxs-lookup"><span data-stu-id="9e503-144">3.0</span></span>
- <span data-ttu-id="9e503-145">2.2</span><span class="sxs-lookup"><span data-stu-id="9e503-145">2.2</span></span>
- <span data-ttu-id="9e503-146">2.0</span><span class="sxs-lookup"><span data-stu-id="9e503-146">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="9e503-147">Удалите предварительные версии</span><span class="sxs-lookup"><span data-stu-id="9e503-147">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="dependencies"></a><span data-ttu-id="9e503-148">Зависимости</span><span class="sxs-lookup"><span data-stu-id="9e503-148">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="install-on-older-distributions"></a><span data-ttu-id="9e503-149">Установка в других дистрибутивах</span><span class="sxs-lookup"><span data-stu-id="9e503-149">Install on older distributions</span></span>

<span data-ttu-id="9e503-150">В репозиториях пакетов по умолчанию для более старых версий Fedora отсутствует .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9e503-150">Older versions of Fedora don't contain .NET Core in the default package repositories.</span></span> <span data-ttu-id="9e503-151">Вы можете установить .NET с помощью пакета [snap](linux-snap.md), [скрипта _dotnet-install.sh_](linux-scripted-manual.md#scripted-install)или репозитория Майкрософт:</span><span class="sxs-lookup"><span data-stu-id="9e503-151">You can install .NET with [snap](linux-snap.md), through the [_dotnet-install.sh_ script](linux-scripted-manual.md#scripted-install), or use Microsoft's repository to install .NET:</span></span>

01. <span data-ttu-id="9e503-152">Сначала необходимо добавить ключ подписывания пакета Майкрософт в список доверенных ключей.</span><span class="sxs-lookup"><span data-stu-id="9e503-152">First, add the Microsoft signing key to your list of trusted keys.</span></span>

    ```bash
    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    ```

02. <span data-ttu-id="9e503-153">Далее добавьте репозиторий пакетов Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="9e503-153">Next, add the Microsoft package repository.</span></span> <span data-ttu-id="9e503-154">Источник репозитория зависит от вашей версии Fedora.</span><span class="sxs-lookup"><span data-stu-id="9e503-154">The source of the repository is based on your version of Fedora.</span></span>

    | <span data-ttu-id="9e503-155">Версия Fedora</span><span class="sxs-lookup"><span data-stu-id="9e503-155">Fedora Version</span></span> | <span data-ttu-id="9e503-156">Репозиторий пакетов</span><span class="sxs-lookup"><span data-stu-id="9e503-156">Package repository</span></span> |
    | -------------- | ------- |
    | <span data-ttu-id="9e503-157">31</span><span class="sxs-lookup"><span data-stu-id="9e503-157">31</span></span>             | `https://packages.microsoft.com/config/fedora/31/prod.repo` |
    | <span data-ttu-id="9e503-158">30</span><span class="sxs-lookup"><span data-stu-id="9e503-158">30</span></span>             | `https://packages.microsoft.com/config/fedora/30/prod.repo` |
    | <span data-ttu-id="9e503-159">29</span><span class="sxs-lookup"><span data-stu-id="9e503-159">29</span></span>             | `https://packages.microsoft.com/config/fedora/29/prod.repo` |
    | <span data-ttu-id="9e503-160">28</span><span class="sxs-lookup"><span data-stu-id="9e503-160">28</span></span>             | `https://packages.microsoft.com/config/fedora/28/prod.repo` |
    | <span data-ttu-id="9e503-161">27</span><span class="sxs-lookup"><span data-stu-id="9e503-161">27</span></span>             | `https://packages.microsoft.com/config/fedora/27/prod.repo` |

    ```bash
    sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
    ```

[!INCLUDE [linux-dnf-install-31](./includes/linux-install-31-dnf.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="9e503-162">Установка других версий</span><span class="sxs-lookup"><span data-stu-id="9e503-162">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="9e503-163">Устранение неполадок диспетчера пакетов</span><span class="sxs-lookup"><span data-stu-id="9e503-163">Troubleshoot the package manager</span></span>

<span data-ttu-id="9e503-164">В этом разделе описаны распространенные ошибки, которые могут возникнуть при использовании диспетчера пакетов для установки .NET или .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9e503-164">This section provides information on common errors you may get while using the package manager to install .NET or .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="9e503-165">Не удалось найти пакет</span><span class="sxs-lookup"><span data-stu-id="9e503-165">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="9e503-166">Ошибка получения</span><span class="sxs-lookup"><span data-stu-id="9e503-166">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="next-steps"></a><span data-ttu-id="9e503-167">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="9e503-167">Next steps</span></span>

- [<span data-ttu-id="9e503-168">Включение заполнения клавишей TAB для .NET CLI</span><span class="sxs-lookup"><span data-stu-id="9e503-168">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="9e503-169">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9e503-169">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
