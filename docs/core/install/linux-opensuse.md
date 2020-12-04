---
title: Установка .NET в openSUSE — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: eb31e3109ccd40999c22a27607d48544bf117dc2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031869"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-opensuse"></a><span data-ttu-id="c1331-103">Установка пакета SDK для .NET или среды выполнения .NET в openSUSE</span><span class="sxs-lookup"><span data-stu-id="c1331-103">Install the .NET SDK or the .NET Runtime on openSUSE</span></span>

<span data-ttu-id="c1331-104">.NET поддерживается в openSUSE.</span><span class="sxs-lookup"><span data-stu-id="c1331-104">.NET is supported on openSUSE.</span></span> <span data-ttu-id="c1331-105">В этой статье описано, как установить .NET в openSUSE.</span><span class="sxs-lookup"><span data-stu-id="c1331-105">This article describes how to install .NET on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="c1331-106">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="c1331-106">Supported distributions</span></span>

<span data-ttu-id="c1331-107">В следующей таблице приведен список выпусков .NET, которые сейчас поддерживаются в openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="c1331-107">The following table is a list of currently supported .NET releases on openSUSE 15.</span></span> <span data-ttu-id="c1331-108">Эти версии поддерживаются до тех пор, пока для версии [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или версии openSUSE не будет прекращена поддержка.</span><span class="sxs-lookup"><span data-stu-id="c1331-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="c1331-109">Значок ✔️ означает, что версия openSUSE или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c1331-109">A ✔️ indicates that the version of openSUSE or .NET is still supported.</span></span>
- <span data-ttu-id="c1331-110">Значок ❌ означает, что версия openSUSE или версия .NET в таком выпуске openSUSE не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c1331-110">A ❌ indicates that the version of openSUSE or .NET isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="c1331-111">Если значок ✔️ стоит как напротив версии openSUSE, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="c1331-111">When both a version of openSUSE and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="c1331-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="c1331-112">openSUSE</span></span>                   | <span data-ttu-id="c1331-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c1331-113">.NET Core 2.1</span></span> | <span data-ttu-id="c1331-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c1331-114">.NET Core 3.1</span></span> | <span data-ttu-id="c1331-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="c1331-115">.NET 5.0</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="c1331-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="c1331-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="c1331-117">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="c1331-117">✔️ 2.1</span></span>        | <span data-ttu-id="c1331-118">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="c1331-118">✔️ 3.1</span></span>        | <span data-ttu-id="c1331-119">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="c1331-119">✔️ 5.0</span></span> |

<span data-ttu-id="c1331-120">Следующие версии .NET больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="c1331-120">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="c1331-121">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="c1331-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="c1331-122">3.0</span><span class="sxs-lookup"><span data-stu-id="c1331-122">3.0</span></span>
- <span data-ttu-id="c1331-123">2.2</span><span class="sxs-lookup"><span data-stu-id="c1331-123">2.2</span></span>
- <span data-ttu-id="c1331-124">2.0</span><span class="sxs-lookup"><span data-stu-id="c1331-124">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="c1331-125">Удалите предварительные версии</span><span class="sxs-lookup"><span data-stu-id="c1331-125">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="c1331-126">Установка других версий</span><span class="sxs-lookup"><span data-stu-id="c1331-126">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="c1331-127">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="c1331-127">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="c1331-128">Устранение неполадок диспетчера пакетов</span><span class="sxs-lookup"><span data-stu-id="c1331-128">Troubleshoot the package manager</span></span>

<span data-ttu-id="c1331-129">В этом разделе описаны распространенные ошибки, которые могут возникнуть при использовании диспетчера пакетов для установки .NET.</span><span class="sxs-lookup"><span data-stu-id="c1331-129">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="c1331-130">Не удалось найти пакет</span><span class="sxs-lookup"><span data-stu-id="c1331-130">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="c1331-131">Ошибка получения</span><span class="sxs-lookup"><span data-stu-id="c1331-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="c1331-132">Snap-пакеты</span><span class="sxs-lookup"><span data-stu-id="c1331-132">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="c1331-133">Зависимости</span><span class="sxs-lookup"><span data-stu-id="c1331-133">Dependencies</span></span>

<span data-ttu-id="c1331-134">Если для установки используется диспетчер пакетов, эти библиотеки устанавливаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="c1331-134">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="c1331-135">Но если вы устанавливаете .NET вручную или публикуете автономное приложение, вам потребуется установить эти библиотеки:</span><span class="sxs-lookup"><span data-stu-id="c1331-135">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="c1331-136">krb5</span><span class="sxs-lookup"><span data-stu-id="c1331-136">krb5</span></span>
- <span data-ttu-id="c1331-137">libicu</span><span class="sxs-lookup"><span data-stu-id="c1331-137">libicu</span></span>
- <span data-ttu-id="c1331-138">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="c1331-138">libopenssl1_0_0</span></span>

<span data-ttu-id="c1331-139">Если в целевой среде выполнения установлена версия OpenSSL 1.1 или более поздняя, необходимо установить **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="c1331-139">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="c1331-140">Дополнительные сведения о зависимостях см. в статье об [автономных приложениях Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="c1331-140">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="c1331-141">Для приложений .NET, использующих сборку *System.Drawing.Common*, необходима также следующая зависимость:</span><span class="sxs-lookup"><span data-stu-id="c1331-141">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="c1331-142">libgdiplus (версии 6.0.1 или выше)</span><span class="sxs-lookup"><span data-stu-id="c1331-142">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="c1331-143">Вы можете установить последнюю версию *libgdiplus*, добавив в систему репозиторий Mono.</span><span class="sxs-lookup"><span data-stu-id="c1331-143">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="c1331-144">Для получения дополнительной информации см. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="c1331-144">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="c1331-145">Установка с помощью скрипта</span><span class="sxs-lookup"><span data-stu-id="c1331-145">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="c1331-146">Установка вручную</span><span class="sxs-lookup"><span data-stu-id="c1331-146">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="c1331-147">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="c1331-147">Next steps</span></span>

- [<span data-ttu-id="c1331-148">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c1331-148">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
