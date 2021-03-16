---
title: Установка .NET в Fedora — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в Fedora.
author: adegeo
ms.author: adegeo
ms.date: 02/17/2021
ms.openlocfilehash: efaad4788db2200b1a47f9b4ae2414730588c6ae
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102255765"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="c65a2-103">Установка пакета SDK для .NET или среды выполнения .NET в Fedora</span><span class="sxs-lookup"><span data-stu-id="c65a2-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="c65a2-104">Платформа .NET поддерживается в Fedora. В этой статье описано, как установить .NET в Fedora.</span><span class="sxs-lookup"><span data-stu-id="c65a2-104">.NET is supported on Fedora and this article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="c65a2-105">Если поддержка какой-либо версии Fedora прекращается, то .NET также перестает поддерживать ее.</span><span class="sxs-lookup"><span data-stu-id="c65a2-105">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="c65a2-106">Дополнительные сведения об установке .NET без использования диспетчера пакетов см. в одной из следующих статей:</span><span class="sxs-lookup"><span data-stu-id="c65a2-106">For more information on installing .NET without a package manager, see one of the following articles:</span></span>

- [<span data-ttu-id="c65a2-107">Установка пакета SDK для .NET или среды выполнения .NET с использованием пакета Snap.</span><span class="sxs-lookup"><span data-stu-id="c65a2-107">Install the .NET SDK or the .NET Runtime with Snap.</span></span>](linux-snap.md)
- [<span data-ttu-id="c65a2-108">Установка пакета SDK для .NET или среды выполнения .NET с использованием скрипта.</span><span class="sxs-lookup"><span data-stu-id="c65a2-108">Install the .NET SDK or the .NET Runtime with a script.</span></span>](linux-scripted-manual.md#scripted-install)
- [<span data-ttu-id="c65a2-109">Установка пакета SDK для .NET или среды выполнения .NET вручную.</span><span class="sxs-lookup"><span data-stu-id="c65a2-109">Install the .NET SDK or the .NET Runtime manually.</span></span>](linux-scripted-manual.md#manual-install)

## <a name="install-net-50"></a><span data-ttu-id="c65a2-110">Установка .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="c65a2-110">Install .NET 5.0</span></span>

<span data-ttu-id="c65a2-111">Последней версией .NET, которая представлена в репозиториях пакетов по умолчанию для Fedora 33, является .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="c65a2-111">The latest version of .NET available in the default package repositories for Fedora is .NET 5.0.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="install-net-core-31"></a><span data-ttu-id="c65a2-112">Установка .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c65a2-112">Install .NET Core 3.1</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="supported-distributions"></a><span data-ttu-id="c65a2-113">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="c65a2-113">Supported distributions</span></span>

<span data-ttu-id="c65a2-114">В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET и версий Fedora, в которых они поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="c65a2-114">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="c65a2-115">Эти версии поддерживаются до того же времени, что и версия [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или [Fedora](https://fedoraproject.org/wiki/End_of_life).</span><span class="sxs-lookup"><span data-stu-id="c65a2-115">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="c65a2-116">Значок ✔️ означает, что версия Fedora или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c65a2-116">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="c65a2-117">Значок ❌ означает, что версия Fedora или версия .NET в таком выпуске Fedora не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c65a2-117">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="c65a2-118">Если значок ✔️ стоит как напротив версии Fedora, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c65a2-118">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="c65a2-119">Версия .NET</span><span class="sxs-lookup"><span data-stu-id="c65a2-119">.NET Version</span></span>  | <span data-ttu-id="c65a2-120">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-120">Fedora 33 ✔️</span></span> | <span data-ttu-id="c65a2-121">32 ✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-121">32 ✔️</span></span> | <span data-ttu-id="c65a2-122">31 ❌</span><span class="sxs-lookup"><span data-stu-id="c65a2-122">31 ❌</span></span> | <span data-ttu-id="c65a2-123">30 ❌</span><span class="sxs-lookup"><span data-stu-id="c65a2-123">30 ❌</span></span> | <span data-ttu-id="c65a2-124">29 ❌</span><span class="sxs-lookup"><span data-stu-id="c65a2-124">29 ❌</span></span> | <span data-ttu-id="c65a2-125">28 ❌</span><span class="sxs-lookup"><span data-stu-id="c65a2-125">28 ❌</span></span> | <span data-ttu-id="c65a2-126">27 ❌</span><span class="sxs-lookup"><span data-stu-id="c65a2-126">27 ❌</span></span> |
| ------------  | ---------: | --: | --: | --: | --: | --: | --: |
| <span data-ttu-id="c65a2-127">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="c65a2-127">.NET 5.0</span></span>      | <span data-ttu-id="c65a2-128">✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-128">✔️</span></span>        | <span data-ttu-id="c65a2-129">✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-129">✔️</span></span> | ❌|❌ |❌ |❌  |❌ |
| <span data-ttu-id="c65a2-130">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c65a2-130">.NET Core 3.1</span></span> | <span data-ttu-id="c65a2-131">✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-131">✔️</span></span>        | <span data-ttu-id="c65a2-132">✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-132">✔️</span></span> | <span data-ttu-id="c65a2-133">✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-133">✔️</span></span>|<span data-ttu-id="c65a2-134">✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-134">✔️</span></span> |<span data-ttu-id="c65a2-135">✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-135">✔️</span></span> |❌  |❌ |
| <span data-ttu-id="c65a2-136">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c65a2-136">.NET Core 2.1</span></span> | <span data-ttu-id="c65a2-137">✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-137">✔️</span></span>        | <span data-ttu-id="c65a2-138">✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-138">✔️</span></span> | <span data-ttu-id="c65a2-139">✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-139">✔️</span></span>|<span data-ttu-id="c65a2-140">✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-140">✔️</span></span> |<span data-ttu-id="c65a2-141">✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-141">✔️</span></span> |<span data-ttu-id="c65a2-142">✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-142">✔️</span></span>  |<span data-ttu-id="c65a2-143">✔️</span><span class="sxs-lookup"><span data-stu-id="c65a2-143">✔️</span></span> |

<span data-ttu-id="c65a2-144">Следующие версии .NET больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="c65a2-144">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="c65a2-145">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="c65a2-145">The downloads for these still remain published:</span></span>

- <span data-ttu-id="c65a2-146">3.0</span><span class="sxs-lookup"><span data-stu-id="c65a2-146">3.0</span></span>
- <span data-ttu-id="c65a2-147">2.2</span><span class="sxs-lookup"><span data-stu-id="c65a2-147">2.2</span></span>
- <span data-ttu-id="c65a2-148">2.0</span><span class="sxs-lookup"><span data-stu-id="c65a2-148">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="c65a2-149">Удалите предварительные версии</span><span class="sxs-lookup"><span data-stu-id="c65a2-149">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="dependencies"></a><span data-ttu-id="c65a2-150">Зависимости</span><span class="sxs-lookup"><span data-stu-id="c65a2-150">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="install-on-older-distributions"></a><span data-ttu-id="c65a2-151">Установка в других дистрибутивах</span><span class="sxs-lookup"><span data-stu-id="c65a2-151">Install on older distributions</span></span>

<span data-ttu-id="c65a2-152">В репозиториях пакетов по умолчанию для более старых версий Fedora отсутствует .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c65a2-152">Older versions of Fedora don't contain .NET Core in the default package repositories.</span></span> <span data-ttu-id="c65a2-153">Вы можете установить .NET с помощью пакета [snap](linux-snap.md), [скрипта _dotnet-install.sh_](linux-scripted-manual.md#scripted-install)или репозитория Майкрософт:</span><span class="sxs-lookup"><span data-stu-id="c65a2-153">You can install .NET with [snap](linux-snap.md), through the [_dotnet-install.sh_ script](linux-scripted-manual.md#scripted-install), or use Microsoft's repository to install .NET:</span></span>

01. <span data-ttu-id="c65a2-154">Сначала необходимо добавить ключ подписывания пакета Майкрософт в список доверенных ключей.</span><span class="sxs-lookup"><span data-stu-id="c65a2-154">First, add the Microsoft signing key to your list of trusted keys.</span></span>

    ```bash
    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    ```

02. <span data-ttu-id="c65a2-155">Далее добавьте репозиторий пакетов Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="c65a2-155">Next, add the Microsoft package repository.</span></span> <span data-ttu-id="c65a2-156">Источник репозитория зависит от вашей версии Fedora.</span><span class="sxs-lookup"><span data-stu-id="c65a2-156">The source of the repository is based on your version of Fedora.</span></span>

    | <span data-ttu-id="c65a2-157">Версия Fedora</span><span class="sxs-lookup"><span data-stu-id="c65a2-157">Fedora Version</span></span> | <span data-ttu-id="c65a2-158">Репозиторий пакетов</span><span class="sxs-lookup"><span data-stu-id="c65a2-158">Package repository</span></span> |
    | -------------- | ------- |
    | <span data-ttu-id="c65a2-159">31</span><span class="sxs-lookup"><span data-stu-id="c65a2-159">31</span></span>             | `https://packages.microsoft.com/config/fedora/31/prod.repo` |
    | <span data-ttu-id="c65a2-160">30</span><span class="sxs-lookup"><span data-stu-id="c65a2-160">30</span></span>             | `https://packages.microsoft.com/config/fedora/30/prod.repo` |
    | <span data-ttu-id="c65a2-161">29</span><span class="sxs-lookup"><span data-stu-id="c65a2-161">29</span></span>             | `https://packages.microsoft.com/config/fedora/29/prod.repo` |
    | <span data-ttu-id="c65a2-162">28</span><span class="sxs-lookup"><span data-stu-id="c65a2-162">28</span></span>             | `https://packages.microsoft.com/config/fedora/28/prod.repo` |
    | <span data-ttu-id="c65a2-163">27</span><span class="sxs-lookup"><span data-stu-id="c65a2-163">27</span></span>             | `https://packages.microsoft.com/config/fedora/27/prod.repo` |

    ```bash
    sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
    ```

[!INCLUDE [linux-dnf-install-31](./includes/linux-install-31-dnf.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="c65a2-164">Установка других версий</span><span class="sxs-lookup"><span data-stu-id="c65a2-164">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="c65a2-165">Устранение неполадок диспетчера пакетов</span><span class="sxs-lookup"><span data-stu-id="c65a2-165">Troubleshoot the package manager</span></span>

<span data-ttu-id="c65a2-166">В этом разделе описаны распространенные ошибки, которые могут возникнуть при использовании диспетчера пакетов для установки .NET или .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c65a2-166">This section provides information on common errors you may get while using the package manager to install .NET or .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="c65a2-167">Не удалось найти пакет</span><span class="sxs-lookup"><span data-stu-id="c65a2-167">Unable to find package</span></span>

<span data-ttu-id="c65a2-168">Дополнительные сведения об установке .NET без использования диспетчера пакетов см. в одной из следующих статей:</span><span class="sxs-lookup"><span data-stu-id="c65a2-168">For more information on installing .NET without a package manager, see one of the following articles:</span></span>

- [<span data-ttu-id="c65a2-169">Установка пакета SDK для .NET или среды выполнения .NET с использованием пакета Snap.</span><span class="sxs-lookup"><span data-stu-id="c65a2-169">Install the .NET SDK or the .NET Runtime with Snap.</span></span>](linux-snap.md)
- [<span data-ttu-id="c65a2-170">Установка пакета SDK для .NET или среды выполнения .NET с использованием скрипта.</span><span class="sxs-lookup"><span data-stu-id="c65a2-170">Install the .NET SDK or the .NET Runtime with a script.</span></span>](linux-scripted-manual.md#scripted-install)
- [<span data-ttu-id="c65a2-171">Установка пакета SDK для .NET или среды выполнения .NET вручную.</span><span class="sxs-lookup"><span data-stu-id="c65a2-171">Install the .NET SDK or the .NET Runtime manually.</span></span>](linux-scripted-manual.md#manual-install)

### <a name="failed-to-fetch"></a><span data-ttu-id="c65a2-172">Ошибка получения</span><span class="sxs-lookup"><span data-stu-id="c65a2-172">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="next-steps"></a><span data-ttu-id="c65a2-173">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="c65a2-173">Next steps</span></span>

- [<span data-ttu-id="c65a2-174">Включение заполнения клавишей TAB для .NET CLI</span><span class="sxs-lookup"><span data-stu-id="c65a2-174">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="c65a2-175">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c65a2-175">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
