---
title: Установка .NET в Alpine — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в Alpine.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: ece9a253cc11195c67e79c89747efe462a71632d
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873761"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a><span data-ttu-id="f65c6-103">Установка пакета SDK для .NET или среды выполнения .NET в Alpine</span><span class="sxs-lookup"><span data-stu-id="f65c6-103">Install the .NET SDK or the .NET Runtime on Alpine</span></span>

<span data-ttu-id="f65c6-104">В этой статье описано, как установить .NET в Alpine.</span><span class="sxs-lookup"><span data-stu-id="f65c6-104">This article describes how to install .NET on Alpine.</span></span> <span data-ttu-id="f65c6-105">Если поддержка какой-либо версии Alpine прекращается, то .NET также перестает поддерживать ее.</span><span class="sxs-lookup"><span data-stu-id="f65c6-105">When an Alpine version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="f65c6-106">Но с помощью этих инструкций вы сможете запустить .NET даже в неподдерживаемых версиях.</span><span class="sxs-lookup"><span data-stu-id="f65c6-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install"></a><span data-ttu-id="f65c6-107">Установить</span><span class="sxs-lookup"><span data-stu-id="f65c6-107">Install</span></span>

<span data-ttu-id="f65c6-108">Для Alpine Linux недоступны установщики.</span><span class="sxs-lookup"><span data-stu-id="f65c6-108">Installers aren't available for Alpine Linux.</span></span> <span data-ttu-id="f65c6-109">Устанавливать .NET необходимо одним из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="f65c6-109">You must install .NET in one of the following ways:</span></span>

- [<span data-ttu-id="f65c6-110">Пакет Snap</span><span class="sxs-lookup"><span data-stu-id="f65c6-110">Snap package</span></span>](linux-snap.md)
- [<span data-ttu-id="f65c6-111">Установка с помощью скрипта _install-dotnet.sh_</span><span class="sxs-lookup"><span data-stu-id="f65c6-111">Scripted install with _install-dotnet.sh_</span></span>](linux-scripted-manual.md#scripted-install)
- [<span data-ttu-id="f65c6-112">Ручное извлечение двоичных файлов</span><span class="sxs-lookup"><span data-stu-id="f65c6-112">Manual binary extraction</span></span>](linux-scripted-manual.md#manual-install)

## <a name="supported-distributions"></a><span data-ttu-id="f65c6-113">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="f65c6-113">Supported distributions</span></span>

<span data-ttu-id="f65c6-114">В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET и версий Alpine, в которых они поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="f65c6-114">The following table is a list of currently supported .NET releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="f65c6-115">Эти версии поддерживаются до окончания поддержки версии [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) либо до окончания жизненного цикла версии [Alpine](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span><span class="sxs-lookup"><span data-stu-id="f65c6-115">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="f65c6-116">Значок ✔️ означает, что версия Alpine или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="f65c6-116">A ✔️ indicates that the version of Alpine or .NET is still supported.</span></span>
- <span data-ttu-id="f65c6-117">Значок ❌ означает, что версия Alpine или версия .NET в таком выпуске Alpine не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="f65c6-117">A ❌ indicates that the version of Alpine or .NET isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="f65c6-118">Если значок ✔️ стоит как напротив версии Alpine, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="f65c6-118">When both a version of Alpine and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="f65c6-119">Alpine</span><span class="sxs-lookup"><span data-stu-id="f65c6-119">Alpine</span></span>  | <span data-ttu-id="f65c6-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f65c6-120">.NET Core 2.1</span></span> | <span data-ttu-id="f65c6-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="f65c6-121">.NET Core 3.1</span></span> | <span data-ttu-id="f65c6-122">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="f65c6-122">.NET 5.0</span></span> |
|-------- |---------------|---------------|----------------|
| <span data-ttu-id="f65c6-123">✔️ 3.13</span><span class="sxs-lookup"><span data-stu-id="f65c6-123">✔️ 3.13</span></span> | <span data-ttu-id="f65c6-124">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f65c6-124">✔️ 2.1</span></span>        | <span data-ttu-id="f65c6-125">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f65c6-125">✔️ 3.1</span></span>        | <span data-ttu-id="f65c6-126">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="f65c6-126">✔️ 5.0</span></span> |
| <span data-ttu-id="f65c6-127">✔️ 3.12</span><span class="sxs-lookup"><span data-stu-id="f65c6-127">✔️ 3.12</span></span> | <span data-ttu-id="f65c6-128">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f65c6-128">✔️ 2.1</span></span>        | <span data-ttu-id="f65c6-129">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f65c6-129">✔️ 3.1</span></span>        | <span data-ttu-id="f65c6-130">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="f65c6-130">✔️ 5.0</span></span> |
| <span data-ttu-id="f65c6-131">✔️ 3.11</span><span class="sxs-lookup"><span data-stu-id="f65c6-131">✔️ 3.11</span></span> | <span data-ttu-id="f65c6-132">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f65c6-132">✔️ 2.1</span></span>        | <span data-ttu-id="f65c6-133">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f65c6-133">✔️ 3.1</span></span>        | <span data-ttu-id="f65c6-134">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="f65c6-134">✔️ 5.0</span></span> |
| <span data-ttu-id="f65c6-135">✔️ 3.10</span><span class="sxs-lookup"><span data-stu-id="f65c6-135">✔️ 3.10</span></span> | <span data-ttu-id="f65c6-136">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f65c6-136">✔️ 2.1</span></span>        | <span data-ttu-id="f65c6-137">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f65c6-137">✔️ 3.1</span></span>        | <span data-ttu-id="f65c6-138">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="f65c6-138">❌ 5.0</span></span> |
| <span data-ttu-id="f65c6-139">❌ 3.9</span><span class="sxs-lookup"><span data-stu-id="f65c6-139">❌ 3.9</span></span>  | <span data-ttu-id="f65c6-140">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f65c6-140">✔️ 2.1</span></span>        | <span data-ttu-id="f65c6-141">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f65c6-141">✔️ 3.1</span></span>        | <span data-ttu-id="f65c6-142">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="f65c6-142">❌ 5.0</span></span> |
| <span data-ttu-id="f65c6-143">❌ 3.8</span><span class="sxs-lookup"><span data-stu-id="f65c6-143">❌ 3.8</span></span>  | <span data-ttu-id="f65c6-144">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f65c6-144">✔️ 2.1</span></span>        | <span data-ttu-id="f65c6-145">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f65c6-145">✔️ 3.1</span></span>        | <span data-ttu-id="f65c6-146">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="f65c6-146">❌ 5.0</span></span> |

<span data-ttu-id="f65c6-147">Следующие версии .NET больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="f65c6-147">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="f65c6-148">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="f65c6-148">The downloads for these still remain published:</span></span>

- <span data-ttu-id="f65c6-149">3.0</span><span class="sxs-lookup"><span data-stu-id="f65c6-149">3.0</span></span>
- <span data-ttu-id="f65c6-150">2.2</span><span class="sxs-lookup"><span data-stu-id="f65c6-150">2.2</span></span>
- <span data-ttu-id="f65c6-151">2.0</span><span class="sxs-lookup"><span data-stu-id="f65c6-151">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="f65c6-152">Зависимости</span><span class="sxs-lookup"><span data-stu-id="f65c6-152">Dependencies</span></span>

<span data-ttu-id="f65c6-153">Для .NET в Alpine Linux необходимо установить следующие зависимости:</span><span class="sxs-lookup"><span data-stu-id="f65c6-153">.NET on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="f65c6-154">bash</span><span class="sxs-lookup"><span data-stu-id="f65c6-154">bash</span></span>
- <span data-ttu-id="f65c6-155">icu-libs</span><span class="sxs-lookup"><span data-stu-id="f65c6-155">icu-libs</span></span>
- <span data-ttu-id="f65c6-156">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="f65c6-156">krb5-libs</span></span>
- <span data-ttu-id="f65c6-157">libgcc</span><span class="sxs-lookup"><span data-stu-id="f65c6-157">libgcc</span></span>
- <span data-ttu-id="f65c6-158">libgdiplus (если для приложения .NET требуется сборка *System.Drawing.Common*)</span><span class="sxs-lookup"><span data-stu-id="f65c6-158">libgdiplus (if the .NET app requires the *System.Drawing.Common* assembly)</span></span>
- <span data-ttu-id="f65c6-159">libintl</span><span class="sxs-lookup"><span data-stu-id="f65c6-159">libintl</span></span>
- <span data-ttu-id="f65c6-160">libssl 1.1 (Alpine версии 3.9 или более поздней)</span><span class="sxs-lookup"><span data-stu-id="f65c6-160">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="f65c6-161">libssl1.0 (Alpine версии 3.8 или более ранней)</span><span class="sxs-lookup"><span data-stu-id="f65c6-161">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="f65c6-162">libstdc++</span><span class="sxs-lookup"><span data-stu-id="f65c6-162">libstdc++</span></span>
- <span data-ttu-id="f65c6-163">zlib</span><span class="sxs-lookup"><span data-stu-id="f65c6-163">zlib</span></span>

<span data-ttu-id="f65c6-164">Чтобы установить необходимые требования, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="f65c6-164">To install the needed requirements, run the following command:</span></span>

```bash
apk add bash icu-libs krb5-libs libgcc libintl libssl1.1 libstdc++ zlib
```

<span data-ttu-id="f65c6-165">Для установки **libgdiplus**, возможно, потребуется указать репозиторий:</span><span class="sxs-lookup"><span data-stu-id="f65c6-165">To install **libgdiplus**, you may need to specify a repository:</span></span>

```bash
apk add libgdiplus --repository https://dl-3.alpinelinux.org/alpine/edge/testing/
```

## <a name="next-steps"></a><span data-ttu-id="f65c6-166">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="f65c6-166">Next steps</span></span>

- [<span data-ttu-id="f65c6-167">Включение заполнения клавишей TAB для .NET CLI</span><span class="sxs-lookup"><span data-stu-id="f65c6-167">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="f65c6-168">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f65c6-168">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
