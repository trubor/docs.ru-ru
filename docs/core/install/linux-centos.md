---
title: Установка .NET в CentOS — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в CentOS.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: b30aa206057107aa17fcd62e0f042f9fe3ad56dc
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031934"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-centos"></a><span data-ttu-id="455f0-103">Установка пакета SDK для .NET или среды выполнения .NET в CentOS</span><span class="sxs-lookup"><span data-stu-id="455f0-103">Install the .NET SDK or the .NET Runtime on CentOS</span></span>

<span data-ttu-id="455f0-104">.NET поддерживается в CentOS.</span><span class="sxs-lookup"><span data-stu-id="455f0-104">.NET is supported on CentOS.</span></span> <span data-ttu-id="455f0-105">В этой статье описано, как установить .NET в CentOS.</span><span class="sxs-lookup"><span data-stu-id="455f0-105">This article describes how to install .NET on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="455f0-106">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="455f0-106">Supported distributions</span></span>

<span data-ttu-id="455f0-107">В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET в CentOS 7 и CentOS 8.</span><span class="sxs-lookup"><span data-stu-id="455f0-107">The following table is a list of currently supported .NET releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="455f0-108">Эти версии поддерживаются до того же времени, что и версия [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или CentOS.</span><span class="sxs-lookup"><span data-stu-id="455f0-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="455f0-109">Значок ✔️ означает, что версия CentOS или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="455f0-109">A ✔️ indicates that the version of CentOS or .NET is still supported.</span></span>
- <span data-ttu-id="455f0-110">Значок ❌ означает, что версия CentOS или версия .NET в таком выпуске CentOS не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="455f0-110">A ❌ indicates that the version of CentOS or .NET isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="455f0-111">Если значок ✔️ стоит как напротив версии CentOS, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="455f0-111">When both a version of CentOS and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="455f0-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="455f0-112">CentOS</span></span>                   | <span data-ttu-id="455f0-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="455f0-113">.NET Core 2.1</span></span> | <span data-ttu-id="455f0-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="455f0-114">.NET Core 3.1</span></span> | <span data-ttu-id="455f0-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="455f0-115">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="455f0-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="455f0-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="455f0-117">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="455f0-117">✔️ 2.1</span></span>        | <span data-ttu-id="455f0-118">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="455f0-118">✔️ 3.1</span></span>        | <span data-ttu-id="455f0-119">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="455f0-119">✔️ 5.0</span></span> |
| <span data-ttu-id="455f0-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="455f0-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="455f0-121">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="455f0-121">✔️ 2.1</span></span>        | <span data-ttu-id="455f0-122">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="455f0-122">✔️ 3.1</span></span>        | <span data-ttu-id="455f0-123">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="455f0-123">✔️ 5.0</span></span> |

<span data-ttu-id="455f0-124">Следующие версии .NET больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="455f0-124">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="455f0-125">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="455f0-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="455f0-126">3.0</span><span class="sxs-lookup"><span data-stu-id="455f0-126">3.0</span></span>
- <span data-ttu-id="455f0-127">2.2</span><span class="sxs-lookup"><span data-stu-id="455f0-127">2.2</span></span>
- <span data-ttu-id="455f0-128">2.0</span><span class="sxs-lookup"><span data-stu-id="455f0-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="remove-preview-versions"></a><span data-ttu-id="455f0-129">Удалите предварительные версии</span><span class="sxs-lookup"><span data-stu-id="455f0-129">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="455f0-130">Установка других версий</span><span class="sxs-lookup"><span data-stu-id="455f0-130">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="centos-8-"></a><span data-ttu-id="455f0-131">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="455f0-131">CentOS 8 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="455f0-132">.NET 5.0 пока недоступна в репозиториях в пакете по умолчанию, однако .NET Core 3.1 доступна.</span><span class="sxs-lookup"><span data-stu-id="455f0-132">.NET 5.0 isn't yet available in the default package repositories, but .NET Core 3.1 is.</span></span> <span data-ttu-id="455f0-133">Чтобы установить .NET Core 3.1, используйте команду `dnf install` с соответствующим пакетом, например `aspnetcore-runtime-3.1` или `dotnet-sdk-3.1`.</span><span class="sxs-lookup"><span data-stu-id="455f0-133">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="455f0-134">Следующие действия приведены для .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="455f0-134">The following instructions are for .NET 5.0.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/8/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="455f0-135">CentOS 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="455f0-135">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-50](includes/linux-install-50-yum.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="455f0-136">Устранение неполадок диспетчера пакетов</span><span class="sxs-lookup"><span data-stu-id="455f0-136">Troubleshoot the package manager</span></span>

<span data-ttu-id="455f0-137">В этом разделе описаны распространенные ошибки, которые могут возникнуть при использовании диспетчера пакетов для установки .NET.</span><span class="sxs-lookup"><span data-stu-id="455f0-137">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="455f0-138">Не удалось найти пакет</span><span class="sxs-lookup"><span data-stu-id="455f0-138">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="455f0-139">Ошибка получения</span><span class="sxs-lookup"><span data-stu-id="455f0-139">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="455f0-140">Snap-пакеты</span><span class="sxs-lookup"><span data-stu-id="455f0-140">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="455f0-141">Зависимости</span><span class="sxs-lookup"><span data-stu-id="455f0-141">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="455f0-142">Установка с помощью скрипта</span><span class="sxs-lookup"><span data-stu-id="455f0-142">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="455f0-143">Установка вручную</span><span class="sxs-lookup"><span data-stu-id="455f0-143">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="455f0-144">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="455f0-144">Next steps</span></span>

- [<span data-ttu-id="455f0-145">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="455f0-145">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
