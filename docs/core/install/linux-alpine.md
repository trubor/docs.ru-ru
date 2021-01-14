---
title: Установка .NET в Alpine — .NET
description: Здесь приводятся различные способы установки пакета SDK для .NET и среды выполнения .NET в Alpine.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 6adaa905c400b45526ebbc3d8e2606522863eec3
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970854"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a><span data-ttu-id="6dbbf-103">Установка пакета SDK для .NET или среды выполнения .NET в Alpine</span><span class="sxs-lookup"><span data-stu-id="6dbbf-103">Install the .NET SDK or the .NET Runtime on Alpine</span></span>

<span data-ttu-id="6dbbf-104">В этой статье описано, как установить .NET в Alpine.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-104">This article describes how to install .NET on Alpine.</span></span> <span data-ttu-id="6dbbf-105">Если поддержка какой-либо версии Alpine прекращается, то .NET также перестает поддерживать ее.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-105">When an Alpine version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="6dbbf-106">Но с помощью этих инструкций вы сможете запустить .NET даже в неподдерживаемых версиях.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install"></a><span data-ttu-id="6dbbf-107">Установить</span><span class="sxs-lookup"><span data-stu-id="6dbbf-107">Install</span></span>

<span data-ttu-id="6dbbf-108">Для Alpine Linux недоступны установщики.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-108">Installers aren't available for Alpine Linux.</span></span> <span data-ttu-id="6dbbf-109">Устанавливать .NET необходимо одним из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="6dbbf-109">You must install .NET in one of the following ways:</span></span>

- [<span data-ttu-id="6dbbf-110">Пакет Snap</span><span class="sxs-lookup"><span data-stu-id="6dbbf-110">Snap package</span></span>](linux-snap.md)
- [<span data-ttu-id="6dbbf-111">Установка с помощью скрипта _install-dotnet.sh_</span><span class="sxs-lookup"><span data-stu-id="6dbbf-111">Scripted install with _install-dotnet.sh_</span></span>](linux-scripted-manual.md#scripted-install)
- [<span data-ttu-id="6dbbf-112">Ручное извлечение двоичных файлов</span><span class="sxs-lookup"><span data-stu-id="6dbbf-112">Manual binary extraction</span></span>](linux-scripted-manual.md#manual-install)

## <a name="supported-distributions"></a><span data-ttu-id="6dbbf-113">Поддерживаемые дистрибутивы</span><span class="sxs-lookup"><span data-stu-id="6dbbf-113">Supported distributions</span></span>

<span data-ttu-id="6dbbf-114">В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET и версий Alpine, в которых они поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-114">The following table is a list of currently supported .NET releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="6dbbf-115">Эти версии поддерживаются до окончания поддержки версии [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) либо до окончания жизненного цикла версии [Alpine](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span><span class="sxs-lookup"><span data-stu-id="6dbbf-115">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="6dbbf-116">Значок ✔️ означает, что версия Alpine или .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-116">A ✔️ indicates that the version of Alpine or .NET is still supported.</span></span>
- <span data-ttu-id="6dbbf-117">Значок ❌ означает, что версия Alpine или версия .NET в таком выпуске Alpine не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-117">A ❌ indicates that the version of Alpine or .NET isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="6dbbf-118">Если значок ✔️ стоит как напротив версии Alpine, так и напротив версии .NET, это значит, что такое сочетание ОС и .NET поддерживается.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-118">When both a version of Alpine and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="6dbbf-119">Alpine</span><span class="sxs-lookup"><span data-stu-id="6dbbf-119">Alpine</span></span>  | <span data-ttu-id="6dbbf-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6dbbf-120">.NET Core 2.1</span></span> | <span data-ttu-id="6dbbf-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6dbbf-121">.NET Core 3.1</span></span> | <span data-ttu-id="6dbbf-122">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="6dbbf-122">.NET 5.0</span></span> |
|-------- |---------------|---------------|----------------|
| <span data-ttu-id="6dbbf-123">✔️ 3.12</span><span class="sxs-lookup"><span data-stu-id="6dbbf-123">✔️ 3.12</span></span> | <span data-ttu-id="6dbbf-124">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="6dbbf-124">✔️ 2.1</span></span>        | <span data-ttu-id="6dbbf-125">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="6dbbf-125">✔️ 3.1</span></span>        | <span data-ttu-id="6dbbf-126">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="6dbbf-126">✔️ 5.0</span></span> |
| <span data-ttu-id="6dbbf-127">✔️ 3.11</span><span class="sxs-lookup"><span data-stu-id="6dbbf-127">✔️ 3.11</span></span> | <span data-ttu-id="6dbbf-128">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="6dbbf-128">✔️ 2.1</span></span>        | <span data-ttu-id="6dbbf-129">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="6dbbf-129">✔️ 3.1</span></span>        | <span data-ttu-id="6dbbf-130">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="6dbbf-130">✔️ 5.0</span></span> |
| <span data-ttu-id="6dbbf-131">✔️ 3.10</span><span class="sxs-lookup"><span data-stu-id="6dbbf-131">✔️ 3.10</span></span> | <span data-ttu-id="6dbbf-132">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="6dbbf-132">✔️ 2.1</span></span>        | <span data-ttu-id="6dbbf-133">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="6dbbf-133">✔️ 3.1</span></span>        | <span data-ttu-id="6dbbf-134">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="6dbbf-134">❌ 5.0</span></span> |
| <span data-ttu-id="6dbbf-135">❌ 3.9</span><span class="sxs-lookup"><span data-stu-id="6dbbf-135">❌ 3.9</span></span>  | <span data-ttu-id="6dbbf-136">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="6dbbf-136">✔️ 2.1</span></span>        | <span data-ttu-id="6dbbf-137">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="6dbbf-137">✔️ 3.1</span></span>        | <span data-ttu-id="6dbbf-138">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="6dbbf-138">❌ 5.0</span></span> |
| <span data-ttu-id="6dbbf-139">❌ 3.8</span><span class="sxs-lookup"><span data-stu-id="6dbbf-139">❌ 3.8</span></span>  | <span data-ttu-id="6dbbf-140">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="6dbbf-140">✔️ 2.1</span></span>        | <span data-ttu-id="6dbbf-141">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="6dbbf-141">✔️ 3.1</span></span>        | <span data-ttu-id="6dbbf-142">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="6dbbf-142">❌ 5.0</span></span> |

<span data-ttu-id="6dbbf-143">Следующие версии .NET больше не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="6dbbf-143">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="6dbbf-144">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="6dbbf-144">The downloads for these still remain published:</span></span>

- <span data-ttu-id="6dbbf-145">3.0</span><span class="sxs-lookup"><span data-stu-id="6dbbf-145">3.0</span></span>
- <span data-ttu-id="6dbbf-146">2.2</span><span class="sxs-lookup"><span data-stu-id="6dbbf-146">2.2</span></span>
- <span data-ttu-id="6dbbf-147">2.0</span><span class="sxs-lookup"><span data-stu-id="6dbbf-147">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="6dbbf-148">Зависимости</span><span class="sxs-lookup"><span data-stu-id="6dbbf-148">Dependencies</span></span>

<span data-ttu-id="6dbbf-149">Для .NET в Alpine Linux необходимо установить следующие зависимости:</span><span class="sxs-lookup"><span data-stu-id="6dbbf-149">.NET on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="6dbbf-150">icu-libs</span><span class="sxs-lookup"><span data-stu-id="6dbbf-150">icu-libs</span></span>
- <span data-ttu-id="6dbbf-151">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="6dbbf-151">krb5-libs</span></span>
- <span data-ttu-id="6dbbf-152">libgcc</span><span class="sxs-lookup"><span data-stu-id="6dbbf-152">libgcc</span></span>
- <span data-ttu-id="6dbbf-153">libintl</span><span class="sxs-lookup"><span data-stu-id="6dbbf-153">libintl</span></span>
- <span data-ttu-id="6dbbf-154">libssl 1.1 (Alpine версии 3.9 или более поздней)</span><span class="sxs-lookup"><span data-stu-id="6dbbf-154">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="6dbbf-155">libssl1.0 (Alpine версии 3.8 или более ранней)</span><span class="sxs-lookup"><span data-stu-id="6dbbf-155">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="6dbbf-156">libstdc++</span><span class="sxs-lookup"><span data-stu-id="6dbbf-156">libstdc++</span></span>
- <span data-ttu-id="6dbbf-157">zlib</span><span class="sxs-lookup"><span data-stu-id="6dbbf-157">zlib</span></span>

## <a name="next-steps"></a><span data-ttu-id="6dbbf-158">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="6dbbf-158">Next steps</span></span>

- [<span data-ttu-id="6dbbf-159">Включение заполнения клавишей TAB для .NET CLI</span><span class="sxs-lookup"><span data-stu-id="6dbbf-159">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="6dbbf-160">Учебник. Создание консольного приложения с помощью пакета SDK для .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6dbbf-160">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
