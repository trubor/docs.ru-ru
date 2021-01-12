---
title: Установка .NET в SLES — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в SLES.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 80da69616dd1507b809ef56d439645d569a6a805
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970789"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-sles"></a><span data-ttu-id="3a2d6-103">Установка пакета SDK для .NET или среды выполнения .NET в SLES</span><span class="sxs-lookup"><span data-stu-id="3a2d6-103">Install the .NET SDK or the .NET Runtime on SLES</span></span>

<span data-ttu-id="3a2d6-104">.NET поддерживается в SLES.</span><span class="sxs-lookup"><span data-stu-id="3a2d6-104">.NET is supported on SLES.</span></span> <span data-ttu-id="3a2d6-105">В этой статье описано, как установить .NET в SLES.</span><span class="sxs-lookup"><span data-stu-id="3a2d6-105">This article describes how to install .NET on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="3a2d6-106">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="3a2d6-106">Supported distributions</span></span>

<span data-ttu-id="3a2d6-107">В следующей таблице приведен список выпусков .NET, которые сейчас поддерживаются в SLES 12 SP2 и SLES 15.</span><span class="sxs-lookup"><span data-stu-id="3a2d6-107">The following table is a list of currently supported .NET releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="3a2d6-108">Эти версии поддерживаются до тех пор, пока для версии [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) или версии SLES не будет прекращена поддержка.</span><span class="sxs-lookup"><span data-stu-id="3a2d6-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="3a2d6-109">Значок ✔️ означает, что версия SLES или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="3a2d6-109">A ✔️ indicates that the version of SLES or .NET is still supported.</span></span>
- <span data-ttu-id="3a2d6-110">Значок ❌ означает, что версия SLES или версия .NET в таком выпуске SLES не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="3a2d6-110">A ❌ indicates that the version of SLES or .NET isn't supported on that SLES release.</span></span>
- <span data-ttu-id="3a2d6-111">Если значок ✔️ стоит как напротив версии SLES, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="3a2d6-111">When both a version of SLES and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="3a2d6-112">SLES</span><span class="sxs-lookup"><span data-stu-id="3a2d6-112">SLES</span></span>                   | <span data-ttu-id="3a2d6-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3a2d6-113">.NET Core 2.1</span></span> | <span data-ttu-id="3a2d6-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="3a2d6-114">.NET Core 3.1</span></span> | <span data-ttu-id="3a2d6-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="3a2d6-115">.NET 5.0</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="3a2d6-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="3a2d6-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="3a2d6-117">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="3a2d6-117">✔️ 2.1</span></span>        | <span data-ttu-id="3a2d6-118">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="3a2d6-118">✔️ 3.1</span></span>        | <span data-ttu-id="3a2d6-119">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="3a2d6-119">✔️ 5.0</span></span> |
| <span data-ttu-id="3a2d6-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="3a2d6-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="3a2d6-121">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="3a2d6-121">✔️ 2.1</span></span>        | <span data-ttu-id="3a2d6-122">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="3a2d6-122">✔️ 3.1</span></span>        | <span data-ttu-id="3a2d6-123">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="3a2d6-123">✔️ 5.0</span></span> |

<span data-ttu-id="3a2d6-124">Следующие версии .NET Core больше не поддерживаются</span><span class="sxs-lookup"><span data-stu-id="3a2d6-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="3a2d6-125">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="3a2d6-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="3a2d6-126">3.0</span><span class="sxs-lookup"><span data-stu-id="3a2d6-126">3.0</span></span>
- <span data-ttu-id="3a2d6-127">2.2</span><span class="sxs-lookup"><span data-stu-id="3a2d6-127">2.2</span></span>
- <span data-ttu-id="3a2d6-128">2.0</span><span class="sxs-lookup"><span data-stu-id="3a2d6-128">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="3a2d6-129">Удалите предварительные версии</span><span class="sxs-lookup"><span data-stu-id="3a2d6-129">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="sles-15-"></a><span data-ttu-id="3a2d6-130">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="3a2d6-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="3a2d6-131">В настоящее время пакет установки репозитория Microsoft SLES 15 устанавливает файл *microsoft-prod.repo* в неправильный каталог, мешая поиску пакетов .NET в zypper.</span><span class="sxs-lookup"><span data-stu-id="3a2d6-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET packages.</span></span> <span data-ttu-id="3a2d6-132">Чтобы устранить эту проблему, создайте символьную ссылку в правильном каталоге.</span><span class="sxs-lookup"><span data-stu-id="3a2d6-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="3a2d6-133">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="3a2d6-133">SLES 12 ✔️</span></span>

<span data-ttu-id="3a2d6-134">.NET требуется как минимум семейство SLES 12 с пакетом обновления 2 (SP2).</span><span class="sxs-lookup"><span data-stu-id="3a2d6-134">.NET requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="3a2d6-135">Установка других версий</span><span class="sxs-lookup"><span data-stu-id="3a2d6-135">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="3a2d6-136">Устранение неполадок диспетчера пакетов</span><span class="sxs-lookup"><span data-stu-id="3a2d6-136">Troubleshoot the package manager</span></span>

<span data-ttu-id="3a2d6-137">В этом разделе описаны распространенные ошибки, которые могут возникнуть при использовании диспетчера пакетов для установки .NET.</span><span class="sxs-lookup"><span data-stu-id="3a2d6-137">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="3a2d6-138">Ошибка получения</span><span class="sxs-lookup"><span data-stu-id="3a2d6-138">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="3a2d6-139">Зависимости</span><span class="sxs-lookup"><span data-stu-id="3a2d6-139">Dependencies</span></span>

<span data-ttu-id="3a2d6-140">Если для установки используется диспетчер пакетов, эти библиотеки устанавливаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="3a2d6-140">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="3a2d6-141">Но если вы устанавливаете .NET вручную или публикуете автономное приложение, вам потребуется установить эти библиотеки:</span><span class="sxs-lookup"><span data-stu-id="3a2d6-141">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="3a2d6-142">krb5</span><span class="sxs-lookup"><span data-stu-id="3a2d6-142">krb5</span></span>
- <span data-ttu-id="3a2d6-143">libicu</span><span class="sxs-lookup"><span data-stu-id="3a2d6-143">libicu</span></span>
- <span data-ttu-id="3a2d6-144">libopenssl1_1</span><span class="sxs-lookup"><span data-stu-id="3a2d6-144">libopenssl1_1</span></span>

<span data-ttu-id="3a2d6-145">Если в целевой среде выполнения установлена версия OpenSSL 1.1 или более поздняя, необходимо установить **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="3a2d6-145">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="3a2d6-146">Дополнительные сведения о зависимостях см. в статье об [автономных приложениях Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="3a2d6-146">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="3a2d6-147">Для приложений .NET, использующих сборку *System.Drawing.Common*, необходима также следующая зависимость:</span><span class="sxs-lookup"><span data-stu-id="3a2d6-147">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="3a2d6-148">libgdiplus (версии 6.0.1 или выше)</span><span class="sxs-lookup"><span data-stu-id="3a2d6-148">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="3a2d6-149">Вы можете установить последнюю версию *libgdiplus*, добавив в систему репозиторий Mono.</span><span class="sxs-lookup"><span data-stu-id="3a2d6-149">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="3a2d6-150">Для получения дополнительной информации см. <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="3a2d6-150">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3a2d6-151">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="3a2d6-151">Next steps</span></span>

- [<span data-ttu-id="3a2d6-152">Включение заполнения клавишей TAB для .NET CLI</span><span class="sxs-lookup"><span data-stu-id="3a2d6-152">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="3a2d6-153">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3a2d6-153">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
