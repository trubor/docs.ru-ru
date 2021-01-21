---
title: Средство удаления
description: Обзор средства удаления .NET Core — интерактивного средства, позволяющего управлять очисткой пакетов SDK и сред выполнения .NET Core.
author: sfoslund
ms.date: 05/27/2020
ms.openlocfilehash: ed43b4ec8437ae0ccaf5f1234758dda9f16bd51e
ms.sourcegitcommit: 4f5f1855849cb02c3b610c7006ac21d7429f3348
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/15/2021
ms.locfileid: "98235356"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="d6281-103">Средство удаления .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6281-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="d6281-104">[Средство удаления .NET Core](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) позволяет удалять пакеты SDK и среды выполнения .NET Core из системы.</span><span class="sxs-lookup"><span data-stu-id="d6281-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="d6281-105">Указать версии, которые нужно удалить, можно с помощью ряда параметров.</span><span class="sxs-lookup"><span data-stu-id="d6281-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="d6281-106">Это средство поддерживают ОС Windows и macOS.</span><span class="sxs-lookup"><span data-stu-id="d6281-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="d6281-107">ОС Linux сейчас не поддерживает это средство.</span><span class="sxs-lookup"><span data-stu-id="d6281-107">Linux is currently not supported.</span></span>

<span data-ttu-id="d6281-108">В ОС Windows средство может удалять только пакеты SDK и среды выполнения, установленные с помощью одного из следующих установщиков:</span><span class="sxs-lookup"><span data-stu-id="d6281-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="d6281-109">установщик сред выполнения и пакетов SDK для .NET Core;</span><span class="sxs-lookup"><span data-stu-id="d6281-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="d6281-110">установщик Visual Studio более ранних версий, чем Visual Studio 2019 версии 16.3.</span><span class="sxs-lookup"><span data-stu-id="d6281-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="d6281-111">В macOS средство может удалять только пакеты SDK и среды выполнения, расположенные в папке */usr/local/share/dotnet*.</span><span class="sxs-lookup"><span data-stu-id="d6281-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="d6281-112">Из-за этих ограничений средство не сможет удалить все пакеты SDK и среды выполнения .NET Core на компьютере.</span><span class="sxs-lookup"><span data-stu-id="d6281-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="d6281-113">Вы можете использовать команду `dotnet --info`, чтобы найти все установленные пакеты SDK и среды выполнения .NET Core, в том числе те, которые не удается удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d6281-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="d6281-114">Команда `dotnet-core-uninstall list` позволяет просмотреть, какие пакеты SDK можно удалить с помощью средства.</span><span class="sxs-lookup"><span data-stu-id="d6281-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span> <span data-ttu-id="d6281-115">В версии 1.2 и более поздних версиях можно удалять пакеты SDK и среды выполнения с версией 5.0 или более ранней, а в предыдущих версиях средства можно удалить версии 3.1 и более ранние.</span><span class="sxs-lookup"><span data-stu-id="d6281-115">Versions 1.2 and later can uninstall SDKs and runtimes with version 5.0 or earlier, and previous versions of the tool can uninstall 3.1 and earlier.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="d6281-116">Установка средства</span><span class="sxs-lookup"><span data-stu-id="d6281-116">Install the tool</span></span>

<span data-ttu-id="d6281-117">Средство удаления .NET Core можно скачать на [странице со списком выпусков средства](https://aka.ms/dotnet-core-uninstall-tool), а его исходный код доступен в репозитории GitHub [dotnet/cli-lab](https://github.com/dotnet/cli-lab).</span><span class="sxs-lookup"><span data-stu-id="d6281-117">You can download the .NET Core Uninstall Tool from [the tool's releases page](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="d6281-118">Для удаления пакетов SDK и сред выполнения .NET Core средству требуются повышенные права.</span><span class="sxs-lookup"><span data-stu-id="d6281-118">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="d6281-119">Следовательно, его нужно устанавливать в защищенном от записи каталоге, например *C:\Program Files* в ОС Windows или */usr/local/bin* в macOS.</span><span class="sxs-lookup"><span data-stu-id="d6281-119">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="d6281-120">Ознакомьтесь также со статьей [Повышенные права доступа для команд dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="d6281-120">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="d6281-121">Дополнительные сведения см. в [подробных инструкциях по установке](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="d6281-121">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="d6281-122">Запуск программы</span><span class="sxs-lookup"><span data-stu-id="d6281-122">Run the tool</span></span>

<span data-ttu-id="d6281-123">Шаги ниже демонстрируют рекомендуемый подход к работе со средством удаления.</span><span class="sxs-lookup"><span data-stu-id="d6281-123">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="d6281-124">Шаг 1. Отображение установленных пакетов SDK и сред выполнения .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6281-124">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="d6281-125">Шаг 2. Пробный запуск</span><span class="sxs-lookup"><span data-stu-id="d6281-125">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="d6281-126">Шаг 3. Удаление пакетов SDK и сред выполнения .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6281-126">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="d6281-127">Шаг 4. Удаление резервной папки NuGet (необязательный)</span><span class="sxs-lookup"><span data-stu-id="d6281-127">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="d6281-128">Шаг 1. Отображение установленных пакетов SDK и сред выполнения .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6281-128">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="d6281-129">Команда `dotnet-core-uninstall list` перечисляет установленные пакеты SDK и среды выполнения .NET Core, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d6281-129">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="d6281-130">Некоторые пакеты SDK и среды выполнения могут требоваться для работы Visual Studio, и они отображаются с предупреждением о том, почему их не рекомендуется удалять.</span><span class="sxs-lookup"><span data-stu-id="d6281-130">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="d6281-131">В большинстве случаев выходные данные команды `dotnet-core-uninstall list` не будут соответствовать списку установленных версий в выходных данных `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="d6281-131">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="d6281-132">В частности, это средство не будет отображать версии, установленные ZIP-файлами или управляемые Visual Studio (любая версия, установленная с Visual Studio 2019 версии 16.3 или более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="d6281-132">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="d6281-133">Один из способов проверить, находится ли версия под управлением Visual Studio, — просмотреть ее в `Add or Remove Programs`, в которой управляемые версии Visual Studio помечены в отображаемых именах.</span><span class="sxs-lookup"><span data-stu-id="d6281-133">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="d6281-134">**dotnet-core-uninstall list**</span><span class="sxs-lookup"><span data-stu-id="d6281-134">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d6281-135">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="d6281-135">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="d6281-136">Параметры</span><span class="sxs-lookup"><span data-stu-id="d6281-136">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="d6281-137">Windows</span><span class="sxs-lookup"><span data-stu-id="d6281-137">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="d6281-138">Перечисляет все среды выполнения ASP.NET Core, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d6281-138">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="d6281-139">Перечисляет все пакеты размещения .NET Core, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d6281-139">Lists all the .NET Core hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="d6281-140">Перечисляет все среды выполнения .NET Core, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d6281-140">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="d6281-141">Перечисляет все пакеты SDK для .NET Core, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d6281-141">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d6281-142">Устанавливает уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="d6281-142">Sets the verbosity level.</span></span> <span data-ttu-id="d6281-143">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d6281-143">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d6281-144">Значение по умолчанию — `normal`.</span><span class="sxs-lookup"><span data-stu-id="d6281-144">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="d6281-145">Перечисляет все пакеты SDK и среды выполнения .NET Core x64, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d6281-145">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="d6281-146">Перечисляет все пакеты SDK и среды выполнения .NET Core x86, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d6281-146">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="d6281-147">macOS</span><span class="sxs-lookup"><span data-stu-id="d6281-147">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="d6281-148">Перечисляет все среды выполнения .NET Core, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d6281-148">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="d6281-149">Перечисляет все пакеты SDK для .NET Core, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d6281-149">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d6281-150">Устанавливает уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="d6281-150">Sets the verbosity level.</span></span> <span data-ttu-id="d6281-151">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d6281-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d6281-152">Значение по умолчанию — `normal`.</span><span class="sxs-lookup"><span data-stu-id="d6281-152">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="d6281-153">Примеры</span><span class="sxs-lookup"><span data-stu-id="d6281-153">Examples</span></span>

* <span data-ttu-id="d6281-154">Перечисление всех пакетов SDK и сред выполнения .NET Core, которые можно удалить с помощью этого средства:</span><span class="sxs-lookup"><span data-stu-id="d6281-154">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="d6281-155">Перечисление всех пакетов SDK и сред выполнения .NET Core x64:</span><span class="sxs-lookup"><span data-stu-id="d6281-155">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="d6281-156">Перечисление всех пакетов SDK для .NET Core x86:</span><span class="sxs-lookup"><span data-stu-id="d6281-156">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="d6281-157">Шаг 2. Пробный запуск</span><span class="sxs-lookup"><span data-stu-id="d6281-157">Step 2 - Do a dry run</span></span>

<span data-ttu-id="d6281-158">Команды `dotnet-core-uninstall dry-run` и `dotnet-core-uninstall whatif` позволяют просмотреть пакеты SDK и среды выполнения .NET Core, которые будут удалены, на основе указанных параметров без выполнения удаления.</span><span class="sxs-lookup"><span data-stu-id="d6281-158">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="d6281-159">Эти синонимичные команды.</span><span class="sxs-lookup"><span data-stu-id="d6281-159">These commands are synonyms.</span></span>

<span data-ttu-id="d6281-160">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span><span class="sxs-lookup"><span data-stu-id="d6281-160">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d6281-161">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="d6281-161">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="d6281-162">Аргументы</span><span class="sxs-lookup"><span data-stu-id="d6281-162">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="d6281-163">Указанная версия для удаления.</span><span class="sxs-lookup"><span data-stu-id="d6281-163">The specified version to uninstall.</span></span> <span data-ttu-id="d6281-164">Вы можете перечислить несколько версий одну за другой, разделяя их пробелами.</span><span class="sxs-lookup"><span data-stu-id="d6281-164">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="d6281-165">Поддерживаются также файлы ответов.</span><span class="sxs-lookup"><span data-stu-id="d6281-165">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="d6281-166">Файлы ответов можно использовать вместо того, чтобы указывать все версии в командной строке.</span><span class="sxs-lookup"><span data-stu-id="d6281-166">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="d6281-167">Это текстовые файлы, обычно с расширением \*.rsp. Каждая версия указывается в отдельной строке.</span><span class="sxs-lookup"><span data-stu-id="d6281-167">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="d6281-168">Чтобы указать файл ответов для аргумента `VERSION`, используйте символ \@ сразу после имени файла ответа.</span><span class="sxs-lookup"><span data-stu-id="d6281-168">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="d6281-169">Параметры</span><span class="sxs-lookup"><span data-stu-id="d6281-169">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="d6281-170">Windows</span><span class="sxs-lookup"><span data-stu-id="d6281-170">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="d6281-171">Удаляет все пакеты SDK и среды выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-171">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="d6281-172">Удаляет только пакеты SDK и среды .NET Core, версия которых вышла раньше, чем указанная.</span><span class="sxs-lookup"><span data-stu-id="d6281-172">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="d6281-173">Указанная версия не удаляется.</span><span class="sxs-lookup"><span data-stu-id="d6281-173">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="d6281-174">Удаляет все пакеты SDK и среды выполнения .NET Core, за исключением указанных версий.</span><span class="sxs-lookup"><span data-stu-id="d6281-174">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="d6281-175">Удаляет пакеты SDK и среды выполнения .NET Core, за исключением самых поздних версий.</span><span class="sxs-lookup"><span data-stu-id="d6281-175">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="d6281-176">Удаляет пакеты SDK и среды выполнения .NET Core, замененные более поздними исправлениями.</span><span class="sxs-lookup"><span data-stu-id="d6281-176">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="d6281-177">Этот параметр обеспечивает защиту файла global.json.</span><span class="sxs-lookup"><span data-stu-id="d6281-177">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="d6281-178">Удаляет пакеты SDK и среды выполнения .NET Core, помеченные как предварительные версии.</span><span class="sxs-lookup"><span data-stu-id="d6281-178">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="d6281-179">Удаляет пакеты SDK и среды выполнения .NET Core, помеченные как предварительные версии, за исключением самых поздних.</span><span class="sxs-lookup"><span data-stu-id="d6281-179">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="d6281-180">Удаляет только среды выполнения ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-180">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="d6281-181">Удаляет только среду выполнения и пакеты размещения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-181">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="d6281-182">Удаляет пакеты SDK и среды выполнения .NET Core, соответствующие указанной версии `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="d6281-182">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="d6281-183">Удаляет только среды выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-183">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="d6281-184">Удаляет только пакеты SDK для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-184">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d6281-185">Устанавливает уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="d6281-185">Sets the verbosity level.</span></span> <span data-ttu-id="d6281-186">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d6281-186">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d6281-187">Значение по умолчанию — `normal`.</span><span class="sxs-lookup"><span data-stu-id="d6281-187">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="d6281-188">Необходимо использовать с `--sdk`, `--runtime` и `--aspnet-runtime` для удаления пакетов SDK или сред выполнения x64.</span><span class="sxs-lookup"><span data-stu-id="d6281-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="d6281-189">Необходимо использовать с `--sdk`, `--runtime` и `--aspnet-runtime` для удаления пакетов SDK или сред выполнения x86.</span><span class="sxs-lookup"><span data-stu-id="d6281-189">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="d6281-190">**`--force`** Принудительно удаляет версии, которые могут использоваться в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d6281-190">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="d6281-191">Примечания.</span><span class="sxs-lookup"><span data-stu-id="d6281-191">Notes:</span></span>

1. <span data-ttu-id="d6281-192">Требуется только один из параметров `--sdk`, `--runtime`, `--aspnet-runtime` или `--hosting-bundle`.</span><span class="sxs-lookup"><span data-stu-id="d6281-192">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="d6281-193">Параметры `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor` и `[<VERSION>...]` служат для исключения.</span><span class="sxs-lookup"><span data-stu-id="d6281-193">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="d6281-194">Если `--x64` или `--x86` не указаны, будут удалены обе версии.</span><span class="sxs-lookup"><span data-stu-id="d6281-194">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="d6281-195">macOS</span><span class="sxs-lookup"><span data-stu-id="d6281-195">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="d6281-196">Удаляет все пакеты SDK и среды выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-196">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="d6281-197">Удаляет пакеты SDK и среды выполнения .NET Core, версия которых вышла ранее, чем указанная.</span><span class="sxs-lookup"><span data-stu-id="d6281-197">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="d6281-198">Указанная версия не будет удалена.</span><span class="sxs-lookup"><span data-stu-id="d6281-198">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="d6281-199">Удаляет пакеты SDK и среды выполнения .NET Core, за исключением указанных версий.</span><span class="sxs-lookup"><span data-stu-id="d6281-199">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="d6281-200">Удаляет пакеты SDK и среды выполнения .NET Core, за исключением самых поздних версий.</span><span class="sxs-lookup"><span data-stu-id="d6281-200">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="d6281-201">Удаляет пакеты SDK и среды выполнения .NET Core, замененные более поздними исправлениями.</span><span class="sxs-lookup"><span data-stu-id="d6281-201">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="d6281-202">Этот параметр обеспечивает защиту файла global.json.</span><span class="sxs-lookup"><span data-stu-id="d6281-202">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="d6281-203">Удаляет пакеты SDK и среды выполнения .NET Core, помеченные как предварительные версии.</span><span class="sxs-lookup"><span data-stu-id="d6281-203">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="d6281-204">Удаляет пакеты SDK и среды выполнения .NET Core, помеченные как предварительные версии, за исключением самых поздних.</span><span class="sxs-lookup"><span data-stu-id="d6281-204">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="d6281-205">Удаляет пакеты SDK и среды выполнения .NET Core, соответствующие указанной версии `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="d6281-205">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="d6281-206">Удаляет только среды выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-206">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="d6281-207">Удаляет только пакеты SDK для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-207">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d6281-208">Устанавливает уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="d6281-208">Sets the verbosity level.</span></span> <span data-ttu-id="d6281-209">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d6281-209">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d6281-210">Значение по умолчанию — `normal`.</span><span class="sxs-lookup"><span data-stu-id="d6281-210">The default value is `normal`.</span></span>
  
* <span data-ttu-id="d6281-211">**`--force`** Принудительно удаляет версии, которые могут использоваться Visual Studio или пакетами SDK.</span><span class="sxs-lookup"><span data-stu-id="d6281-211">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="d6281-212">Примечания.</span><span class="sxs-lookup"><span data-stu-id="d6281-212">Notes:</span></span>

1. <span data-ttu-id="d6281-213">Требуется указать только один параметр: `--sdk` или `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="d6281-213">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="d6281-214">Параметры `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor` и `[<VERSION>...]` служат для исключения.</span><span class="sxs-lookup"><span data-stu-id="d6281-214">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="d6281-215">Примеры</span><span class="sxs-lookup"><span data-stu-id="d6281-215">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="d6281-216">По умолчанию пакеты SDK и среды выполнения .NET Core, которые могут требоваться для работы Visual Studio или других пакетов SDK, не включаются в выходные данные `dotnet-core-uninstall dry-run`.</span><span class="sxs-lookup"><span data-stu-id="d6281-216">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="d6281-217">В примерах ниже некоторые указанные пакеты SDK и среды выполнения могут быть исключены из выходных данных в зависимости от состояния компьютера.</span><span class="sxs-lookup"><span data-stu-id="d6281-217">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="d6281-218">Чтобы включить все пакеты SDK и среды выполнения, укажите их явно в качестве аргументов или используйте параметр `--force`.</span><span class="sxs-lookup"><span data-stu-id="d6281-218">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="d6281-219">Пробный запуск удаления всех сред выполнения .NET Core, замененных более поздними версиями:</span><span class="sxs-lookup"><span data-stu-id="d6281-219">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="d6281-220">Пробный запуск удаления всех пакетов SDK для .NET Core, версия которых вышла раньше `2.2.301`:</span><span class="sxs-lookup"><span data-stu-id="d6281-220">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="d6281-221">Шаг 3. Удаление пакетов SDK и сред выполнения .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6281-221">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="d6281-222">Команда `dotnet-core-uninstall remove` удаляет пакеты SDK и среды выполнения .NET Core, указанные с использованием коллекции параметров.</span><span class="sxs-lookup"><span data-stu-id="d6281-222">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="d6281-223">В версии 1.2 и более поздних версиях можно удалять пакеты SDK и среды выполнения с версией 5.0 или более ранней, а в предыдущих версиях средства можно удалить версии 3.1 и более ранние.</span><span class="sxs-lookup"><span data-stu-id="d6281-223">Versions 1.2 and later can uninstall SDKs and runtimes with version 5.0 or earlier, and previous versions of the tool can uninstall 3.1 and earlier.</span></span>

<span data-ttu-id="d6281-224">У средства разрушающее поведение, поэтому **настоятельно** рекомендуется выполнять пробный запуск перед выполнением команды удаления.</span><span class="sxs-lookup"><span data-stu-id="d6281-224">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="d6281-225">В ходе пробного запуска будут показаны пакеты SDK и среды .NET Core, подлежащие удалению при использовании команды `remove`.</span><span class="sxs-lookup"><span data-stu-id="d6281-225">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="d6281-226">Чтобы узнать, какие пакеты SDK и среды выполнения безопасно удалять, обратитесь к разделу [Нужно ли удалять версию](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version).</span><span class="sxs-lookup"><span data-stu-id="d6281-226">Refer to [Should I remove a version?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="d6281-227">Учитывайте следующие факторы.</span><span class="sxs-lookup"><span data-stu-id="d6281-227">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="d6281-228">Это средство может удалять версии пакета SDK для .NET Core, необходимые для файлов `global.json` на компьютере.</span><span class="sxs-lookup"><span data-stu-id="d6281-228">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="d6281-229">Эти пакеты можно повторно установить, предварительно скачав их на [этой странице](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="d6281-229">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="d6281-230">Средство может удалять версии среды выполнения .NET Core, необходимые для зависимых от платформы приложений на компьютере.</span><span class="sxs-lookup"><span data-stu-id="d6281-230">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="d6281-231">Вы можете переустановить среду выполнения .NET Core, предварительно скачав ее с [этой страницы](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="d6281-231">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="d6281-232">Это средство может удалять версии пакета SDK и среды выполнения .NET Core, от которых зависит работа Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d6281-232">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="d6281-233">Если нарушите работу установленной версии Visual Studio, выполните команду "Исправить" в установщике Visual Studio, чтобы восстановить рабочее состояние.</span><span class="sxs-lookup"><span data-stu-id="d6281-233">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="d6281-234">По умолчанию все команды поддерживают пакеты SDK и среды выполнения .NET Core, которые могут потребоваться для работы Visual Studio или других пакетов SDK.</span><span class="sxs-lookup"><span data-stu-id="d6281-234">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="d6281-235">Эти пакеты и среды выполнения можно удалить путем их явного перечисления в виде аргументов или с использованием параметра `--force`.</span><span class="sxs-lookup"><span data-stu-id="d6281-235">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="d6281-236">Для удаления пакетов SDK и сред выполнения .NET Core средству требуются повышенные права.</span><span class="sxs-lookup"><span data-stu-id="d6281-236">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="d6281-237">Запустите средство в командной строке администратора в ОС Windows или с помощью команды `sudo` в macOS.</span><span class="sxs-lookup"><span data-stu-id="d6281-237">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="d6281-238">Для команд `dry-run` и `whatif` повышение прав не требуется.</span><span class="sxs-lookup"><span data-stu-id="d6281-238">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="d6281-239">**dotnet-core-uninstall remove**</span><span class="sxs-lookup"><span data-stu-id="d6281-239">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d6281-240">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="d6281-240">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="d6281-241">Аргументы</span><span class="sxs-lookup"><span data-stu-id="d6281-241">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="d6281-242">Указанная версия для удаления.</span><span class="sxs-lookup"><span data-stu-id="d6281-242">The specified version to uninstall.</span></span> <span data-ttu-id="d6281-243">Вы можете перечислить несколько версий одну за другой, разделяя их пробелами.</span><span class="sxs-lookup"><span data-stu-id="d6281-243">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="d6281-244">Поддерживаются также файлы ответов.</span><span class="sxs-lookup"><span data-stu-id="d6281-244">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="d6281-245">Файлы ответов можно использовать вместо того, чтобы указывать все версии в командной строке.</span><span class="sxs-lookup"><span data-stu-id="d6281-245">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="d6281-246">Это текстовые файлы, обычно с расширением \*.rsp. Каждая версия указывается в отдельной строке.</span><span class="sxs-lookup"><span data-stu-id="d6281-246">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="d6281-247">Чтобы указать файл ответов для аргумента `VERSION`, используйте символ \@ сразу после имени файла ответа.</span><span class="sxs-lookup"><span data-stu-id="d6281-247">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="d6281-248">Параметры</span><span class="sxs-lookup"><span data-stu-id="d6281-248">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="d6281-249">Windows</span><span class="sxs-lookup"><span data-stu-id="d6281-249">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="d6281-250">Удаляет все пакеты SDK и среды выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-250">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="d6281-251">Удаляет только пакеты SDK и среды .NET Core, версия которых вышла раньше, чем указанная.</span><span class="sxs-lookup"><span data-stu-id="d6281-251">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="d6281-252">Указанная версия не удаляется.</span><span class="sxs-lookup"><span data-stu-id="d6281-252">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="d6281-253">Удаляет все пакеты SDK и среды выполнения .NET Core, за исключением указанных версий.</span><span class="sxs-lookup"><span data-stu-id="d6281-253">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="d6281-254">Удаляет пакеты SDK и среды выполнения .NET Core, за исключением самых поздних версий.</span><span class="sxs-lookup"><span data-stu-id="d6281-254">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="d6281-255">Удаляет пакеты SDK и среды выполнения .NET Core, замененные более поздними исправлениями.</span><span class="sxs-lookup"><span data-stu-id="d6281-255">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="d6281-256">Этот параметр обеспечивает защиту файла global.json.</span><span class="sxs-lookup"><span data-stu-id="d6281-256">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="d6281-257">Удаляет пакеты SDK и среды выполнения .NET Core, помеченные как предварительные версии.</span><span class="sxs-lookup"><span data-stu-id="d6281-257">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="d6281-258">Удаляет пакеты SDK и среды выполнения .NET Core, помеченные как предварительные версии, за исключением самых поздних.</span><span class="sxs-lookup"><span data-stu-id="d6281-258">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="d6281-259">Удаляет только среды выполнения ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-259">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="d6281-260">Удаляет только пакеты размещения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-260">Removes .NET Core hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="d6281-261">Удаляет пакеты SDK и среды выполнения .NET Core, соответствующие указанной версии `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="d6281-261">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="d6281-262">Удаляет только среды выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-262">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="d6281-263">Удаляет только пакеты SDK для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-263">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d6281-264">Устанавливает уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="d6281-264">Sets the verbosity level.</span></span> <span data-ttu-id="d6281-265">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d6281-265">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d6281-266">Значение по умолчанию — `normal`.</span><span class="sxs-lookup"><span data-stu-id="d6281-266">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="d6281-267">Необходимо использовать с `--sdk`, `--runtime` и `--aspnet-runtime` для удаления пакетов SDK или сред выполнения x64.</span><span class="sxs-lookup"><span data-stu-id="d6281-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="d6281-268">Необходимо использовать с `--sdk`, `--runtime` и `--aspnet-runtime` для удаления пакетов SDK или сред выполнения x86.</span><span class="sxs-lookup"><span data-stu-id="d6281-268">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="d6281-269">**`-y, --yes`** Выполняет команду без подтверждения Yes или No.</span><span class="sxs-lookup"><span data-stu-id="d6281-269">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="d6281-270">**`--force`** Принудительно удаляет версии, которые могут использоваться в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d6281-270">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="d6281-271">Примечания.</span><span class="sxs-lookup"><span data-stu-id="d6281-271">Notes:</span></span>

1. <span data-ttu-id="d6281-272">Требуется только один из параметров `--sdk`, `--runtime`, `--aspnet-runtime` или `--hosting-bundle`.</span><span class="sxs-lookup"><span data-stu-id="d6281-272">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="d6281-273">Параметры `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor` и `[<VERSION>...]` служат для исключения.</span><span class="sxs-lookup"><span data-stu-id="d6281-273">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="d6281-274">Если `--x64` или `--x86` не указаны, будут удалены обе версии.</span><span class="sxs-lookup"><span data-stu-id="d6281-274">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="d6281-275">macOS</span><span class="sxs-lookup"><span data-stu-id="d6281-275">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="d6281-276">Удаляет все пакеты SDK и среды выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-276">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="d6281-277">Удаляет пакеты SDK и среды выполнения .NET Core, версия которых вышла ранее, чем указанная.</span><span class="sxs-lookup"><span data-stu-id="d6281-277">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="d6281-278">Указанная версия не будет удалена.</span><span class="sxs-lookup"><span data-stu-id="d6281-278">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="d6281-279">Удаляет пакеты SDK и среды выполнения .NET Core, за исключением указанных версий.</span><span class="sxs-lookup"><span data-stu-id="d6281-279">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="d6281-280">Удаляет пакеты SDK и среды выполнения .NET Core, за исключением самых поздних версий.</span><span class="sxs-lookup"><span data-stu-id="d6281-280">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="d6281-281">Удаляет пакеты SDK и среды выполнения .NET Core, замененные более поздними исправлениями.</span><span class="sxs-lookup"><span data-stu-id="d6281-281">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="d6281-282">Этот параметр обеспечивает защиту файла global.json.</span><span class="sxs-lookup"><span data-stu-id="d6281-282">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="d6281-283">Удаляет пакеты SDK и среды выполнения .NET Core, помеченные как предварительные версии.</span><span class="sxs-lookup"><span data-stu-id="d6281-283">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="d6281-284">Удаляет пакеты SDK и среды выполнения .NET Core, помеченные как предварительные версии, за исключением самых поздних.</span><span class="sxs-lookup"><span data-stu-id="d6281-284">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="d6281-285">Удаляет пакеты SDK и среды выполнения .NET Core, соответствующие указанной версии `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="d6281-285">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="d6281-286">Удаляет только среды выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-286">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="d6281-287">Удаляет только пакеты SDK для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6281-287">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d6281-288">Устанавливает уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="d6281-288">Sets the verbosity level.</span></span> <span data-ttu-id="d6281-289">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d6281-289">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d6281-290">Значение по умолчанию — `normal`.</span><span class="sxs-lookup"><span data-stu-id="d6281-290">The default value is `normal`.</span></span>

* <span data-ttu-id="d6281-291">**`-y, --yes`** Выполняет команду без подтверждения Yes или No.</span><span class="sxs-lookup"><span data-stu-id="d6281-291">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="d6281-292">**`--force`** Принудительно удаляет версии, которые могут использоваться Visual Studio или пакетами SDK.</span><span class="sxs-lookup"><span data-stu-id="d6281-292">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="d6281-293">Примечания.</span><span class="sxs-lookup"><span data-stu-id="d6281-293">Notes:</span></span>

1. <span data-ttu-id="d6281-294">Требуется указать только один параметр: `--sdk` или `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="d6281-294">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="d6281-295">Параметры `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor` и `[<VERSION>...]` служат для исключения.</span><span class="sxs-lookup"><span data-stu-id="d6281-295">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="d6281-296">Примеры</span><span class="sxs-lookup"><span data-stu-id="d6281-296">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="d6281-297">По умолчанию пакеты SDK и среды выполнения .NET Core, которые могут требоваться для работы Visual Studio или других пакетов SDK, сохраняются.</span><span class="sxs-lookup"><span data-stu-id="d6281-297">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="d6281-298">В примерах ниже могут остаться некоторые из указанных пакетов SDK и сред выполнения в зависимости от состояния компьютера.</span><span class="sxs-lookup"><span data-stu-id="d6281-298">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="d6281-299">Чтобы удалить все пакеты и среды выполнения, укажите их явно в качестве аргументов или используйте параметр `--force`.</span><span class="sxs-lookup"><span data-stu-id="d6281-299">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="d6281-300">Удаление всех сред выполнения .NET Core, кроме версии `3.0.0-preview6-27804-01` без подтверждения Yes или No:</span><span class="sxs-lookup"><span data-stu-id="d6281-300">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="d6281-301">Удаление всех пакетов SDK для .NET Core 1.1 без подтверждения Yes или No:</span><span class="sxs-lookup"><span data-stu-id="d6281-301">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="d6281-302">Удаление пакета SDK для .NET Core 1.1.11 без вывода на консоль:</span><span class="sxs-lookup"><span data-stu-id="d6281-302">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="d6281-303">Удаление всех пакетов SDK для .NET Core, которые можно безопасно удалить с помощью этого средства:</span><span class="sxs-lookup"><span data-stu-id="d6281-303">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="d6281-304">Удаление всех пакетов SDK для .NET Core, которые можно безопасно удалить с помощью этого средства, в том числе тех, которые могут требоваться для работы Visual Studio (не рекомендуется):</span><span class="sxs-lookup"><span data-stu-id="d6281-304">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="d6281-305">Удаление всех пакетов SDK для .NET Core, указанных в файле ответов `versions.rsp`:</span><span class="sxs-lookup"><span data-stu-id="d6281-305">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="d6281-306">В файле *versions.rsp* содержится следующее:</span><span class="sxs-lookup"><span data-stu-id="d6281-306">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="d6281-307">Шаг 4. Удаление резервной папки NuGet (необязательный)</span><span class="sxs-lookup"><span data-stu-id="d6281-307">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="d6281-308">В некоторых случаях папка `NuGetFallbackFolder` может больше не требоваться, и ее понадобится удалить.</span><span class="sxs-lookup"><span data-stu-id="d6281-308">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="d6281-309">Дополнительные сведения об удалении папки NuGetFallbackFolder см. в [этом разделе](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="d6281-309">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="d6281-310">Удаление средства</span><span class="sxs-lookup"><span data-stu-id="d6281-310">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="d6281-311">Windows</span><span class="sxs-lookup"><span data-stu-id="d6281-311">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="d6281-312">Откройте окно **Установка и удаление программ**.</span><span class="sxs-lookup"><span data-stu-id="d6281-312">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="d6281-313">Найдите `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="d6281-313">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="d6281-314">Выберите **Удалить**.</span><span class="sxs-lookup"><span data-stu-id="d6281-314">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="d6281-315">macOS</span><span class="sxs-lookup"><span data-stu-id="d6281-315">macOS</span></span>](#tab/macos)

<span data-ttu-id="d6281-316">Удалите скачанный файл *dotnet-core-uninstall.tar.gz* из каталога, в котором он установлен.</span><span class="sxs-lookup"><span data-stu-id="d6281-316">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="d6281-317">Если содержимое этого файла распаковано в другой каталог, необходимо также удалить это содержимое.</span><span class="sxs-lookup"><span data-stu-id="d6281-317">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
