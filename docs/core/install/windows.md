---
title: Установка .NET в Windows
description: Сведения о версиях Windows, в которых возможна установка .NET.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 55746b29b579a6d3aacb7d11c5604dc601440ab5
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506296"
---
# <a name="install-net-on-windows"></a><span data-ttu-id="6b436-103">Установка .NET в Windows</span><span class="sxs-lookup"><span data-stu-id="6b436-103">Install .NET on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [Установка в Windows](windows.md)
> - [Установка в macOS](macos.md)
> - [Установка на Linux](linux.md)

<span data-ttu-id="6b436-107">В этой статье вы узнаете, как установить .NET в Windows.</span><span class="sxs-lookup"><span data-stu-id="6b436-107">In this article, you'll learn how to install .NET on Windows.</span></span> <span data-ttu-id="6b436-108">.NET состоит из среды выполнения и пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="6b436-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="6b436-109">Среда выполнения используется для запуска приложения .NET и может не включаться в состав приложения.</span><span class="sxs-lookup"><span data-stu-id="6b436-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="6b436-110">Пакет SDK используется для создания приложений и библиотек .NET.</span><span class="sxs-lookup"><span data-stu-id="6b436-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="6b436-111">Среда выполнения .NET всегда устанавливается вместе с пакетом SDK.</span><span class="sxs-lookup"><span data-stu-id="6b436-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="6b436-112">.NET 5.0 является последней версией.</span><span class="sxs-lookup"><span data-stu-id="6b436-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="6b436-113">Скачать .NET</span><span class="sxs-lookup"><span data-stu-id="6b436-113">Download .NET</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="6b436-114">Поддерживаемые выпуски</span><span class="sxs-lookup"><span data-stu-id="6b436-114">Supported releases</span></span>

<span data-ttu-id="6b436-115">В приведенной ниже таблице содержится список поддерживаемых сейчас выпусков .NET и версий Windows, в которых они поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="6b436-115">The following table is a list of currently supported .NET releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="6b436-116">Эти версии поддерживаются до окончания поддержки версии [.NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core), либо до окончания жизненного цикла версии [Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span><span class="sxs-lookup"><span data-stu-id="6b436-116">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="6b436-117">Даты окончания жизненного цикла версий Windows 10 зависят от выпуска.</span><span class="sxs-lookup"><span data-stu-id="6b436-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="6b436-118">В следующей таблице рассматриваются только выпуски **Домашняя**, **Профессиональная**, **Pro для образовательных учреждений** и **Pro для рабочих станций**.</span><span class="sxs-lookup"><span data-stu-id="6b436-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="6b436-119">Дополнительные сведения см. в [справочных материалах по жизненному циклу поддержки Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span><span class="sxs-lookup"><span data-stu-id="6b436-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

> [!TIP]
> <span data-ttu-id="6b436-120">Символ `+` представляет минимальную версию.</span><span class="sxs-lookup"><span data-stu-id="6b436-120">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6b436-121">Операционная система</span><span class="sxs-lookup"><span data-stu-id="6b436-121">Operating System</span></span>            | <span data-ttu-id="6b436-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6b436-122">.NET Core 2.1</span></span> | <span data-ttu-id="6b436-123">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6b436-123">.NET Core 3.1</span></span> | <span data-ttu-id="6b436-124">.NET 5</span><span class="sxs-lookup"><span data-stu-id="6b436-124">.NET 5</span></span> |
|-----------------------------|---------------|---------------|--------|
| <span data-ttu-id="6b436-125">Windows 10 или Windows Server версии 20H2</span><span class="sxs-lookup"><span data-stu-id="6b436-125">Windows 10 / Windows Server, Version 20H2</span></span>    | <span data-ttu-id="6b436-126">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-126">✔️</span></span>           | <span data-ttu-id="6b436-127">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-127">✔️</span></span>            | <span data-ttu-id="6b436-128">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-128">✔️</span></span>    |
| <span data-ttu-id="6b436-129">Windows 10 или Windows Server версии 2004</span><span class="sxs-lookup"><span data-stu-id="6b436-129">Windows 10 / Windows Server, Version 2004</span></span>    | <span data-ttu-id="6b436-130">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-130">✔️</span></span>           | <span data-ttu-id="6b436-131">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-131">✔️</span></span>            | <span data-ttu-id="6b436-132">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-132">✔️</span></span>    |
| <span data-ttu-id="6b436-133">Windows 10 или Windows Server версии 1909</span><span class="sxs-lookup"><span data-stu-id="6b436-133">Windows 10 / Windows Server, Version 1909</span></span>    | <span data-ttu-id="6b436-134">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-134">✔️</span></span>           | <span data-ttu-id="6b436-135">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-135">✔️</span></span>            | <span data-ttu-id="6b436-136">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-136">✔️</span></span>    |
| <span data-ttu-id="6b436-137">Windows 10 или Windows Server версии 1903</span><span class="sxs-lookup"><span data-stu-id="6b436-137">Windows 10 / Windows Server, Version 1903</span></span>    | <span data-ttu-id="6b436-138">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-138">✔️</span></span>           | <span data-ttu-id="6b436-139">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-139">✔️</span></span>            | <span data-ttu-id="6b436-140">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-140">✔️</span></span>    |
| <span data-ttu-id="6b436-141">Windows 10, версия 1809</span><span class="sxs-lookup"><span data-stu-id="6b436-141">Windows 10, Version 1809</span></span>    | <span data-ttu-id="6b436-142">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-142">✔️</span></span>           | <span data-ttu-id="6b436-143">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-143">✔️</span></span>            | <span data-ttu-id="6b436-144">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-144">✔️</span></span>    |
| <span data-ttu-id="6b436-145"> Windows 10, версия 1803</span><span class="sxs-lookup"><span data-stu-id="6b436-145">Windows 10, Version 1803</span></span>    | <span data-ttu-id="6b436-146">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-146">✔️</span></span>           | <span data-ttu-id="6b436-147">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-147">✔️</span></span>            | <span data-ttu-id="6b436-148">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-148">✔️</span></span>    |
| <span data-ttu-id="6b436-149"> Windows 10, версия 1709</span><span class="sxs-lookup"><span data-stu-id="6b436-149">Windows 10, Version 1709</span></span>    | <span data-ttu-id="6b436-150">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-150">✔️</span></span>           | <span data-ttu-id="6b436-151">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-151">✔️</span></span>            | <span data-ttu-id="6b436-152">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-152">✔️</span></span>    |
| <span data-ttu-id="6b436-153">Windows 10 (версия 1607)</span><span class="sxs-lookup"><span data-stu-id="6b436-153">Windows 10, Version 1607</span></span>    | <span data-ttu-id="6b436-154">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-154">✔️</span></span>           | <span data-ttu-id="6b436-155">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-155">✔️</span></span>            | <span data-ttu-id="6b436-156">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-156">✔️</span></span>    |
| <span data-ttu-id="6b436-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="6b436-157">Windows 8.1</span></span>                 | <span data-ttu-id="6b436-158">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-158">✔️</span></span>           | <span data-ttu-id="6b436-159">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-159">✔️</span></span>            | <span data-ttu-id="6b436-160">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-160">✔️</span></span>    |
| <span data-ttu-id="6b436-161">Windows 7 с пакетом обновления 1 (SP1), [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="6b436-161">Windows 7 SP1 [ESU][esu]</span></span>    | <span data-ttu-id="6b436-162">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-162">✔️</span></span>           | <span data-ttu-id="6b436-163">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-163">✔️</span></span>            | <span data-ttu-id="6b436-164">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-164">✔️</span></span>    |
| <span data-ttu-id="6b436-165">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="6b436-165">Windows Server 2019</span></span><br><span data-ttu-id="6b436-166">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="6b436-166">Windows Server 2016</span></span><br><span data-ttu-id="6b436-167">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6b436-167">Windows Server 2012 R2</span></span><br>      | <span data-ttu-id="6b436-168">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-168">✔️</span></span>           | <span data-ttu-id="6b436-169">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-169">✔️</span></span>            | <span data-ttu-id="6b436-170">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-170">✔️</span></span>    |
| <span data-ttu-id="6b436-171">Windows Server Core 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6b436-171">Windows Server Core 2012 R2</span></span> | <span data-ttu-id="6b436-172">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-172">✔️</span></span>           | <span data-ttu-id="6b436-173">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-173">✔️</span></span>            | <span data-ttu-id="6b436-174">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-174">✔️</span></span>    |
| <span data-ttu-id="6b436-175">Nano Server, версия 1809 и выше</span><span class="sxs-lookup"><span data-stu-id="6b436-175">Nano Server, Version 1809+</span></span>  | <span data-ttu-id="6b436-176">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-176">✔️</span></span>           | <span data-ttu-id="6b436-177">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-177">✔️</span></span>            | <span data-ttu-id="6b436-178">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-178">✔️</span></span>    |
| <span data-ttu-id="6b436-179">Nano Server, версия 1803</span><span class="sxs-lookup"><span data-stu-id="6b436-179">Nano Server, Version 1803</span></span>   | <span data-ttu-id="6b436-180">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-180">✔️</span></span>           | <span data-ttu-id="6b436-181">✔️</span><span class="sxs-lookup"><span data-stu-id="6b436-181">✔️</span></span>            | ❌    |

## <a name="unsupported-releases"></a><span data-ttu-id="6b436-182">Неподдерживаемые выпуски</span><span class="sxs-lookup"><span data-stu-id="6b436-182">Unsupported releases</span></span>

<span data-ttu-id="6b436-183">Следующие версии .NET больше не поддерживаются (❌).</span><span class="sxs-lookup"><span data-stu-id="6b436-183">The following versions of .NET are ❌ no longer supported:</span></span>

- <span data-ttu-id="6b436-184">3.0</span><span class="sxs-lookup"><span data-stu-id="6b436-184">3.0</span></span>
- <span data-ttu-id="6b436-185">2.2</span><span class="sxs-lookup"><span data-stu-id="6b436-185">2.2</span></span>
- <span data-ttu-id="6b436-186">2.0</span><span class="sxs-lookup"><span data-stu-id="6b436-186">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="6b436-187">Сведения о среде выполнения</span><span class="sxs-lookup"><span data-stu-id="6b436-187">Runtime information</span></span>

<span data-ttu-id="6b436-188">Среда выполнения используется для запуска приложений, созданных с помощью .NET.</span><span class="sxs-lookup"><span data-stu-id="6b436-188">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="6b436-189">При публикации приложения автор может включить среду выполнения в его состав.</span><span class="sxs-lookup"><span data-stu-id="6b436-189">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="6b436-190">В противном случае устанавливать среду выполнения будет пользователь.</span><span class="sxs-lookup"><span data-stu-id="6b436-190">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="6b436-191">В Windows можно установить три различные версии среды выполнения:</span><span class="sxs-lookup"><span data-stu-id="6b436-191">There are three different runtimes you can install on Windows:</span></span>

- <span data-ttu-id="6b436-192">*Среда выполнения ASP.NET Core*</span><span class="sxs-lookup"><span data-stu-id="6b436-192">*ASP.NET Core runtime*</span></span>\
  <span data-ttu-id="6b436-193">Используется для запуска приложений ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b436-193">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="6b436-194">Включает среду выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="6b436-194">Includes the .NET runtime.</span></span>

- <span data-ttu-id="6b436-195">*Среда выполнения для классических приложений*</span><span class="sxs-lookup"><span data-stu-id="6b436-195">*Desktop runtime*</span></span>\
  <span data-ttu-id="6b436-196">Используется для запуска классических приложений .NET WPF и Windows Forms для Windows.</span><span class="sxs-lookup"><span data-stu-id="6b436-196">Runs .NET WPF and Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="6b436-197">Включает среду выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="6b436-197">Includes the .NET runtime.</span></span>

- <span data-ttu-id="6b436-198">*Среда выполнения .NET*</span><span class="sxs-lookup"><span data-stu-id="6b436-198">*.NET runtime*</span></span>\
  <span data-ttu-id="6b436-199">Простейшая среда выполнения, в состав которой не входят какие-либо другие среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="6b436-199">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="6b436-200">Чтобы обеспечить максимальный уровень совместимости с приложениями .NET, настоятельно рекомендуется устанавливать *среду выполнения ASP.NET Core* и *среду выполнения для классических приложений*.</span><span class="sxs-lookup"><span data-stu-id="6b436-200">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="6b436-201">Загрузка среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="6b436-201">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="6b436-202">Сведения о пакете SDK</span><span class="sxs-lookup"><span data-stu-id="6b436-202">SDK information</span></span>

<span data-ttu-id="6b436-203">Пакет SDK используется для создания и публикации приложений и библиотек .NET.</span><span class="sxs-lookup"><span data-stu-id="6b436-203">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="6b436-204">При установке пакета SDK также устанавливаются все три [среды выполнения](#runtime-information): ASP.NET Core, компьютер и .NET.</span><span class="sxs-lookup"><span data-stu-id="6b436-204">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="6b436-205">Зависимости</span><span class="sxs-lookup"><span data-stu-id="6b436-205">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[<span data-ttu-id="6b436-206">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="6b436-206">.NET 5.0</span></span>](#tab/net50)

<span data-ttu-id="6b436-207">.NET 5.0 поддерживает следующие версии Windows:</span><span class="sxs-lookup"><span data-stu-id="6b436-207">The following Windows versions are supported with .NET 5.0:</span></span>

> [!NOTE]
> <span data-ttu-id="6b436-208">Символ `+` представляет минимальную версию.</span><span class="sxs-lookup"><span data-stu-id="6b436-208">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6b436-209">Операционная система</span><span class="sxs-lookup"><span data-stu-id="6b436-209">OS</span></span>                  | <span data-ttu-id="6b436-210">Version</span><span class="sxs-lookup"><span data-stu-id="6b436-210">Version</span></span>       | <span data-ttu-id="6b436-211">Архитектуры</span><span class="sxs-lookup"><span data-stu-id="6b436-211">Architectures</span></span>   |
|---------------------|---------------|-----------------|
| <span data-ttu-id="6b436-212">Клиент Windows 10</span><span class="sxs-lookup"><span data-stu-id="6b436-212">Windows 10 Client</span></span>   | <span data-ttu-id="6b436-213">Версия 1607+</span><span class="sxs-lookup"><span data-stu-id="6b436-213">Version 1607+</span></span> | <span data-ttu-id="6b436-214">x64, x86, ARM64</span><span class="sxs-lookup"><span data-stu-id="6b436-214">x64, x86, ARM64</span></span> |
| <span data-ttu-id="6b436-215">Клиент Windows</span><span class="sxs-lookup"><span data-stu-id="6b436-215">Windows Client</span></span>      | <span data-ttu-id="6b436-216">7 с пакетом обновления 1 и более поздних версий (SP1+), 8.1</span><span class="sxs-lookup"><span data-stu-id="6b436-216">7 SP1+, 8.1</span></span>   | <span data-ttu-id="6b436-217">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-217">x64, x86</span></span>        |
| <span data-ttu-id="6b436-218">Windows Server</span><span class="sxs-lookup"><span data-stu-id="6b436-218">Windows Server</span></span>      | <span data-ttu-id="6b436-219">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="6b436-219">2012 R2+</span></span>      | <span data-ttu-id="6b436-220">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-220">x64, x86</span></span>        |
| <span data-ttu-id="6b436-221">Windows Server Core</span><span class="sxs-lookup"><span data-stu-id="6b436-221">Windows Server Core</span></span> | <span data-ttu-id="6b436-222">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="6b436-222">2012 R2+</span></span>      | <span data-ttu-id="6b436-223">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-223">x64, x86</span></span>        |
| <span data-ttu-id="6b436-224">Nano Server</span><span class="sxs-lookup"><span data-stu-id="6b436-224">Nano Server</span></span>         | <span data-ttu-id="6b436-225">Версия 1809+</span><span class="sxs-lookup"><span data-stu-id="6b436-225">Version 1809+</span></span> | <span data-ttu-id="6b436-226">X64</span><span class="sxs-lookup"><span data-stu-id="6b436-226">x64</span></span>             |

<span data-ttu-id="6b436-227">Дополнительные сведения об операционных системах, дистрибутивах и политике жизненного цикла, поддерживаемых .NET 5.0, см. в статье [Поддерживаемые .NET 5.0 версии ОС](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6b436-227">For more information about .NET 5.0 supported operating systems, distributions, and lifecycle policy, see [.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span></span>

# <a name="net-core-31"></a>[<span data-ttu-id="6b436-228">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6b436-228">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="6b436-229">.NET Core 3.1 поддерживает следующие версии Windows:</span><span class="sxs-lookup"><span data-stu-id="6b436-229">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="6b436-230">Символ `+` представляет минимальную версию.</span><span class="sxs-lookup"><span data-stu-id="6b436-230">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6b436-231">Операционная система</span><span class="sxs-lookup"><span data-stu-id="6b436-231">OS</span></span>                            | <span data-ttu-id="6b436-232">Version</span><span class="sxs-lookup"><span data-stu-id="6b436-232">Version</span></span>                        | <span data-ttu-id="6b436-233">Архитектуры</span><span class="sxs-lookup"><span data-stu-id="6b436-233">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="6b436-234">Клиент Windows</span><span class="sxs-lookup"><span data-stu-id="6b436-234">Windows Client</span></span>                | <span data-ttu-id="6b436-235">7 с пакетом обновления 1 и более поздних версий (SP1+), 8.1</span><span class="sxs-lookup"><span data-stu-id="6b436-235">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="6b436-236">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-236">x64, x86</span></span>        |
| <span data-ttu-id="6b436-237">Клиент Windows 10</span><span class="sxs-lookup"><span data-stu-id="6b436-237">Windows 10 Client</span></span>             | <span data-ttu-id="6b436-238">Версия 1607+</span><span class="sxs-lookup"><span data-stu-id="6b436-238">Version 1607+</span></span>                  | <span data-ttu-id="6b436-239">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-239">x64, x86</span></span>        |
| <span data-ttu-id="6b436-240">Windows Server</span><span class="sxs-lookup"><span data-stu-id="6b436-240">Windows Server</span></span>                | <span data-ttu-id="6b436-241">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="6b436-241">2012 R2+</span></span>                       | <span data-ttu-id="6b436-242">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-242">x64, x86</span></span>        |
| <span data-ttu-id="6b436-243">Nano Server</span><span class="sxs-lookup"><span data-stu-id="6b436-243">Nano Server</span></span>                   | <span data-ttu-id="6b436-244">Версия 1803+</span><span class="sxs-lookup"><span data-stu-id="6b436-244">Version 1803+</span></span>                  | <span data-ttu-id="6b436-245">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6b436-245">x64, ARM32</span></span>      |

<span data-ttu-id="6b436-246">Дополнительные сведения об операционных системах, дистрибутивах и политике жизненного цикла, поддерживаемых .NET Core 3.1, см. в статье [Поддерживаемые .NET Core 3.1 версии ОС](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6b436-246">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="6b436-247">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6b436-247">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="6b436-248">*Сейчас .NET Core 3.0 ❌ не поддерживается. Дополнительные сведения см. в статье о [политике поддержки .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="6b436-248">*.NET Core 3.0 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="6b436-249">.NET Core 3.0 поддерживает следующие версии Windows:</span><span class="sxs-lookup"><span data-stu-id="6b436-249">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="6b436-250">Символ `+` представляет минимальную версию.</span><span class="sxs-lookup"><span data-stu-id="6b436-250">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6b436-251">Операционная система</span><span class="sxs-lookup"><span data-stu-id="6b436-251">OS</span></span>                            | <span data-ttu-id="6b436-252">Version</span><span class="sxs-lookup"><span data-stu-id="6b436-252">Version</span></span>                        | <span data-ttu-id="6b436-253">Архитектуры</span><span class="sxs-lookup"><span data-stu-id="6b436-253">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="6b436-254">Клиент Windows</span><span class="sxs-lookup"><span data-stu-id="6b436-254">Windows Client</span></span>                | <span data-ttu-id="6b436-255">7 с пакетом обновления 1 и более поздних версий (SP1+), 8.1</span><span class="sxs-lookup"><span data-stu-id="6b436-255">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="6b436-256">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-256">x64, x86</span></span>        |
| <span data-ttu-id="6b436-257">Клиент Windows 10</span><span class="sxs-lookup"><span data-stu-id="6b436-257">Windows 10 Client</span></span>             | <span data-ttu-id="6b436-258">Версия 1607+</span><span class="sxs-lookup"><span data-stu-id="6b436-258">Version 1607+</span></span>                  | <span data-ttu-id="6b436-259">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-259">x64, x86</span></span>        |
| <span data-ttu-id="6b436-260">Windows Server</span><span class="sxs-lookup"><span data-stu-id="6b436-260">Windows Server</span></span>                | <span data-ttu-id="6b436-261">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="6b436-261">2012 R2+</span></span>                       | <span data-ttu-id="6b436-262">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-262">x64, x86</span></span>        |
| <span data-ttu-id="6b436-263">Nano Server</span><span class="sxs-lookup"><span data-stu-id="6b436-263">Nano Server</span></span>                   | <span data-ttu-id="6b436-264">Версия 1803+</span><span class="sxs-lookup"><span data-stu-id="6b436-264">Version 1803+</span></span>                  | <span data-ttu-id="6b436-265">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6b436-265">x64, ARM32</span></span>      |

<span data-ttu-id="6b436-266">Дополнительные сведения об операционных системах, дистрибутивах и политике жизненного цикла, поддерживаемых .NET Core 3.0, см. в статье [Поддерживаемые .NET Core 3.0 версии ОС](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6b436-266">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="6b436-267">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="6b436-267">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="6b436-268">*Сейчас .NET Core 2.2 ❌ не поддерживается. Дополнительные сведения см. в статье о [политике поддержки .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="6b436-268">*.NET Core 2.2 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="6b436-269">.NET Core 2.2 поддерживает следующие версии Windows:</span><span class="sxs-lookup"><span data-stu-id="6b436-269">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="6b436-270">Символ `+` представляет минимальную версию.</span><span class="sxs-lookup"><span data-stu-id="6b436-270">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6b436-271">Операционная система</span><span class="sxs-lookup"><span data-stu-id="6b436-271">OS</span></span>                            | <span data-ttu-id="6b436-272">Version</span><span class="sxs-lookup"><span data-stu-id="6b436-272">Version</span></span>                        | <span data-ttu-id="6b436-273">Архитектуры</span><span class="sxs-lookup"><span data-stu-id="6b436-273">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="6b436-274">Клиент Windows</span><span class="sxs-lookup"><span data-stu-id="6b436-274">Windows Client</span></span>                | <span data-ttu-id="6b436-275">7 с пакетом обновления 1 и более поздних версий (SP1+), 8.1</span><span class="sxs-lookup"><span data-stu-id="6b436-275">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="6b436-276">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-276">x64, x86</span></span>        |
| <span data-ttu-id="6b436-277">Клиент Windows 10</span><span class="sxs-lookup"><span data-stu-id="6b436-277">Windows 10 Client</span></span>             | <span data-ttu-id="6b436-278">Версия 1607+</span><span class="sxs-lookup"><span data-stu-id="6b436-278">Version 1607+</span></span>                  | <span data-ttu-id="6b436-279">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-279">x64, x86</span></span>        |
| <span data-ttu-id="6b436-280">Windows Server</span><span class="sxs-lookup"><span data-stu-id="6b436-280">Windows Server</span></span>                | <span data-ttu-id="6b436-281">2008 R2 с пакетом обновления 1 или более поздней версии (SP1+)</span><span class="sxs-lookup"><span data-stu-id="6b436-281">2008 R2 SP1+</span></span>                   | <span data-ttu-id="6b436-282">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-282">x64, x86</span></span>        |
| <span data-ttu-id="6b436-283">Nano Server</span><span class="sxs-lookup"><span data-stu-id="6b436-283">Nano Server</span></span>                   | <span data-ttu-id="6b436-284">Версия 1803+</span><span class="sxs-lookup"><span data-stu-id="6b436-284">Version 1803+</span></span>                   | <span data-ttu-id="6b436-285">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6b436-285">x64, ARM32</span></span>      |

<span data-ttu-id="6b436-286">Дополнительные сведения об операционных системах, дистрибутивах и политике жизненного цикла, поддерживаемых .NET Core 2.2, см. в статье [Поддерживаемые .NET Core 2.2 версии ОС](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6b436-286">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="6b436-287">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6b436-287">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="6b436-288">.NET Core 2.1 поддерживает следующие версии Windows:</span><span class="sxs-lookup"><span data-stu-id="6b436-288">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="6b436-289">Символ `+` представляет минимальную версию.</span><span class="sxs-lookup"><span data-stu-id="6b436-289">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6b436-290">Операционная система</span><span class="sxs-lookup"><span data-stu-id="6b436-290">OS</span></span>                            | <span data-ttu-id="6b436-291">Version</span><span class="sxs-lookup"><span data-stu-id="6b436-291">Version</span></span>                        | <span data-ttu-id="6b436-292">Архитектуры</span><span class="sxs-lookup"><span data-stu-id="6b436-292">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="6b436-293">Клиент Windows</span><span class="sxs-lookup"><span data-stu-id="6b436-293">Windows Client</span></span>                | <span data-ttu-id="6b436-294">7 с пакетом обновления 1 и более поздних версий (SP1+), 8.1</span><span class="sxs-lookup"><span data-stu-id="6b436-294">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="6b436-295">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-295">x64, x86</span></span>        |
| <span data-ttu-id="6b436-296">Клиент Windows 10</span><span class="sxs-lookup"><span data-stu-id="6b436-296">Windows 10 Client</span></span>             | <span data-ttu-id="6b436-297">Версия 1607+</span><span class="sxs-lookup"><span data-stu-id="6b436-297">Version 1607+</span></span>                  | <span data-ttu-id="6b436-298">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-298">x64, x86</span></span>        |
| <span data-ttu-id="6b436-299">Windows Server</span><span class="sxs-lookup"><span data-stu-id="6b436-299">Windows Server</span></span>                | <span data-ttu-id="6b436-300">2008 R2 с пакетом обновления 1 или более поздней версии (SP1+)</span><span class="sxs-lookup"><span data-stu-id="6b436-300">2008 R2 SP1+</span></span>                   | <span data-ttu-id="6b436-301">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6b436-301">x64, x86</span></span>        |
| <span data-ttu-id="6b436-302">Nano Server</span><span class="sxs-lookup"><span data-stu-id="6b436-302">Nano Server</span></span>                   | <span data-ttu-id="6b436-303">Версия 1803+</span><span class="sxs-lookup"><span data-stu-id="6b436-303">Version 1803+</span></span>                  | <span data-ttu-id="6b436-304">x64,</span><span class="sxs-lookup"><span data-stu-id="6b436-304">x64,</span></span>            |

<span data-ttu-id="6b436-305">Дополнительные сведения об операционных системах, дистрибутивах и политике жизненного цикла, поддерживаемых .NET Core 2.1, см. в статье [Поддерживаемые .NET Core 2.1 версии ОС](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6b436-305">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

### <a name="offline-install-for-windows-7"></a><span data-ttu-id="6b436-306">Автономная установка для Windows 7</span><span class="sxs-lookup"><span data-stu-id="6b436-306">Offline install for Windows 7</span></span>

<span data-ttu-id="6b436-307">При выполнении автономной установки платформы .NET Core 2.1 в Windows 7 необходимо сначала убедиться, что на целевом компьютере установлена актуальная версия [Центра корневой сертификации Microsoft 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm).</span><span class="sxs-lookup"><span data-stu-id="6b436-307">When doing an offline install for .NET Core 2.1 on Windows 7, you'll first need to make sure that the latest [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) has been installed on the target machine.</span></span>

<span data-ttu-id="6b436-308">Средство _certmgr.exe_ позволяет автоматизировать установку сертификата и его получение из Visual Studio или Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="6b436-308">The _certmgr.exe_ tool can automate installing a certificate and is obtained from Visual Studio or the Windows SDK.</span></span> <span data-ttu-id="6b436-309">Следующая команда используется для установки сертификата перед запуском установщика платформы .NET Core 2.1:</span><span class="sxs-lookup"><span data-stu-id="6b436-309">The following command is used to install the certificate before running the .NET Core 2.1 installer:</span></span>

```console
certmgr.exe /add MicRooCerAut2011_2011_03_22.crt /s /r localMachine root
```

<span data-ttu-id="6b436-310">Обязательно ознакомьтесь с зависимостями ниже, необходимыми для [Windows 7](#additional-deps).</span><span class="sxs-lookup"><span data-stu-id="6b436-310">Be sure to review the dependencies required for [Windows 7 below](#additional-deps).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="6b436-311">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6b436-311">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="6b436-312">При установке пакета SDK для .NET или среды выполнения .NET в следующих версиях Windows требуются дополнительные зависимости:</span><span class="sxs-lookup"><span data-stu-id="6b436-312">More dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

| <span data-ttu-id="6b436-313">Операционная система</span><span class="sxs-lookup"><span data-stu-id="6b436-313">Operating System</span></span>         | <span data-ttu-id="6b436-314">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="6b436-314">Prerequisites</span></span>                                                                    |
|--------------------------|----------------------------------------------------------------------------------|
| <span data-ttu-id="6b436-315">Windows 7 с пакетом обновления 1 (SP1), [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="6b436-315">Windows 7 SP1 [ESU][esu]</span></span> | <span data-ttu-id="6b436-316">– Распространяемый компонент Microsoft Visual C++ 2015–2019, [64-разрядный][vcc64] / [32-разрядный][vcc32]</span><span class="sxs-lookup"><span data-stu-id="6b436-316">- Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> <br> <span data-ttu-id="6b436-317">– Обновление KB3063858, [64-разрядное][kb64] / [32-разрядное][kb32]</span><span class="sxs-lookup"><span data-stu-id="6b436-317">- KB3063858 [64-bit][kb64] / [32-bit][kb32]</span></span> <br> <span data-ttu-id="6b436-318">- [Центр корневой сертификации Microsoft 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) (только удаленный установщик .NET Core 2.1)</span><span class="sxs-lookup"><span data-stu-id="6b436-318">- [Microsoft Root Certificate Authority 2011](https://www.microsoft.com/pkiops/Docs/Repository.htm) (.NET Core 2.1 offline installer only)</span></span> |
| <span data-ttu-id="6b436-319">Windows Vista с пакетом обновления 2 (SP2)</span><span class="sxs-lookup"><span data-stu-id="6b436-319">Windows Vista SP 2</span></span>       | <span data-ttu-id="6b436-320">Распространяемый компонент Microsoft Visual C++ 2015–2019, [64-разрядный][vcc64] / [32-разрядный][vcc32]</span><span class="sxs-lookup"><span data-stu-id="6b436-320">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="6b436-321">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="6b436-321">Windows 8.1</span></span>              | <span data-ttu-id="6b436-322">Распространяемый компонент Microsoft Visual C++ 2015–2019, [64-разрядный][vcc64] / [32-разрядный][vcc32]</span><span class="sxs-lookup"><span data-stu-id="6b436-322">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="6b436-323">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="6b436-323">Windows Server 2008 R2</span></span>   | <span data-ttu-id="6b436-324">Распространяемый компонент Microsoft Visual C++ 2015–2019, [64-разрядный][vcc64] / [32-разрядный][vcc32]</span><span class="sxs-lookup"><span data-stu-id="6b436-324">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |
| <span data-ttu-id="6b436-325">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6b436-325">Windows Server 2012 R2</span></span>   | <span data-ttu-id="6b436-326">Распространяемый компонент Microsoft Visual C++ 2015–2019, [64-разрядный][vcc64] / [32-разрядный][vcc32]</span><span class="sxs-lookup"><span data-stu-id="6b436-326">Microsoft Visual C++ 2015-2019 Redistributable [64-bit][vcc64] / [32-bit][vcc32]</span></span> |

<span data-ttu-id="6b436-327">Приведенные выше требования также применяются, если возникает ошибка, связанная с любой из следующих библиотек DLL:</span><span class="sxs-lookup"><span data-stu-id="6b436-327">The previous requirements are also required if you receive an error related to either of the following dlls:</span></span>

- <span data-ttu-id="6b436-328">*api-ms-win-crt-runtime-l1-1-0.dll*</span><span class="sxs-lookup"><span data-stu-id="6b436-328">*api-ms-win-crt-runtime-l1-1-0.dll*</span></span>
- <span data-ttu-id="6b436-329">*api-ms-win-cor-timezone-l1-1-0.dll*</span><span class="sxs-lookup"><span data-stu-id="6b436-329">*api-ms-win-cor-timezone-l1-1-0.dll*</span></span>
- <span data-ttu-id="6b436-330">*hostfxr.dll*</span><span class="sxs-lookup"><span data-stu-id="6b436-330">*hostfxr.dll*</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="6b436-331">Установка с помощью функции автоматизации PowerShell</span><span class="sxs-lookup"><span data-stu-id="6b436-331">Install with PowerShell automation</span></span>

<span data-ttu-id="6b436-332">[Сценарии dotnet-install](../tools/dotnet-install-script.md) используются для автоматизации непрерывной интеграции и ее осуществления без прав администратора.</span><span class="sxs-lookup"><span data-stu-id="6b436-332">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="6b436-333">Вы можете скачать сценарий со [страницы справочника по сценариям dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="6b436-333">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="6b436-334">Этот сценарий по умолчанию устанавливает последнюю версию [с долгосрочной поддержкой (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core), которой сейчас является .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="6b436-334">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="6b436-335">Вы можете выбрать конкретный выпуск, указав параметр `Channel`.</span><span class="sxs-lookup"><span data-stu-id="6b436-335">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="6b436-336">Включите параметр `Runtime` для установки среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="6b436-336">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="6b436-337">В противном случае сценарий устанавливает пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="6b436-337">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

<span data-ttu-id="6b436-338">Установите пакет SDK, опустив параметр `-Runtime`.</span><span class="sxs-lookup"><span data-stu-id="6b436-338">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="6b436-339">В этом примере для параметра `-Channel` задано значение `Current`, которое определяет установку последней поддерживаемой версии.</span><span class="sxs-lookup"><span data-stu-id="6b436-339">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="6b436-340">Установка с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6b436-340">Install with Visual Studio</span></span>

<span data-ttu-id="6b436-341">Если вы используете Visual Studio для разработки приложений .NET, в следующей таблице указана минимальная требуемая версия Visual Studio на основе целевой версии пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="6b436-341">If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.</span></span>

| <span data-ttu-id="6b436-342">Версия пакета SDK для .NET</span><span class="sxs-lookup"><span data-stu-id="6b436-342">.NET SDK version</span></span>      | <span data-ttu-id="6b436-343">Версия Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6b436-343">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="6b436-344">5,0</span><span class="sxs-lookup"><span data-stu-id="6b436-344">5.0</span></span>                   | <span data-ttu-id="6b436-345">Visual Studio 2019 версии 16.8 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="6b436-345">Visual Studio 2019 version 16.8 or higher.</span></span> |
| <span data-ttu-id="6b436-346">3.1</span><span class="sxs-lookup"><span data-stu-id="6b436-346">3.1</span></span>                   | <span data-ttu-id="6b436-347">Visual Studio 2019 версии 16.4 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="6b436-347">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="6b436-348">3.0</span><span class="sxs-lookup"><span data-stu-id="6b436-348">3.0</span></span>                   | <span data-ttu-id="6b436-349">Visual Studio 2019 версии 16.3 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="6b436-349">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="6b436-350">2.2</span><span class="sxs-lookup"><span data-stu-id="6b436-350">2.2</span></span>                   | <span data-ttu-id="6b436-351">Visual Studio 2017 версии 15.9 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="6b436-351">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="6b436-352">2.1</span><span class="sxs-lookup"><span data-stu-id="6b436-352">2.1</span></span>                   | <span data-ttu-id="6b436-353">Visual Studio 2017 версии 15.7 или более поздней.</span><span class="sxs-lookup"><span data-stu-id="6b436-353">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="6b436-354">Если среда Visual Studio уже установлена, вы можете проверить ее версию, выполнив указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="6b436-354">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="6b436-355">Запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6b436-355">Open Visual Studio.</span></span>
01. <span data-ttu-id="6b436-356">Выберите **Справка** > **О Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="6b436-356">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="6b436-357">Считайте номер версии из диалогового окна **О программе**.</span><span class="sxs-lookup"><span data-stu-id="6b436-357">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="6b436-358">Visual Studio может установить последнюю версию пакета SDK для .NET и среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="6b436-358">Visual Studio can install the latest .NET SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="6b436-359">[Скачайте Visual Studio.](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)</span><span class="sxs-lookup"><span data-stu-id="6b436-359">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="6b436-360">Выбор рабочей нагрузки</span><span class="sxs-lookup"><span data-stu-id="6b436-360">Select a workload</span></span>

<span data-ttu-id="6b436-361">При установке или изменении Visual Studio выберите одну или несколько из следующих рабочих нагрузок в зависимости от типа создаваемого приложения:</span><span class="sxs-lookup"><span data-stu-id="6b436-361">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="6b436-362">рабочая нагрузка **Кроссплатформенная разработка .NET Core** в разделе **Другие наборы инструментов**;</span><span class="sxs-lookup"><span data-stu-id="6b436-362">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="6b436-363">рабочая нагрузка **ASP.NET и разработка веб-приложений** в разделе **Веб-разработка и облако**;</span><span class="sxs-lookup"><span data-stu-id="6b436-363">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="6b436-364">рабочая нагрузка **Разработка для Azure** в разделе **Веб-разработка и облако**;</span><span class="sxs-lookup"><span data-stu-id="6b436-364">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="6b436-365">рабочая нагрузка **Разработка классических приложений .NET** в разделе **Классические и мобильные**.</span><span class="sxs-lookup"><span data-stu-id="6b436-365">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="6b436-366">[![Windows Visual Studio 2019 с рабочей нагрузкой .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="6b436-366">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="6b436-367">Установка вместе с Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6b436-367">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="6b436-368">Visual Studio Code — это эффективный и облегченный редактор исходного кода, который работает на компьютере.</span><span class="sxs-lookup"><span data-stu-id="6b436-368">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="6b436-369">Visual Studio Code доступен для Windows, macOS и Linux.</span><span class="sxs-lookup"><span data-stu-id="6b436-369">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="6b436-370">Хотя Visual Studio Code не поставляется с автоматическим установщиком .NET Core, таким как Visual Studio, добавление поддержки .NET Core не вызывает затруднений.</span><span class="sxs-lookup"><span data-stu-id="6b436-370">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="6b436-371">[Скачайте и установите Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="6b436-371">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="6b436-372">[Скачайте и установите пакет SDK для .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="6b436-372">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="6b436-373">[Установите расширение C# из Marketplace для Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="6b436-373">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="6b436-374">Установщик Windows</span><span class="sxs-lookup"><span data-stu-id="6b436-374">Windows Installer</span></span>

<span data-ttu-id="6b436-375">[Страница загрузки](https://dotnet.microsoft.com/download/dotnet-core) для .NET содержит исполняемые файлы установщика Windows.</span><span class="sxs-lookup"><span data-stu-id="6b436-375">The [download page](https://dotnet.microsoft.com/download/dotnet-core) for .NET provides Windows Installer executables.</span></span>

<span data-ttu-id="6b436-376">При использовании установщиков Windows для установки .NET вы можете указать путь установки, задав параметры `DOTNETHOME_X64` и `DOTNETHOME_X86`.</span><span class="sxs-lookup"><span data-stu-id="6b436-376">When you use the Windows installers to install .NET, you can customize the installation path by setting the `DOTNETHOME_X64` and `DOTNETHOME_X86` parameters:</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

<span data-ttu-id="6b436-377">Для установки .NET в автоматическом режиме, например, в рабочей среде, или для поддержки непрерывной интеграции, используйте следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="6b436-377">If you want to install .NET silently, such as in a production environment or to support continuous integration, use the following switches:</span></span>

- `/install`\
<span data-ttu-id="6b436-378">Устанавливает .NET.</span><span class="sxs-lookup"><span data-stu-id="6b436-378">Installs .NET.</span></span>

- `/quiet`\
<span data-ttu-id="6b436-379">Предотвращает отображение любого пользовательского интерфейса и запросов.</span><span class="sxs-lookup"><span data-stu-id="6b436-379">Prevents any UI and prompts from displaying.</span></span>

- `norestart`\
<span data-ttu-id="6b436-380">Предотвращает все попытки перезапуска.</span><span class="sxs-lookup"><span data-stu-id="6b436-380">Suppresses any attempts to restart.</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe /install /quiet /norestart
```

<span data-ttu-id="6b436-381">Дополнительные сведения смотрите в статье [Параметры командной строки стандартного установщика](/windows/win32/msi/standard-installer-command-line-options).</span><span class="sxs-lookup"><span data-stu-id="6b436-381">For more information, see [Standard Installer Command-Line Options](/windows/win32/msi/standard-installer-command-line-options).</span></span>

> [!TIP]
> <span data-ttu-id="6b436-382">В случае успешной установки установщик возвращает код 0; если требуется перезагрузка, установщик возвращает код 3010.</span><span class="sxs-lookup"><span data-stu-id="6b436-382">The installer returns an exit code of 0 for success and an exit code of 3010 to indicate that a restart is required.</span></span> <span data-ttu-id="6b436-383">Любое другое значение обычно является кодом ошибки.</span><span class="sxs-lookup"><span data-stu-id="6b436-383">Any other value is generally an error code.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="6b436-384">Скачивание и установка вручную</span><span class="sxs-lookup"><span data-stu-id="6b436-384">Download and manually install</span></span>

<span data-ttu-id="6b436-385">В качестве альтернативы установщикам Windows для .NET можно скачать и вручную установить пакет SDK или среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="6b436-385">As an alternative to the Windows installers for .NET, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="6b436-386">Установка вручную как правило выполняется в рамках тестирования непрерывной интеграции.</span><span class="sxs-lookup"><span data-stu-id="6b436-386">Manual install is usually done as part of continuous integration testing.</span></span> <span data-ttu-id="6b436-387">В большинстве случаев разработчикам и пользователям рекомендуется использовать [установщик](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="6b436-387">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="6b436-388">Как пакет SDK для .NET, так и среду выполнения .NET можно установить вручную после скачивания.</span><span class="sxs-lookup"><span data-stu-id="6b436-388">Both .NET SDK and .NET Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="6b436-389">При установке пакета SDK для .NET не нужно устанавливать соответствующую среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="6b436-389">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="6b436-390">Сначала скачайте двоичный выпуск пакета SDK или среды выполнения с одного из следующих сайтов:</span><span class="sxs-lookup"><span data-stu-id="6b436-390">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- [<span data-ttu-id="6b436-391">Скачиваемые файлы для .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="6b436-391">.NET 5.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- [<span data-ttu-id="6b436-392">Скачиваемые файлы для .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6b436-392">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="6b436-393">Скачиваемые файлы для .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6b436-393">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [<span data-ttu-id="6b436-394">Все скачиваемые файлы для .NET Core</span><span class="sxs-lookup"><span data-stu-id="6b436-394">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="6b436-395">Создайте каталог, в который будет выполнено извлечение .NET, например `%USERPROFILE%\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="6b436-395">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="6b436-396">Затем извлеките скачанный ZIP-файл в этот каталог.</span><span class="sxs-lookup"><span data-stu-id="6b436-396">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="6b436-397">По умолчанию команды и приложения .NET CLI не будут использовать платформу .NET, установленную таким образом. Вам нужно выбрать ее явно.</span><span class="sxs-lookup"><span data-stu-id="6b436-397">By default, .NET CLI commands and apps won't use .NET installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="6b436-398">Для этого измените переменные среды, с которыми запускается приложение:</span><span class="sxs-lookup"><span data-stu-id="6b436-398">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="6b436-399">Такой подход позволяет установить несколько версий в отдельные расположения, а затем явно выбрать расположение установки, которое должно использовать приложение, запустив приложение с переменными среды, указывающими на это расположение.</span><span class="sxs-lookup"><span data-stu-id="6b436-399">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="6b436-400">Если параметр `DOTNET_MULTILEVEL_LOOKUP` имеет значение `0`, .NET игнорирует любые установленные глобально версии .NET.</span><span class="sxs-lookup"><span data-stu-id="6b436-400">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET ignores any globally installed .NET version.</span></span> <span data-ttu-id="6b436-401">Если нужно, чтобы платформа .NET учитывала глобальное расположение установки по умолчанию при выборе лучшей платформы для запуска приложения, удалите этот параметр среды.</span><span class="sxs-lookup"><span data-stu-id="6b436-401">Remove that environment setting to let .NET consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="6b436-402">По умолчанию обычно используется каталог `C:\Program Files\dotnet`, в который выполняется установка .NET при использовании установщика.</span><span class="sxs-lookup"><span data-stu-id="6b436-402">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET.</span></span>

## <a name="docker"></a><span data-ttu-id="6b436-403">Docker</span><span class="sxs-lookup"><span data-stu-id="6b436-403">Docker</span></span>

<span data-ttu-id="6b436-404">Контейнеры обеспечивают простой способ изоляции приложения от остальной части основной системы.</span><span class="sxs-lookup"><span data-stu-id="6b436-404">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="6b436-405">Контейнеры на одном компьютере совместно использую только ядро, а также используют ресурсы, которые передаются в приложение.</span><span class="sxs-lookup"><span data-stu-id="6b436-405">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="6b436-406">.NET можно выполнять в контейнере Docker.</span><span class="sxs-lookup"><span data-stu-id="6b436-406">.NET can run in a Docker container.</span></span> <span data-ttu-id="6b436-407">Официальные образы Docker для .NET публикуются в реестре контейнеров Microsoft (MCR), и доступ к ним можно получить в [репозитории Microsoft .NET Docker Hub](https://hub.docker.com/_/microsoft-dotnet).</span><span class="sxs-lookup"><span data-stu-id="6b436-407">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet).</span></span> <span data-ttu-id="6b436-408">Каждый репозиторий содержит рабочие образы для разных сочетаний .NET (пакета SDK или среды выполнения) и операционной системы.</span><span class="sxs-lookup"><span data-stu-id="6b436-408">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="6b436-409">Корпорация Майкрософт предоставляет образы, которые предназначены для конкретных сценариев.</span><span class="sxs-lookup"><span data-stu-id="6b436-409">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="6b436-410">Например [репозиторий ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-aspnet) содержит образы, которые предназначены для запуска приложений ASP.NET Core в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="6b436-410">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="6b436-411">Дополнительные сведения об использовании .NET в контейнере Docker см. в статьях [Введение в .NET и Docker](../docker/introduction.md) и [Примеры](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="6b436-411">For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6b436-412">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="6b436-412">Next steps</span></span>

- <span data-ttu-id="6b436-413">[Проверка того, установлена ли платформа .NET](how-to-detect-installed-versions.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="6b436-413">[How to check if .NET is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="6b436-414">[Учебник. Hello World](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="6b436-414">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="6b436-415">[Учебник. Создание приложения с помощью Visual Studio Code](../tutorials/with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="6b436-415">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="6b436-416">[Учебник. Контейнеризация приложения .NET Core](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="6b436-416">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
[vcc64]: https://aka.ms/vs/16/release/vc_redist.x64.exe
[vcc32]: https://aka.ms/vs/16/release/vc_redist.x86.exe
[kb64]: https://www.microsoft.com/download/details.aspx?id=47442
[kb32]: https://www.microsoft.com/download/details.aspx?id=47409
