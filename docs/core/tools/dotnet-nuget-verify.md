---
title: Команда dotnet nuget verify
description: Команда otnet nuget verify проверяет подписанный пакет.
author: kartheekp-ms
ms.date: 10/08/2020
ms.openlocfilehash: 1c300e5a09b4049a9895b9b3f6c742f701dc2200
ms.sourcegitcommit: 985c603cb21a085f8a8105f34ff5b87a44b76ab4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107564848"
---
# <a name="dotnet-nuget-verify"></a><span data-ttu-id="c3b4b-103">dotnet nuget verify</span><span class="sxs-lookup"><span data-stu-id="c3b4b-103">dotnet nuget verify</span></span>

<span data-ttu-id="c3b4b-104">**Эта статья относится к следующему:** ✔️ пакет SDK для .NET 5.0.100-rc.2.x и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="c3b4b-104">**This article applies to:** ✔️ .NET 5.0.100-rc.2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c3b4b-105">Имя</span><span class="sxs-lookup"><span data-stu-id="c3b4b-105">Name</span></span>

<span data-ttu-id="c3b4b-106">`dotnet nuget verify` — проверяет подписанный пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-106">`dotnet nuget verify` - Verifies a signed NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c3b4b-107">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="c3b4b-107">Synopsis</span></span>

```dotnetcli
dotnet nuget verify [<package-path(s)>]
    [--all]
    [--certificate-fingerprint <FINGERPRINT>]
    [-v|--verbosity <LEVEL>]

dotnet nuget verify -h|--help
```

## <a name="description"></a><span data-ttu-id="c3b4b-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c3b4b-108">Description</span></span>

<span data-ttu-id="c3b4b-109">Команда `dotnet nuget verify` проверяет подписанный пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-109">The `dotnet nuget verify` command verifies a signed NuGet package.</span></span>

## <a name="arguments"></a><span data-ttu-id="c3b4b-110">Аргументы</span><span class="sxs-lookup"><span data-stu-id="c3b4b-110">Arguments</span></span>

- **`package-path(s)`**

  <span data-ttu-id="c3b4b-111">Указывает путь к файлу проверяемого пакета.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-111">Specifies the file path to the package(s) to be verified.</span></span> <span data-ttu-id="c3b4b-112">Для проверки нескольких пакетов можно передать несколько аргументов с расположением.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-112">Multiple position arguments can be passed in to verify multiple packages.</span></span>

## <a name="options"></a><span data-ttu-id="c3b4b-113">Параметры</span><span class="sxs-lookup"><span data-stu-id="c3b4b-113">Options</span></span>

- **`--all`**

  <span data-ttu-id="c3b4b-114">Указывает, что для пакетов нужно выполнить все возможные проверки.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-114">Specifies that all verifications possible should be performed on the package(s).</span></span> <span data-ttu-id="c3b4b-115">По умолчанию проверяются только `signatures`.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-115">By default, only `signatures` are verified.</span></span>

> [!NOTE]
> <span data-ttu-id="c3b4b-116">В настоящее время эта команда поддерживает только проверку `signature`.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-116">This command currently supports only `signature` verification.</span></span>

- **`--certificate-fingerprint <FINGERPRINT>`**

  <span data-ttu-id="c3b4b-117">Убедитесь, что сертификат подписавшего лица совпадает с одним из указанных отпечатков `SHA256`.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-117">Verify that the signer certificate matches with one of the specified `SHA256` fingerprints.</span></span> <span data-ttu-id="c3b4b-118">Этот параметр можно указать несколько раз, чтобы предоставить несколько отпечатков.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-118">This option can be supplied multiple times to provide multiple fingerprints.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c3b4b-119">Задает [уровень детализации MSBuild](/visualstudio/msbuild/obtaining-build-logs-with-msbuild#verbosity-settings).</span><span class="sxs-lookup"><span data-stu-id="c3b4b-119">Sets the [MSBuild verbosity level](/visualstudio/msbuild/obtaining-build-logs-with-msbuild#verbosity-settings).</span></span> <span data-ttu-id="c3b4b-120">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-120">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="c3b4b-121">Значение по умолчанию — `minimal`.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-121">The default is `minimal`.</span></span>

    <span data-ttu-id="c3b4b-122">В следующей таблице показано, что отображается для каждого уровня детализации.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-122">The following table shows what is displayed for each verbosity level.</span></span>

                                      | `q[uiet]` | `m[inimal]` | `n[ormal]` | `d[etailed]` | `diag[nostic]`
    ----------------------------------| --------- | ----------- | ---------- | -----------| --------------
    `Certificate chain Information`   | ❌       | ❌          | ❌         | <span data-ttu-id="c3b4b-123">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-123">✔️</span></span>         | <span data-ttu-id="c3b4b-124">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-124">✔️</span></span>
    `Path to package being verified`  | ❌       | ❌          | <span data-ttu-id="c3b4b-125">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-125">✔️</span></span>         | <span data-ttu-id="c3b4b-126">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-126">✔️</span></span>         | <span data-ttu-id="c3b4b-127">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-127">✔️</span></span>
    `Hashing algorithm used for signature`        | ❌       | ❌          | <span data-ttu-id="c3b4b-128">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-128">✔️</span></span>         | <span data-ttu-id="c3b4b-129">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-129">✔️</span></span>         | <span data-ttu-id="c3b4b-130">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-130">✔️</span></span>
    `Author/Repository Certificate -> SHA1 hash`| ❌       | ❌          | <span data-ttu-id="c3b4b-131">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-131">✔️</span></span>         | <span data-ttu-id="c3b4b-132">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-132">✔️</span></span>         | <span data-ttu-id="c3b4b-133">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-133">✔️</span></span>
    `Author/Repository Certificate -> Issued By`| ❌       | ❌          | <span data-ttu-id="c3b4b-134">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-134">✔️</span></span>         | <span data-ttu-id="c3b4b-135">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-135">✔️</span></span>         | <span data-ttu-id="c3b4b-136">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-136">✔️</span></span>
    `Timestamp Certificate -> Issued By`| ❌       | ❌          | <span data-ttu-id="c3b4b-137">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-137">✔️</span></span>         | <span data-ttu-id="c3b4b-138">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-138">✔️</span></span>         | <span data-ttu-id="c3b4b-139">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-139">✔️</span></span>
    `Timestamp Certificate -> SHA-256 hash`| ❌       | ❌          | <span data-ttu-id="c3b4b-140">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-140">✔️</span></span>         | <span data-ttu-id="c3b4b-141">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-141">✔️</span></span>         | <span data-ttu-id="c3b4b-142">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-142">✔️</span></span>
    `Timestamp Certificate -> Validity period`| ❌       | ❌          | <span data-ttu-id="c3b4b-143">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-143">✔️</span></span>         | <span data-ttu-id="c3b4b-144">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-144">✔️</span></span>         | <span data-ttu-id="c3b4b-145">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-145">✔️</span></span>
    `Timestamp Certificate -> SHA1 hash`| ❌       | ❌          | <span data-ttu-id="c3b4b-146">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-146">✔️</span></span>         | <span data-ttu-id="c3b4b-147">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-147">✔️</span></span>         | <span data-ttu-id="c3b4b-148">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-148">✔️</span></span>
    `Timestamp Certificate -> Subject name`| ❌       | ❌          | <span data-ttu-id="c3b4b-149">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-149">✔️</span></span>         | <span data-ttu-id="c3b4b-150">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-150">✔️</span></span>         | <span data-ttu-id="c3b4b-151">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-151">✔️</span></span>
    `Author/Repository Certificate -> Subject name`| ❌       | <span data-ttu-id="c3b4b-152">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-152">✔️</span></span>          | <span data-ttu-id="c3b4b-153">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-153">✔️</span></span>         | <span data-ttu-id="c3b4b-154">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-154">✔️</span></span>         | <span data-ttu-id="c3b4b-155">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-155">✔️</span></span>
    `Author/Repository Certificate -> SHA-256 hash`| ❌       | <span data-ttu-id="c3b4b-156">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-156">✔️</span></span>          | <span data-ttu-id="c3b4b-157">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-157">✔️</span></span>         | <span data-ttu-id="c3b4b-158">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-158">✔️</span></span>         | <span data-ttu-id="c3b4b-159">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-159">✔️</span></span>
    `Author/Repository Certificate -> Validity period`| ❌       | <span data-ttu-id="c3b4b-160">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-160">✔️</span></span>          | <span data-ttu-id="c3b4b-161">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-161">✔️</span></span>         | <span data-ttu-id="c3b4b-162">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-162">✔️</span></span>         | <span data-ttu-id="c3b4b-163">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-163">✔️</span></span>
    `Author/Repository Certificate -> Service index URL (If applicable)`| ❌       | <span data-ttu-id="c3b4b-164">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-164">✔️</span></span>          | <span data-ttu-id="c3b4b-165">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-165">✔️</span></span>         | <span data-ttu-id="c3b4b-166">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-166">✔️</span></span>         | <span data-ttu-id="c3b4b-167">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-167">✔️</span></span>
    `Package name being verified`                    | ❌       | <span data-ttu-id="c3b4b-168">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-168">✔️</span></span>          | <span data-ttu-id="c3b4b-169">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-169">✔️</span></span>         | <span data-ttu-id="c3b4b-170">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-170">✔️</span></span>         | <span data-ttu-id="c3b4b-171">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-171">✔️</span></span>
    `Type of signature (author or repository)`| ❌       | <span data-ttu-id="c3b4b-172">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-172">✔️</span></span>          | <span data-ttu-id="c3b4b-173">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-173">✔️</span></span>         | <span data-ttu-id="c3b4b-174">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-174">✔️</span></span>         | <span data-ttu-id="c3b4b-175">✔️</span><span class="sxs-lookup"><span data-stu-id="c3b4b-175">✔️</span></span>

    <span data-ttu-id="c3b4b-176">❌ указывает сведения, которые **не отображаются**.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-176">❌ indicates details that are **not** displayed.</span></span> <span data-ttu-id="c3b4b-177">✔️ указывает сведения, которые будут отображаться.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-177">✔️ indicates details that are displayed.</span></span>

* **`-h|--help`**

  <span data-ttu-id="c3b4b-178">Выводит краткую справку по команде.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-178">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="c3b4b-179">Примеры</span><span class="sxs-lookup"><span data-stu-id="c3b4b-179">Examples</span></span>

- <span data-ttu-id="c3b4b-180">Проверка *foo.nupkg*.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-180">Verify *foo.nupkg*:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg
  ```

- <span data-ttu-id="c3b4b-181">Проверка нескольких пакетов NuGet: *foo.nupkg* и *всех файлов .nupkg в указанном каталоге*.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-181">Verify multiple NuGet packages - *foo.nupkg* and *all .nupkg files in the directory specified*:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg c:\mydir\*.nupkg
  ```

- <span data-ttu-id="c3b4b-182">Проверка того, что сигнатура *foo.nupkg* соответствует указанному отпечатку сертификата.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-182">Verify *foo.nupkg* signature matches with the specified certificate fingerprint:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039
  ```

- <span data-ttu-id="c3b4b-183">Проверка того, что сигнатура *foo.nupkg* соответствует одному из указанных отпечатков сертификата.</span><span class="sxs-lookup"><span data-stu-id="c3b4b-183">Verify *foo.nupkg* signature matches with one of the specified certificate fingerprints:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039 --certificate-fingerprint EC10992GG5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E027
  ```
