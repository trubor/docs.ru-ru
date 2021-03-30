---
title: Установка .NET в openSUSE — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: d238054a217a7295594db856d5497982572af377
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873956"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-opensuse"></a><span data-ttu-id="2c34d-103">Установка пакета SDK для .NET или среды выполнения .NET в openSUSE</span><span class="sxs-lookup"><span data-stu-id="2c34d-103">Install the .NET SDK or the .NET Runtime on openSUSE</span></span>

<span data-ttu-id="2c34d-104">.NET поддерживается в openSUSE.</span><span class="sxs-lookup"><span data-stu-id="2c34d-104">.NET is supported on openSUSE.</span></span> <span data-ttu-id="2c34d-105">В этой статье описано, как установить .NET в openSUSE.</span><span class="sxs-lookup"><span data-stu-id="2c34d-105">This article describes how to install .NET on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="2c34d-106">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="2c34d-106">Supported distributions</span></span>

<span data-ttu-id="2c34d-107">В следующей таблице приведен список выпусков .NET, которые сейчас поддерживаются в openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="2c34d-107">The following table is a list of currently supported .NET releases on openSUSE 15.</span></span> <span data-ttu-id="2c34d-108">Эти версии поддерживаются до тех пор, пока для версии [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или версии openSUSE не будет прекращена поддержка.</span><span class="sxs-lookup"><span data-stu-id="2c34d-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="2c34d-109">Значок ✔️ означает, что версия openSUSE или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="2c34d-109">A ✔️ indicates that the version of openSUSE or .NET is still supported.</span></span>
- <span data-ttu-id="2c34d-110">Значок ❌ означает, что версия openSUSE или версия .NET в таком выпуске openSUSE не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="2c34d-110">A ❌ indicates that the version of openSUSE or .NET isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="2c34d-111">Если значок ✔️ стоит как напротив версии openSUSE, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="2c34d-111">When both a version of openSUSE and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="2c34d-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="2c34d-112">openSUSE</span></span>                   | <span data-ttu-id="2c34d-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2c34d-113">.NET Core 2.1</span></span> | <span data-ttu-id="2c34d-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="2c34d-114">.NET Core 3.1</span></span> | <span data-ttu-id="2c34d-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="2c34d-115">.NET 5.0</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="2c34d-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="2c34d-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="2c34d-117">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="2c34d-117">✔️ 2.1</span></span>        | <span data-ttu-id="2c34d-118">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="2c34d-118">✔️ 3.1</span></span>        | <span data-ttu-id="2c34d-119">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="2c34d-119">✔️ 5.0</span></span> |

<span data-ttu-id="2c34d-120">Следующие версии .NET больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="2c34d-120">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="2c34d-121">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="2c34d-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="2c34d-122">3.0</span><span class="sxs-lookup"><span data-stu-id="2c34d-122">3.0</span></span>
- <span data-ttu-id="2c34d-123">2.2</span><span class="sxs-lookup"><span data-stu-id="2c34d-123">2.2</span></span>
- <span data-ttu-id="2c34d-124">2.0</span><span class="sxs-lookup"><span data-stu-id="2c34d-124">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="2c34d-125">Удалите предварительные версии</span><span class="sxs-lookup"><span data-stu-id="2c34d-125">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="2c34d-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="2c34d-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="2c34d-127">Установка других версий</span><span class="sxs-lookup"><span data-stu-id="2c34d-127">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="2c34d-128">Устранение неполадок диспетчера пакетов</span><span class="sxs-lookup"><span data-stu-id="2c34d-128">Troubleshoot the package manager</span></span>

<span data-ttu-id="2c34d-129">В этом разделе описаны распространенные ошибки, которые могут возникнуть при использовании диспетчера пакетов для установки .NET.</span><span class="sxs-lookup"><span data-stu-id="2c34d-129">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="2c34d-130">Не удалось найти пакет</span><span class="sxs-lookup"><span data-stu-id="2c34d-130">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="2c34d-131">Ошибка получения</span><span class="sxs-lookup"><span data-stu-id="2c34d-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="2c34d-132">Зависимости</span><span class="sxs-lookup"><span data-stu-id="2c34d-132">Dependencies</span></span>

<span data-ttu-id="2c34d-133">Если для установки используется диспетчер пакетов, эти библиотеки устанавливаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="2c34d-133">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="2c34d-134">Но если вы устанавливаете .NET вручную или публикуете автономное приложение, вам потребуется установить эти библиотеки:</span><span class="sxs-lookup"><span data-stu-id="2c34d-134">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="2c34d-135">krb5</span><span class="sxs-lookup"><span data-stu-id="2c34d-135">krb5</span></span>
- <span data-ttu-id="2c34d-136">libicu</span><span class="sxs-lookup"><span data-stu-id="2c34d-136">libicu</span></span>
- <span data-ttu-id="2c34d-137">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="2c34d-137">libopenssl1_0_0</span></span>

<span data-ttu-id="2c34d-138">Если в целевой среде выполнения установлена версия OpenSSL 1.1 или более поздняя, необходимо установить **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="2c34d-138">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="2c34d-139">Дополнительные сведения о зависимостях см. в статье об [автономных приложениях Linux](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="2c34d-139">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/main/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="2c34d-140">Для приложений .NET, использующих сборку *System.Drawing.Common*, необходима также следующая зависимость:</span><span class="sxs-lookup"><span data-stu-id="2c34d-140">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="2c34d-141">libgdiplus (версии 6.0.1 или выше)</span><span class="sxs-lookup"><span data-stu-id="2c34d-141">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="2c34d-142">Вы можете установить последнюю версию *libgdiplus*, добавив в систему репозиторий Mono.</span><span class="sxs-lookup"><span data-stu-id="2c34d-142">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="2c34d-143">Для получения дополнительной информации см. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="2c34d-143">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2c34d-144">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="2c34d-144">Next steps</span></span>

- [<span data-ttu-id="2c34d-145">Включение заполнения клавишей TAB для .NET CLI</span><span class="sxs-lookup"><span data-stu-id="2c34d-145">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="2c34d-146">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2c34d-146">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
