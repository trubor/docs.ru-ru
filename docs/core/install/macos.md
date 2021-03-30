---
title: Установка .NET в macOS
description: Сведения о версиях macOS, в которых возможна установка .NET.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 9961d3e3ddb5f38be1c9c13c01af2e41815f50c9
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104875256"
---
# <a name="install-net-on-macos"></a><span data-ttu-id="91b3d-103">Установка .NET в macOS</span><span class="sxs-lookup"><span data-stu-id="91b3d-103">Install .NET on macOS</span></span>

> [!div class="op_single_selector"]
>
> - [Установка в Windows](windows.md)
> - [Установка в macOS](macos.md)
> - [Установка на Linux](linux.md)

<span data-ttu-id="91b3d-107">В этой статье вы узнаете, как установить .NET в macOS.</span><span class="sxs-lookup"><span data-stu-id="91b3d-107">In this article, you'll learn how to install .NET on macOS.</span></span> <span data-ttu-id="91b3d-108">.NET состоит из среды выполнения и пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="91b3d-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="91b3d-109">Среда выполнения используется для запуска приложения .NET и может не включаться в состав приложения.</span><span class="sxs-lookup"><span data-stu-id="91b3d-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="91b3d-110">Пакет SDK используется для создания приложений и библиотек .NET.</span><span class="sxs-lookup"><span data-stu-id="91b3d-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="91b3d-111">Среда выполнения .NET всегда устанавливается вместе с пакетом SDK.</span><span class="sxs-lookup"><span data-stu-id="91b3d-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="91b3d-112">.NET 5.0 является последней версией.</span><span class="sxs-lookup"><span data-stu-id="91b3d-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="91b3d-113">Загрузить .NET Core</span><span class="sxs-lookup"><span data-stu-id="91b3d-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet)

## <a name="supported-releases"></a><span data-ttu-id="91b3d-114">Поддерживаемые выпуски</span><span class="sxs-lookup"><span data-stu-id="91b3d-114">Supported releases</span></span>

<span data-ttu-id="91b3d-115">В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET и версий macOS, в которых они поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="91b3d-115">The following table is a list of currently supported .NET releases and the versions of macOS they're supported on.</span></span> <span data-ttu-id="91b3d-116">Эти версии будут поддерживаться до [окончания срока поддержки .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="91b3d-116">These versions remain supported either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

- <span data-ttu-id="91b3d-117">Значок ✔️ означает, что версия .NET Core поддерживается.</span><span class="sxs-lookup"><span data-stu-id="91b3d-117">A ✔️ indicates that the version of .NET Core is still supported.</span></span>
- <span data-ttu-id="91b3d-118">Значок ❌️ означает, что версия .NET Core не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="91b3d-118">A ❌ indicates that the version of .NET Core isn't supported.</span></span>

| <span data-ttu-id="91b3d-119">Операционная система</span><span class="sxs-lookup"><span data-stu-id="91b3d-119">Operating System</span></span>          | <span data-ttu-id="91b3d-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="91b3d-120">.NET Core 2.1</span></span> | <span data-ttu-id="91b3d-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="91b3d-121">.NET Core 3.1</span></span> | <span data-ttu-id="91b3d-122">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="91b3d-122">.NET 5.0</span></span> |
|---------------------------|---------------|---------------|----------------|
| <span data-ttu-id="91b3d-123">macOS 11.0 "Big Sur"</span><span class="sxs-lookup"><span data-stu-id="91b3d-123">macOS 11.0 "Big Sur"</span></span>        | <span data-ttu-id="91b3d-124">✔️ 2.1 ([заметки о выпуске][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="91b3d-124">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="91b3d-125">✔️ 3.1 ([заметки о выпуске][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="91b3d-125">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="91b3d-126">✔️ 5.0 ([заметки о выпуске][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="91b3d-126">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="91b3d-127">macOS 10.15 "Catalina"</span><span class="sxs-lookup"><span data-stu-id="91b3d-127">macOS 10.15 "Catalina"</span></span>    | <span data-ttu-id="91b3d-128">✔️ 2.1 ([заметки о выпуске][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="91b3d-128">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="91b3d-129">✔️ 3.1 ([заметки о выпуске][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="91b3d-129">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="91b3d-130">✔️ 5.0 ([заметки о выпуске][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="91b3d-130">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="91b3d-131">macOS 10.14 "Mojave"</span><span class="sxs-lookup"><span data-stu-id="91b3d-131">macOS 10.14 "Mojave"</span></span>      | <span data-ttu-id="91b3d-132">✔️ 2.1 ([заметки о выпуске][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="91b3d-132">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="91b3d-133">✔️ 3.1 ([заметки о выпуске][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="91b3d-133">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="91b3d-134">✔️ 5.0 ([заметки о выпуске][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="91b3d-134">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="91b3d-135">macOS 10.13 "High Sierra"</span><span class="sxs-lookup"><span data-stu-id="91b3d-135">macOS 10.13 "High Sierra"</span></span> | <span data-ttu-id="91b3d-136">✔️ 2.1 ([заметки о выпуске][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="91b3d-136">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="91b3d-137">✔️ 3.1 ([заметки о выпуске][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="91b3d-137">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="91b3d-138">✔️ 5.0 ([заметки о выпуске][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="91b3d-138">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="91b3d-139">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="91b3d-139">macOS 10.12 "Sierra"</span></span>      | <span data-ttu-id="91b3d-140">✔️ 2.1 ([заметки о выпуске][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="91b3d-140">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="91b3d-141">❌ 3.1 ([заметки о выпуске][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="91b3d-141">❌ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="91b3d-142">❌ 5.0 ([заметки о выпуске][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="91b3d-142">❌ 5.0 ([Release notes][release-notes-50])</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="91b3d-143">Неподдерживаемые выпуски</span><span class="sxs-lookup"><span data-stu-id="91b3d-143">Unsupported releases</span></span>

<span data-ttu-id="91b3d-144">Следующие версии .NET больше не поддерживаются (❌).</span><span class="sxs-lookup"><span data-stu-id="91b3d-144">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="91b3d-145">(но остаются доступными для скачивания):</span><span class="sxs-lookup"><span data-stu-id="91b3d-145">The downloads for these still remain published:</span></span>

- <span data-ttu-id="91b3d-146">3.0 ([заметки о выпуске][release-notes-30])</span><span class="sxs-lookup"><span data-stu-id="91b3d-146">3.0 ([Release notes][release-notes-30])</span></span>
- <span data-ttu-id="91b3d-147">2.2 ([заметки о выпуске][release-notes-22])</span><span class="sxs-lookup"><span data-stu-id="91b3d-147">2.2 ([Release notes][release-notes-22])</span></span>
- <span data-ttu-id="91b3d-148">2.0 ([заметки о выпуске][release-notes-20])</span><span class="sxs-lookup"><span data-stu-id="91b3d-148">2.0 ([Release notes][release-notes-20])</span></span>

## <a name="runtime-information"></a><span data-ttu-id="91b3d-149">Сведения о среде выполнения</span><span class="sxs-lookup"><span data-stu-id="91b3d-149">Runtime information</span></span>

<span data-ttu-id="91b3d-150">Среда выполнения используется для запуска приложений, созданных с помощью .NET.</span><span class="sxs-lookup"><span data-stu-id="91b3d-150">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="91b3d-151">При публикации приложения автор может включить среду выполнения в его состав.</span><span class="sxs-lookup"><span data-stu-id="91b3d-151">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="91b3d-152">В противном случае устанавливать среду выполнения будет пользователь.</span><span class="sxs-lookup"><span data-stu-id="91b3d-152">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="91b3d-153">В macOS можно установить две разные среды выполнения:</span><span class="sxs-lookup"><span data-stu-id="91b3d-153">There are two different runtimes you can install on macOS:</span></span>

- <span data-ttu-id="91b3d-154">*Среда выполнения ASP.NET Core*</span><span class="sxs-lookup"><span data-stu-id="91b3d-154">*ASP.NET Core runtime*</span></span>\
  <span data-ttu-id="91b3d-155">Используется для запуска приложений ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="91b3d-155">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="91b3d-156">Включает среду выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="91b3d-156">Includes the .NET runtime.</span></span>

- <span data-ttu-id="91b3d-157">*Среда выполнения .NET*</span><span class="sxs-lookup"><span data-stu-id="91b3d-157">*.NET runtime*</span></span>\
  <span data-ttu-id="91b3d-158">Простейшая среда выполнения, в состав которой не входят какие-либо другие среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="91b3d-158">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="91b3d-159">Чтобы обеспечить максимальный уровень совместимости с приложениями .NET, настоятельно рекомендуется устанавливать *среду выполнения ASP.NET Core*.</span><span class="sxs-lookup"><span data-stu-id="91b3d-159">It's highly recommended that you install *ASP.NET Core runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="91b3d-160">Загрузка среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="91b3d-160">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet)

## <a name="sdk-information"></a><span data-ttu-id="91b3d-161">Сведения о пакете SDK</span><span class="sxs-lookup"><span data-stu-id="91b3d-161">SDK information</span></span>

<span data-ttu-id="91b3d-162">Пакет SDK используется для создания и публикации приложений и библиотек .NET.</span><span class="sxs-lookup"><span data-stu-id="91b3d-162">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="91b3d-163">При установке пакета SDK также устанавливаются обе [среды выполнения](#runtime-information): ASP.NET Core и .NET.</span><span class="sxs-lookup"><span data-stu-id="91b3d-163">Installing the SDK includes both [runtimes](#runtime-information): ASP.NET Core and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="91b3d-164">Зависимости</span><span class="sxs-lookup"><span data-stu-id="91b3d-164">Dependencies</span></span>

<span data-ttu-id="91b3d-165">Платформа .NET поддерживается в следующих выпусках macOS:</span><span class="sxs-lookup"><span data-stu-id="91b3d-165">.NET is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="91b3d-166">Символ `+` представляет минимальную версию.</span><span class="sxs-lookup"><span data-stu-id="91b3d-166">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="91b3d-167">Версия .NET Core</span><span class="sxs-lookup"><span data-stu-id="91b3d-167">.NET Core Version</span></span> | <span data-ttu-id="91b3d-168">macOS</span><span class="sxs-lookup"><span data-stu-id="91b3d-168">macOS</span></span>                 | <span data-ttu-id="91b3d-169">Архитектуры</span><span class="sxs-lookup"><span data-stu-id="91b3d-169">Architectures</span></span> | <span data-ttu-id="91b3d-170">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="91b3d-170">More information</span></span>    |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="91b3d-171">5,0</span><span class="sxs-lookup"><span data-stu-id="91b3d-171">5.0</span></span>               | <span data-ttu-id="91b3d-172">High Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="91b3d-172">High Sierra (10.13+)</span></span>  | <span data-ttu-id="91b3d-173">X64</span><span class="sxs-lookup"><span data-stu-id="91b3d-173">x64</span></span> | [<span data-ttu-id="91b3d-174">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="91b3d-174">More information</span></span>](https://github.com/dotnet/core/blob/main/release-notes/5.0/5.0-supported-os.md) |
| <span data-ttu-id="91b3d-175">3.1</span><span class="sxs-lookup"><span data-stu-id="91b3d-175">3.1</span></span>               | <span data-ttu-id="91b3d-176">High Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="91b3d-176">High Sierra (10.13+)</span></span>  | <span data-ttu-id="91b3d-177">X64</span><span class="sxs-lookup"><span data-stu-id="91b3d-177">x64</span></span> | [<span data-ttu-id="91b3d-178">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="91b3d-178">More information</span></span>](https://github.com/dotnet/core/blob/main/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="91b3d-179">3.0</span><span class="sxs-lookup"><span data-stu-id="91b3d-179">3.0</span></span>               | <span data-ttu-id="91b3d-180">High Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="91b3d-180">High Sierra (10.13+)</span></span>  | <span data-ttu-id="91b3d-181">X64</span><span class="sxs-lookup"><span data-stu-id="91b3d-181">x64</span></span> | [<span data-ttu-id="91b3d-182">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="91b3d-182">More information</span></span>](https://github.com/dotnet/core/blob/main/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="91b3d-183">2.2</span><span class="sxs-lookup"><span data-stu-id="91b3d-183">2.2</span></span>               | <span data-ttu-id="91b3d-184">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="91b3d-184">Sierra (10.12+)</span></span>       | <span data-ttu-id="91b3d-185">X64</span><span class="sxs-lookup"><span data-stu-id="91b3d-185">x64</span></span> | [<span data-ttu-id="91b3d-186">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="91b3d-186">More information</span></span>](https://github.com/dotnet/core/blob/main/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="91b3d-187">2.1</span><span class="sxs-lookup"><span data-stu-id="91b3d-187">2.1</span></span>               | <span data-ttu-id="91b3d-188">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="91b3d-188">Sierra (10.12+)</span></span>       | <span data-ttu-id="91b3d-189">X64</span><span class="sxs-lookup"><span data-stu-id="91b3d-189">x64</span></span> | [<span data-ttu-id="91b3d-190">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="91b3d-190">More information</span></span>](https://github.com/dotnet/core/blob/main/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="91b3d-191">Начиная с macOS Catalina (версия 10.15) все программное обеспечение, созданное после 1 июня 2019 года и распространяемое с идентификатором разработчика, должно быть заверено.</span><span class="sxs-lookup"><span data-stu-id="91b3d-191">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="91b3d-192">Это требование относится к среде выполнения .NET, пакету SDK для .NET и программному обеспечению, созданному с помощью .NET.</span><span class="sxs-lookup"><span data-stu-id="91b3d-192">This requirement applies to the .NET runtime, .NET SDK, and software created with .NET.</span></span>

<span data-ttu-id="91b3d-193">Среда выполнения и установщики пакета SDK для .NET версии 5.0 и .NET Core 3.1, 3.0 и 2.1 были заверены с 18 февраля 2020 г.</span><span class="sxs-lookup"><span data-stu-id="91b3d-193">The runtime and SDK installers for .NET 5.0 and .NET Core 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="91b3d-194">Более ранние версии не заверены.</span><span class="sxs-lookup"><span data-stu-id="91b3d-194">Prior released versions aren't notarized.</span></span> <span data-ttu-id="91b3d-195">При запуске незаверенного приложения появится ошибка, аналогичная следующей:</span><span class="sxs-lookup"><span data-stu-id="91b3d-195">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![Оповещение о заверении macOS Catalina](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="91b3d-197">Дополнительные сведения о том, как принудительное заверение влияет на .NET (и ваши приложения .NET), см. в разделе [Работа с заверением macOS Catalina](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="91b3d-197">For more information about how enforced-notarization affects .NET (and your .NET apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="91b3d-198">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="91b3d-198">libgdiplus</span></span>

<span data-ttu-id="91b3d-199">Приложения .NET, которые используют сборку *System.Drawing.Common*, требуют установки libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="91b3d-199">.NET applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="91b3d-200">Легко получить libgdiplus можно с помощью диспетчера пакетов [Homebrew ("brew")](https://brew.sh/) для macOS.</span><span class="sxs-lookup"><span data-stu-id="91b3d-200">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="91b3d-201">После установки *brew* установите libgdiplus, выполнив следующие команды в окне терминала (аналог командной строки):</span><span class="sxs-lookup"><span data-stu-id="91b3d-201">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a><span data-ttu-id="91b3d-202">Установка с помощью установщика</span><span class="sxs-lookup"><span data-stu-id="91b3d-202">Install with an installer</span></span>

<span data-ttu-id="91b3d-203">В macOS есть автономные установщики, которые можно использовать для установки пакета SDK для .NET 5.0:</span><span class="sxs-lookup"><span data-stu-id="91b3d-203">macOS has standalone installers that can be used to install the .NET 5.0 SDK:</span></span>

- [<span data-ttu-id="91b3d-204">Процессоры x64 (64-разрядные)</span><span class="sxs-lookup"><span data-stu-id="91b3d-204">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)

## <a name="download-and-manually-install"></a><span data-ttu-id="91b3d-205">Скачивание и установка вручную</span><span class="sxs-lookup"><span data-stu-id="91b3d-205">Download and manually install</span></span>

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="91b3d-206">В качестве альтернативы установщикам macOS для .NET можно скачать и вручную установить пакет SDK и среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="91b3d-206">As an alternative to the macOS installers for .NET, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="91b3d-207">Ручная установка как правило выполняется в рамках тестирования непрерывной интеграции.</span><span class="sxs-lookup"><span data-stu-id="91b3d-207">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="91b3d-208">В большинстве случаев разработчикам и пользователям рекомендуется использовать [установщик](https://dotnet.microsoft.com/download/dotnet).</span><span class="sxs-lookup"><span data-stu-id="91b3d-208">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet).</span></span>

<span data-ttu-id="91b3d-209">При установке пакета SDK для .NET не нужно устанавливать соответствующую среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="91b3d-209">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="91b3d-210">Сначала скачайте **двоичный** выпуск пакета SDK или среды выполнения с одного из следующих сайтов:</span><span class="sxs-lookup"><span data-stu-id="91b3d-210">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="91b3d-211">✔️ [Скачиваемые файлы для .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="91b3d-211">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="91b3d-212">✔️ [Скачиваемые файлы .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1)</span><span class="sxs-lookup"><span data-stu-id="91b3d-212">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet/3.1)</span></span>
- <span data-ttu-id="91b3d-213">✔️ [Скачиваемые файлы .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet/2.1)</span><span class="sxs-lookup"><span data-stu-id="91b3d-213">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet/2.1)</span></span>
- [<span data-ttu-id="91b3d-214">Все скачиваемые файлы для .NET Core</span><span class="sxs-lookup"><span data-stu-id="91b3d-214">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet)

<span data-ttu-id="91b3d-215">Извлеките скачанный файл и используйте команду `export`, чтобы задать переменные, используемые .NET, а затем проверьте включение .NET в переменную PATH.</span><span class="sxs-lookup"><span data-stu-id="91b3d-215">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="91b3d-216">Чтобы извлечь среду выполнения и сделать команды .NET CLI доступными в терминале, сначала скачайте двоичный выпуск .NET.</span><span class="sxs-lookup"><span data-stu-id="91b3d-216">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="91b3d-217">Затем откройте терминал и выполните следующие команды в каталоге с сохраненным файлом.</span><span class="sxs-lookup"><span data-stu-id="91b3d-217">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="91b3d-218">Имя файла архива может отличаться в зависимости от скачанных файлов.</span><span class="sxs-lookup"><span data-stu-id="91b3d-218">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="91b3d-219">**Используйте следующие команды для извлечения скачанной среды выполнения или пакета SDK.**</span><span class="sxs-lookup"><span data-stu-id="91b3d-219">**Use the following commands to extract the runtime or SDK that you downloaded.**</span></span> <span data-ttu-id="91b3d-220">Не забудьте заменить значение `DOTNET_FILE` на имя файла:</span><span class="sxs-lookup"><span data-stu-id="91b3d-220">Remember to change the `DOTNET_FILE` value to your file name:</span></span>

```bash
DOTNET_FILE=dotnet-sdk-5.0.102-linux-x64.tar.gz
export DOTNET_ROOT=$HOME/dotnet

mkdir -p "$DOTNET_ROOT" && tar zxf "$DOTNET_FILE" -C "$DOTNET_ROOT"

export PATH=$PATH:$DOTNET_ROOT
```

> [!TIP]
> <span data-ttu-id="91b3d-221">Приведенные выше команды `export` сделают команды .NET CLI доступными только для сеанса терминала, в котором производился запуск.</span><span class="sxs-lookup"><span data-stu-id="91b3d-221">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="91b3d-222">Вы можете изменить профиль оболочки, чтобы добавить команды окончательно.</span><span class="sxs-lookup"><span data-stu-id="91b3d-222">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="91b3d-223">Существует несколько различных оболочек, доступных для Linux, и каждая из них имеет свой профиль.</span><span class="sxs-lookup"><span data-stu-id="91b3d-223">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="91b3d-224">Пример:</span><span class="sxs-lookup"><span data-stu-id="91b3d-224">For example:</span></span>
>
> - <span data-ttu-id="91b3d-225">**Оболочка Bash**: *~/.bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="91b3d-225">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="91b3d-226">**Оболочка Korn**: *~/.kshrc* или *.profile*</span><span class="sxs-lookup"><span data-stu-id="91b3d-226">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="91b3d-227">**Оболочка Z**: *~/.zshrc* или *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="91b3d-227">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="91b3d-228">Измените соответствующий исходный файл оболочки и добавьте `:$HOME/dotnet` в конец существующего оператора `PATH`.</span><span class="sxs-lookup"><span data-stu-id="91b3d-228">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="91b3d-229">Если оператор `PATH` не указан, добавьте новую строку с `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="91b3d-229">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="91b3d-230">Кроме того, добавьте `export DOTNET_ROOT=$HOME/dotnet` в конец файла.</span><span class="sxs-lookup"><span data-stu-id="91b3d-230">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="91b3d-231">Такой подход позволяет устанавливать разные версии в отдельные расположения и выбирать, какие из них следует использовать для каждого приложения.</span><span class="sxs-lookup"><span data-stu-id="91b3d-231">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="91b3d-232">Установка с помощью Visual Studio для Mac</span><span class="sxs-lookup"><span data-stu-id="91b3d-232">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="91b3d-233">Visual Studio для Mac устанавливает пакет SDK для .NET, если выбрана рабочая нагрузка **.NET**.</span><span class="sxs-lookup"><span data-stu-id="91b3d-233">Visual Studio for Mac installs the .NET SDK when the **.NET** workload is selected.</span></span> <span data-ttu-id="91b3d-234">Чтобы приступить к разработке в .NET на macOS, ознакомьтесь со статьей [Установка Visual Studio 2019 для Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="91b3d-234">To get started with .NET development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

| <span data-ttu-id="91b3d-235">Версия пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="91b3d-235">.NET SDK version</span></span>      | <span data-ttu-id="91b3d-236">Версия Visual Studio</span><span class="sxs-lookup"><span data-stu-id="91b3d-236">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="91b3d-237">5,0</span><span class="sxs-lookup"><span data-stu-id="91b3d-237">5.0</span></span>                   | <span data-ttu-id="91b3d-238">Visual Studio 2019 для Mac версии 8.8 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="91b3d-238">Visual Studio 2019 for Mac version 8.8 or higher.</span></span> |
| <span data-ttu-id="91b3d-239">3.1</span><span class="sxs-lookup"><span data-stu-id="91b3d-239">3.1</span></span>                   | <span data-ttu-id="91b3d-240">Visual Studio 2019 для Mac версии 8.4 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="91b3d-240">Visual Studio 2019 for Mac version 8.4 or higher.</span></span> |
| <span data-ttu-id="91b3d-241">2.1</span><span class="sxs-lookup"><span data-stu-id="91b3d-241">2.1</span></span>                   | <span data-ttu-id="91b3d-242">Visual Studio 2019 для Mac версии 8.0 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="91b3d-242">Visual Studio 2019 for Mac version 8.0 or higher.</span></span> |

<span data-ttu-id="91b3d-243">[![Visual Studio 2019 для Mac с компонентом рабочей нагрузки .NET в macOS](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="91b3d-243">[![macOS Visual Studio 2019 for Mac with .NET workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="91b3d-244">Установка вместе с Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="91b3d-244">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="91b3d-245">Visual Studio Code — это эффективный и облегченный редактор исходного кода, который работает на компьютере.</span><span class="sxs-lookup"><span data-stu-id="91b3d-245">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="91b3d-246">Visual Studio Code доступен для Windows, macOS и Linux.</span><span class="sxs-lookup"><span data-stu-id="91b3d-246">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="91b3d-247">Хотя Visual Studio Code не поставляется с автоматическим установщиком .NET, таким как Visual Studio, добавление поддержки .NET не вызывает затруднений.</span><span class="sxs-lookup"><span data-stu-id="91b3d-247">While Visual Studio Code doesn't come with an automated .NET installer like Visual Studio does, adding .NET support is simple.</span></span>

01. <span data-ttu-id="91b3d-248">[Скачайте и установите Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="91b3d-248">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="91b3d-249">[Скачайте и установите пакет SDK для .NET](https://dotnet.microsoft.com/download/dotnet).</span><span class="sxs-lookup"><span data-stu-id="91b3d-249">[Download and install the .NET SDK](https://dotnet.microsoft.com/download/dotnet).</span></span>
01. <span data-ttu-id="91b3d-250">[Установите расширение C# из Marketplace для Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="91b3d-250">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="install-with-bash-automation"></a><span data-ttu-id="91b3d-251">Установка с помощью функции автоматизации Bash</span><span class="sxs-lookup"><span data-stu-id="91b3d-251">Install with bash automation</span></span>

<span data-ttu-id="91b3d-252">[Сценарии dotnet-install](../tools/dotnet-install-script.md) используются для автоматизации установок среды выполнения и их осуществления без прав администратора.</span><span class="sxs-lookup"><span data-stu-id="91b3d-252">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="91b3d-253">Вы можете скачать сценарий со [страницы справочника по сценариям dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="91b3d-253">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="91b3d-254">Этот сценарий по умолчанию устанавливает последнюю версию [с долгосрочной поддержкой (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core), которой сейчас является .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="91b3d-254">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="91b3d-255">Вы можете выбрать конкретный выпуск, указав параметр `current`.</span><span class="sxs-lookup"><span data-stu-id="91b3d-255">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="91b3d-256">Включите параметр `runtime` для установки среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="91b3d-256">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="91b3d-257">В противном случае сценарий устанавливает пакет [SDK](./windows.md).</span><span class="sxs-lookup"><span data-stu-id="91b3d-257">Otherwise, the script installs the [SDK](./windows.md).</span></span>

```bash
./dotnet-install.sh --channel 5.0 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="91b3d-258">Приведенная выше команда устанавливает среду выполнения ASP.NET Core для максимальной совместимости.</span><span class="sxs-lookup"><span data-stu-id="91b3d-258">The previous command installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="91b3d-259">Среда выполнения ASP.NET Core также включает в себя стандартную среду выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="91b3d-259">The ASP.NET Core runtime also includes the standard .NET runtime.</span></span>

## <a name="docker"></a><span data-ttu-id="91b3d-260">Docker</span><span class="sxs-lookup"><span data-stu-id="91b3d-260">Docker</span></span>

<span data-ttu-id="91b3d-261">Контейнеры обеспечивают простой способ изоляции приложения от остальной части основной системы.</span><span class="sxs-lookup"><span data-stu-id="91b3d-261">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="91b3d-262">Контейнеры на одном компьютере совместно использую только ядро, а также используют ресурсы, которые передаются в приложение.</span><span class="sxs-lookup"><span data-stu-id="91b3d-262">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="91b3d-263">.NET можно выполнять в контейнере Docker.</span><span class="sxs-lookup"><span data-stu-id="91b3d-263">.NET can run in a Docker container.</span></span> <span data-ttu-id="91b3d-264">Официальные образы Docker для .NET публикуются в реестре контейнеров Microsoft (MCR), и доступ к ним можно получить в [репозитории Microsoft .NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet/).</span><span class="sxs-lookup"><span data-stu-id="91b3d-264">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet/).</span></span> <span data-ttu-id="91b3d-265">Каждый репозиторий содержит рабочие образы для разных сочетаний .NET (пакета SDK или среды выполнения) и операционной системы.</span><span class="sxs-lookup"><span data-stu-id="91b3d-265">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="91b3d-266">Корпорация Майкрософт предоставляет образы, которые предназначены для конкретных сценариев.</span><span class="sxs-lookup"><span data-stu-id="91b3d-266">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="91b3d-267">Например [репозиторий ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-aspnet) содержит образы, которые предназначены для запуска приложений ASP.NET Core в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="91b3d-267">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="91b3d-268">Дополнительные сведения об использовании .NET Core в контейнере Docker см. в статьях [Введение в .NET и Docker](../docker/introduction.md) и [Примеры](https://github.com/dotnet/dotnet-docker/blob/main/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="91b3d-268">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/main/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="91b3d-269">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="91b3d-269">Next steps</span></span>

- <span data-ttu-id="91b3d-270">[Проверка того, установлена ли платформа .NET Core](how-to-detect-installed-versions.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="91b3d-270">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-macos).</span></span>
- <span data-ttu-id="91b3d-271">[Работа с заверением macOS Catalina](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="91b3d-271">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="91b3d-272">[Учебник. Начало работы с macOS](../tutorials/with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="91b3d-272">[Tutorial: Get started on macOS](../tutorials/with-visual-studio-mac.md).</span></span>
- <span data-ttu-id="91b3d-273">[Учебник. Создание приложения с помощью Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="91b3d-273">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="91b3d-274">[Учебник. Контейнеризация приложения .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="91b3d-274">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[release-notes-21]: https://github.com/dotnet/core/blob/main/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/main/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/main/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/main/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/main/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/main/release-notes/3.0/3.0-supported-os.md
