---
title: Средство удаления
description: Обзор средства удаления .NET — интерактивного средства, позволяющего управлять очисткой пакетов SDK и сред выполнения .NET.
author: sfoslund
ms.date: 01/28/2021
ms.openlocfilehash: 9afcac150659a8f58a04f4c254b0a0219af42e74
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105438"
---
# <a name="net-uninstall-tool"></a><span data-ttu-id="d0b84-103">Средство удаления .NET</span><span class="sxs-lookup"><span data-stu-id="d0b84-103">.NET Uninstall Tool</span></span>

<span data-ttu-id="d0b84-104">[Средство удаления .NET](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) позволяет удалять пакеты SDK и среды выполнения .NET из системы.</span><span class="sxs-lookup"><span data-stu-id="d0b84-104">The [.NET Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET SDKs and Runtimes from a system.</span></span> <span data-ttu-id="d0b84-105">Указать версии, которые нужно удалить, можно с помощью ряда параметров.</span><span class="sxs-lookup"><span data-stu-id="d0b84-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="d0b84-106">Это средство поддерживают ОС Windows и macOS.</span><span class="sxs-lookup"><span data-stu-id="d0b84-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="d0b84-107">ОС Linux сейчас не поддерживает это средство.</span><span class="sxs-lookup"><span data-stu-id="d0b84-107">Linux is currently not supported.</span></span>

<span data-ttu-id="d0b84-108">В ОС Windows средство может удалять только пакеты SDK и среды выполнения, установленные с помощью одного из следующих установщиков:</span><span class="sxs-lookup"><span data-stu-id="d0b84-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="d0b84-109">установщик сред выполнения и пакетов SDK для .NET;</span><span class="sxs-lookup"><span data-stu-id="d0b84-109">The .NET SDK and runtime installer.</span></span>
- <span data-ttu-id="d0b84-110">установщик Visual Studio более ранних версий, чем Visual Studio 2019 версии 16.3.</span><span class="sxs-lookup"><span data-stu-id="d0b84-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="d0b84-111">В macOS средство может удалять только пакеты SDK и среды выполнения, расположенные в папке */usr/local/share/dotnet*.</span><span class="sxs-lookup"><span data-stu-id="d0b84-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="d0b84-112">Из-за этих ограничений средство не сможет удалить все пакеты SDK и среды выполнения .NET на компьютере.</span><span class="sxs-lookup"><span data-stu-id="d0b84-112">Because of these limitations, the tool may not be able to uninstall all of the .NET SDKs and runtimes on your machine.</span></span> <span data-ttu-id="d0b84-113">Вы можете использовать команду `dotnet --info`, чтобы найти все установленные пакеты SDK и среды выполнения .NET, в том числе те, которые не удается удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d0b84-113">You can use the `dotnet --info` command to find all of the .NET SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="d0b84-114">Команда `dotnet-core-uninstall list` позволяет просмотреть, какие пакеты SDK можно удалить с помощью средства.</span><span class="sxs-lookup"><span data-stu-id="d0b84-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span> <span data-ttu-id="d0b84-115">В версии 1.2 и более поздних версиях можно удалять пакеты SDK и среды выполнения с версией 5.0 или более ранней, а в предыдущих версиях средства можно удалить версии 3.1 и более ранние.</span><span class="sxs-lookup"><span data-stu-id="d0b84-115">Versions 1.2 and later can uninstall SDKs and runtimes with version 5.0 or earlier, and previous versions of the tool can uninstall 3.1 and earlier.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="d0b84-116">Установка средства</span><span class="sxs-lookup"><span data-stu-id="d0b84-116">Install the tool</span></span>

<span data-ttu-id="d0b84-117">Средство удаления .NET можно скачать на [странице со списком выпусков средства](https://aka.ms/dotnet-core-uninstall-tool), а его исходный код доступен в репозитории GitHub [dotnet/cli-lab](https://github.com/dotnet/cli-lab).</span><span class="sxs-lookup"><span data-stu-id="d0b84-117">You can download the .NET Uninstall Tool from [the tool's releases page](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="d0b84-118">Для удаления пакетов SDK и сред выполнения .NET средству требуются повышенные права.</span><span class="sxs-lookup"><span data-stu-id="d0b84-118">The tool requires elevation to uninstall .NET SDKs and runtimes.</span></span> <span data-ttu-id="d0b84-119">Следовательно, его нужно устанавливать в защищенном от записи каталоге, например *C:\Program Files* в ОС Windows или */usr/local/bin* в macOS.</span><span class="sxs-lookup"><span data-stu-id="d0b84-119">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="d0b84-120">Ознакомьтесь также со статьей [Повышенные права доступа для команд dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="d0b84-120">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="d0b84-121">Дополнительные сведения см. в [подробных инструкциях по установке](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="d0b84-121">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="d0b84-122">Запуск программы</span><span class="sxs-lookup"><span data-stu-id="d0b84-122">Run the tool</span></span>

<span data-ttu-id="d0b84-123">Шаги ниже демонстрируют рекомендуемый подход к работе со средством удаления.</span><span class="sxs-lookup"><span data-stu-id="d0b84-123">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="d0b84-124">Шаг 1. Отображение установленных пакетов SDK и сред выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="d0b84-124">Step 1 - Display installed .NET SDKs and runtimes</span></span>](#step-1---display-installed-net-sdks-and-runtimes)
- [<span data-ttu-id="d0b84-125">Шаг 2. Пробный запуск</span><span class="sxs-lookup"><span data-stu-id="d0b84-125">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="d0b84-126">Шаг 3. Удаление пакетов SDK и сред выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="d0b84-126">Step 3 - Uninstall .NET SDKs and Runtimes</span></span>](#step-3---uninstall-net-sdks-and-runtimes)
- [<span data-ttu-id="d0b84-127">Шаг 4. Удаление резервной папки NuGet (необязательный)</span><span class="sxs-lookup"><span data-stu-id="d0b84-127">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-sdks-and-runtimes"></a><span data-ttu-id="d0b84-128">Шаг 1. Отображение установленных пакетов SDK и сред выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="d0b84-128">Step 1 - Display installed .NET SDKs and runtimes</span></span>

<span data-ttu-id="d0b84-129">Команда `dotnet-core-uninstall list` перечисляет установленные пакеты SDK и среды выполнения .NET, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d0b84-129">The `dotnet-core-uninstall list` command lists the installed .NET SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="d0b84-130">Некоторые пакеты SDK и среды выполнения могут требоваться для работы Visual Studio, и они отображаются с предупреждением о том, почему их не рекомендуется удалять.</span><span class="sxs-lookup"><span data-stu-id="d0b84-130">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="d0b84-131">В большинстве случаев выходные данные команды `dotnet-core-uninstall list` не будут соответствовать списку установленных версий в выходных данных `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-131">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="d0b84-132">В частности, это средство не будет отображать версии, установленные ZIP-файлами или управляемые Visual Studio (любая версия, установленная с Visual Studio 2019 версии 16.3 или более поздней версии).</span><span class="sxs-lookup"><span data-stu-id="d0b84-132">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="d0b84-133">Один из способов проверить, находится ли версия под управлением Visual Studio, — просмотреть ее в `Add or Remove Programs`, в которой управляемые версии Visual Studio помечены в отображаемых именах.</span><span class="sxs-lookup"><span data-stu-id="d0b84-133">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="d0b84-134">**dotnet-core-uninstall list**</span><span class="sxs-lookup"><span data-stu-id="d0b84-134">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d0b84-135">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="d0b84-135">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="d0b84-136">Параметры</span><span class="sxs-lookup"><span data-stu-id="d0b84-136">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="d0b84-137">Windows</span><span class="sxs-lookup"><span data-stu-id="d0b84-137">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="d0b84-138">Перечисляет все среды выполнения ASP.NET, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d0b84-138">Lists all the ASP.NET Runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="d0b84-139">Перечисляет все пакеты размещения .NET, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d0b84-139">Lists all the .NET hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="d0b84-140">Перечисляет все среды выполнения .NET, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d0b84-140">Lists all .NET Runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="d0b84-141">Перечисляет все пакеты SDK для .NET, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d0b84-141">Lists all .NET SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d0b84-142">Устанавливает уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="d0b84-142">Sets the verbosity level.</span></span> <span data-ttu-id="d0b84-143">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-143">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d0b84-144">Значение по умолчанию — `normal`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-144">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="d0b84-145">Перечисляет все пакеты SDK и среды выполнения .NET x64, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d0b84-145">Lists all x64 .NET SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="d0b84-146">Перечисляет все пакеты SDK и среды выполнения .NET x86, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d0b84-146">Lists all x86 .NET SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="d0b84-147">macOS</span><span class="sxs-lookup"><span data-stu-id="d0b84-147">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="d0b84-148">Перечисляет все среды выполнения .NET, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d0b84-148">Lists all .NET Runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="d0b84-149">Перечисляет все пакеты SDK для .NET, которые можно удалить с помощью этого средства.</span><span class="sxs-lookup"><span data-stu-id="d0b84-149">Lists all .NET SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d0b84-150">Устанавливает уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="d0b84-150">Sets the verbosity level.</span></span> <span data-ttu-id="d0b84-151">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d0b84-152">Значение по умолчанию — `normal`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-152">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="d0b84-153">Примеры</span><span class="sxs-lookup"><span data-stu-id="d0b84-153">Examples</span></span>

* <span data-ttu-id="d0b84-154">Перечисление всех пакетов SDK и сред выполнения .NET, которые можно удалить с помощью этого средства:</span><span class="sxs-lookup"><span data-stu-id="d0b84-154">List all .NET SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="d0b84-155">Перечисление всех пакетов SDK и сред выполнения .NET x64:</span><span class="sxs-lookup"><span data-stu-id="d0b84-155">List all x64 .NET SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="d0b84-156">Перечисление всех пакетов SDK для .NET x86:</span><span class="sxs-lookup"><span data-stu-id="d0b84-156">List all x86 .NET SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="d0b84-157">Шаг 2. Пробный запуск</span><span class="sxs-lookup"><span data-stu-id="d0b84-157">Step 2 - Do a dry run</span></span>

<span data-ttu-id="d0b84-158">Команды `dotnet-core-uninstall dry-run` и `dotnet-core-uninstall whatif` позволяют просмотреть пакеты SDK и среды выполнения .NET, которые будут удалены, на основе указанных параметров без выполнения удаления.</span><span class="sxs-lookup"><span data-stu-id="d0b84-158">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="d0b84-159">Эти синонимичные команды.</span><span class="sxs-lookup"><span data-stu-id="d0b84-159">These commands are synonyms.</span></span>

<span data-ttu-id="d0b84-160">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span><span class="sxs-lookup"><span data-stu-id="d0b84-160">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d0b84-161">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="d0b84-161">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="d0b84-162">Аргументы</span><span class="sxs-lookup"><span data-stu-id="d0b84-162">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="d0b84-163">Указанная версия для удаления.</span><span class="sxs-lookup"><span data-stu-id="d0b84-163">The specified version to uninstall.</span></span> <span data-ttu-id="d0b84-164">Вы можете перечислить несколько версий одну за другой, разделяя их пробелами.</span><span class="sxs-lookup"><span data-stu-id="d0b84-164">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="d0b84-165">Поддерживаются также файлы ответов.</span><span class="sxs-lookup"><span data-stu-id="d0b84-165">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="d0b84-166">Файлы ответов можно использовать вместо того, чтобы указывать все версии в командной строке.</span><span class="sxs-lookup"><span data-stu-id="d0b84-166">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="d0b84-167">Это текстовые файлы, обычно с расширением \*.rsp. Каждая версия указывается в отдельной строке.</span><span class="sxs-lookup"><span data-stu-id="d0b84-167">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="d0b84-168">Чтобы указать файл ответов для аргумента `VERSION`, используйте символ \@ сразу после имени файла ответа.</span><span class="sxs-lookup"><span data-stu-id="d0b84-168">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="d0b84-169">Параметры</span><span class="sxs-lookup"><span data-stu-id="d0b84-169">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="d0b84-170">Windows</span><span class="sxs-lookup"><span data-stu-id="d0b84-170">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="d0b84-171">Удаляет все пакеты SDK и среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-171">Removes all .NET SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="d0b84-172">Удаляет только пакеты SDK и среды .NET, версия которых вышла раньше, чем указанная.</span><span class="sxs-lookup"><span data-stu-id="d0b84-172">Removes only the .NET SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="d0b84-173">Указанная версия не удаляется.</span><span class="sxs-lookup"><span data-stu-id="d0b84-173">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="d0b84-174">Удаляет все пакеты SDK и среды выполнения .NET, за исключением указанных версий.</span><span class="sxs-lookup"><span data-stu-id="d0b84-174">Removes all .NET SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="d0b84-175">Удаляет пакеты SDK и среды выполнения .NET, за исключением самых поздних версий.</span><span class="sxs-lookup"><span data-stu-id="d0b84-175">Removes .NET SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="d0b84-176">Удаляет пакеты SDK и среды выполнения .NET, замененные более поздними исправлениями.</span><span class="sxs-lookup"><span data-stu-id="d0b84-176">Removes .NET SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="d0b84-177">Этот параметр обеспечивает защиту файла global.json.</span><span class="sxs-lookup"><span data-stu-id="d0b84-177">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="d0b84-178">Удаляет пакеты SDK и среды выполнения .NET, помеченные как предварительные версии.</span><span class="sxs-lookup"><span data-stu-id="d0b84-178">Removes .NET SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="d0b84-179">Удаляет пакеты SDK и среды выполнения .NET, помеченные как предварительные версии, за исключением самых поздних.</span><span class="sxs-lookup"><span data-stu-id="d0b84-179">Removes .NET SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="d0b84-180">Удаляет только среды выполнения ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-180">Removes ASP.NET Runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="d0b84-181">Удаляет только среду выполнения и пакеты размещения .NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-181">Removes .NET Runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="d0b84-182">Удаляет пакеты SDK и среды выполнения .NET, соответствующие указанной версии `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-182">Removes .NET SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="d0b84-183">Удаляет только среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-183">Removes .NET Runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="d0b84-184">Удаляет только пакеты SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-184">Removes .NET SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d0b84-185">Устанавливает уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="d0b84-185">Sets the verbosity level.</span></span> <span data-ttu-id="d0b84-186">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-186">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d0b84-187">Значение по умолчанию — `normal`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-187">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="d0b84-188">Необходимо использовать с `--sdk`, `--runtime` и `--aspnet-runtime` для удаления пакетов SDK или сред выполнения x64.</span><span class="sxs-lookup"><span data-stu-id="d0b84-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="d0b84-189">Необходимо использовать с `--sdk`, `--runtime` и `--aspnet-runtime` для удаления пакетов SDK или сред выполнения x86.</span><span class="sxs-lookup"><span data-stu-id="d0b84-189">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="d0b84-190">**`--force`** Принудительно удаляет версии, которые могут использоваться в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0b84-190">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="d0b84-191">Примечания.</span><span class="sxs-lookup"><span data-stu-id="d0b84-191">Notes:</span></span>

1. <span data-ttu-id="d0b84-192">Требуется только один из параметров `--sdk`, `--runtime`, `--aspnet-runtime` или `--hosting-bundle`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-192">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="d0b84-193">Параметры `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor` и `[<VERSION>...]` служат для исключения.</span><span class="sxs-lookup"><span data-stu-id="d0b84-193">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="d0b84-194">Если `--x64` или `--x86` не указаны, будут удалены обе версии.</span><span class="sxs-lookup"><span data-stu-id="d0b84-194">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="d0b84-195">macOS</span><span class="sxs-lookup"><span data-stu-id="d0b84-195">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="d0b84-196">Удаляет все пакеты SDK и среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-196">Removes all .NET SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="d0b84-197">Удаляет пакеты SDK и среды выполнения .NET, версия которых вышла ранее, чем указанная.</span><span class="sxs-lookup"><span data-stu-id="d0b84-197">Removes .NET SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="d0b84-198">Указанная версия не будет удалена.</span><span class="sxs-lookup"><span data-stu-id="d0b84-198">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="d0b84-199">Удаляет пакеты SDK и среды выполнения .NET, за исключением указанных версий.</span><span class="sxs-lookup"><span data-stu-id="d0b84-199">Removes .NET SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="d0b84-200">Удаляет пакеты SDK и среды выполнения .NET, за исключением самых поздних версий.</span><span class="sxs-lookup"><span data-stu-id="d0b84-200">Removes .NET SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="d0b84-201">Удаляет пакеты SDK и среды выполнения .NET, замененные более поздними исправлениями.</span><span class="sxs-lookup"><span data-stu-id="d0b84-201">Removes .NET SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="d0b84-202">Этот параметр обеспечивает защиту файла global.json.</span><span class="sxs-lookup"><span data-stu-id="d0b84-202">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="d0b84-203">Удаляет пакеты SDK и среды выполнения .NET, помеченные как предварительные версии.</span><span class="sxs-lookup"><span data-stu-id="d0b84-203">Removes .NET SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="d0b84-204">Удаляет пакеты SDK и среды выполнения .NET, помеченные как предварительные версии, за исключением самых поздних.</span><span class="sxs-lookup"><span data-stu-id="d0b84-204">Removes .NET SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="d0b84-205">Удаляет пакеты SDK и среды выполнения .NET, соответствующие указанной версии `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-205">Removes .NET SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="d0b84-206">Удаляет только среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-206">Removes .NET Runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="d0b84-207">Удаляет только пакеты SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-207">Removes .NET SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d0b84-208">Устанавливает уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="d0b84-208">Sets the verbosity level.</span></span> <span data-ttu-id="d0b84-209">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-209">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d0b84-210">Значение по умолчанию — `normal`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-210">The default value is `normal`.</span></span>
  
* <span data-ttu-id="d0b84-211">**`--force`** Принудительно удаляет версии, которые могут использоваться Visual Studio или пакетами SDK.</span><span class="sxs-lookup"><span data-stu-id="d0b84-211">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="d0b84-212">Примечания.</span><span class="sxs-lookup"><span data-stu-id="d0b84-212">Notes:</span></span>

1. <span data-ttu-id="d0b84-213">Требуется указать только один параметр: `--sdk` или `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-213">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="d0b84-214">Параметры `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor` и `[<VERSION>...]` служат для исключения.</span><span class="sxs-lookup"><span data-stu-id="d0b84-214">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="d0b84-215">Примеры</span><span class="sxs-lookup"><span data-stu-id="d0b84-215">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="d0b84-216">По умолчанию пакеты SDK и среды выполнения .NET, которые могут требоваться для работы Visual Studio или других пакетов SDK, не включаются в выходные данные `dotnet-core-uninstall dry-run`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-216">By default, .NET SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="d0b84-217">В примерах ниже некоторые указанные пакеты SDK и среды выполнения могут быть исключены из выходных данных в зависимости от состояния компьютера.</span><span class="sxs-lookup"><span data-stu-id="d0b84-217">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="d0b84-218">Чтобы включить все пакеты SDK и среды выполнения, укажите их явно в качестве аргументов или используйте параметр `--force`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-218">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="d0b84-219">Пробный запуск удаления всех сред выполнения .NET, замененных более поздними версиями:</span><span class="sxs-lookup"><span data-stu-id="d0b84-219">Dry run of removing all .NET Runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="d0b84-220">Пробный запуск удаления всех пакетов SDK для .NET, версия которых вышла раньше `2.2.301`:</span><span class="sxs-lookup"><span data-stu-id="d0b84-220">Dry run of removing all .NET SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-sdks-and-runtimes"></a><span data-ttu-id="d0b84-221">Шаг 3. Удаление пакетов SDK и сред выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="d0b84-221">Step 3 - Uninstall .NET SDKs and Runtimes</span></span>

<span data-ttu-id="d0b84-222">Команда `dotnet-core-uninstall remove` удаляет пакеты SDK и среды выполнения .NET, указанные с использованием коллекции параметров.</span><span class="sxs-lookup"><span data-stu-id="d0b84-222">`dotnet-core-uninstall remove` uninstalls .NET SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="d0b84-223">В версии 1.2 и более поздних версиях можно удалять пакеты SDK и среды выполнения с версией 5.0 или более ранней, а в предыдущих версиях средства можно удалить версии 3.1 и более ранние.</span><span class="sxs-lookup"><span data-stu-id="d0b84-223">Versions 1.2 and later can uninstall SDKs and runtimes with version 5.0 or earlier, and previous versions of the tool can uninstall 3.1 and earlier.</span></span>

<span data-ttu-id="d0b84-224">У средства разрушающее поведение, поэтому **настоятельно** рекомендуется выполнять пробный запуск перед выполнением команды удаления.</span><span class="sxs-lookup"><span data-stu-id="d0b84-224">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="d0b84-225">В ходе пробного запуска будут показаны пакеты SDK и среды .NET, подлежащие удалению при использовании команды `remove`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-225">The dry run will show you what .NET SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="d0b84-226">Чтобы узнать, какие пакеты SDK и среды выполнения безопасно удалять, обратитесь к разделу [Нужно ли удалять версию](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version).</span><span class="sxs-lookup"><span data-stu-id="d0b84-226">Refer to [Should I remove a version?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="d0b84-227">Учитывайте следующие факторы.</span><span class="sxs-lookup"><span data-stu-id="d0b84-227">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="d0b84-228">Это средство может удалять версии пакета SDK для .NET, необходимые для файлов `global.json` на компьютере.</span><span class="sxs-lookup"><span data-stu-id="d0b84-228">This tool can uninstall versions of the .NET SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="d0b84-229">Эти пакеты можно повторно установить, предварительно скачав их на [этой странице](https://dotnet.microsoft.com/download/dotnet).</span><span class="sxs-lookup"><span data-stu-id="d0b84-229">You can reinstall .NET SDKs from the [Download .NET](https://dotnet.microsoft.com/download/dotnet) page.</span></span>
>- <span data-ttu-id="d0b84-230">Средство может удалять версии среды выполнения .NET, необходимые для зависимых от платформы приложений на компьютере.</span><span class="sxs-lookup"><span data-stu-id="d0b84-230">This tool can uninstall versions of the .NET Runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="d0b84-231">Вы можете переустановить среду выполнения .NET, предварительно скачав ее с [этой страницы](https://dotnet.microsoft.com/download/dotnet).</span><span class="sxs-lookup"><span data-stu-id="d0b84-231">You can reinstall .NET Runtimes from the [Download .NET](https://dotnet.microsoft.com/download/dotnet) page.</span></span>
>- <span data-ttu-id="d0b84-232">Это средство может удалять версии пакета SDK и среды выполнения .NET, от которых зависит работа Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0b84-232">This tool can uninstall versions of the .NET SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="d0b84-233">Если нарушите работу установленной версии Visual Studio, выполните команду "Исправить" в установщике Visual Studio, чтобы восстановить рабочее состояние.</span><span class="sxs-lookup"><span data-stu-id="d0b84-233">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="d0b84-234">По умолчанию все команды поддерживают пакеты SDK и среды выполнения .NET, которые могут потребоваться для работы Visual Studio или других пакетов SDK.</span><span class="sxs-lookup"><span data-stu-id="d0b84-234">By default, all commands keep the .NET SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="d0b84-235">Эти пакеты и среды выполнения можно удалить путем их явного перечисления в виде аргументов или с использованием параметра `--force`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-235">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="d0b84-236">Для удаления пакетов SDK и сред выполнения .NET средству требуются повышенные права.</span><span class="sxs-lookup"><span data-stu-id="d0b84-236">The tool requires elevation to uninstall .NET SDKs and runtimes.</span></span> <span data-ttu-id="d0b84-237">Запустите средство в командной строке администратора в ОС Windows или с помощью команды `sudo` в macOS.</span><span class="sxs-lookup"><span data-stu-id="d0b84-237">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="d0b84-238">Для команд `dry-run` и `whatif` повышение прав не требуется.</span><span class="sxs-lookup"><span data-stu-id="d0b84-238">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="d0b84-239">**dotnet-core-uninstall remove**</span><span class="sxs-lookup"><span data-stu-id="d0b84-239">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="d0b84-240">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="d0b84-240">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="d0b84-241">Аргументы</span><span class="sxs-lookup"><span data-stu-id="d0b84-241">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="d0b84-242">Указанная версия для удаления.</span><span class="sxs-lookup"><span data-stu-id="d0b84-242">The specified version to uninstall.</span></span> <span data-ttu-id="d0b84-243">Вы можете перечислить несколько версий одну за другой, разделяя их пробелами.</span><span class="sxs-lookup"><span data-stu-id="d0b84-243">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="d0b84-244">Поддерживаются также файлы ответов.</span><span class="sxs-lookup"><span data-stu-id="d0b84-244">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="d0b84-245">Файлы ответов можно использовать вместо того, чтобы указывать все версии в командной строке.</span><span class="sxs-lookup"><span data-stu-id="d0b84-245">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="d0b84-246">Это текстовые файлы, обычно с расширением \*.rsp. Каждая версия указывается в отдельной строке.</span><span class="sxs-lookup"><span data-stu-id="d0b84-246">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="d0b84-247">Чтобы указать файл ответов для аргумента `VERSION`, используйте символ \@ сразу после имени файла ответа.</span><span class="sxs-lookup"><span data-stu-id="d0b84-247">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="d0b84-248">Параметры</span><span class="sxs-lookup"><span data-stu-id="d0b84-248">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="d0b84-249">Windows</span><span class="sxs-lookup"><span data-stu-id="d0b84-249">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="d0b84-250">Удаляет все пакеты SDK и среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-250">Removes all .NET SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="d0b84-251">Удаляет только пакеты SDK и среды .NET, версия которых вышла раньше, чем указанная.</span><span class="sxs-lookup"><span data-stu-id="d0b84-251">Removes only the .NET SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="d0b84-252">Указанная версия не удаляется.</span><span class="sxs-lookup"><span data-stu-id="d0b84-252">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="d0b84-253">Удаляет все пакеты SDK и среды выполнения .NET, за исключением указанных версий.</span><span class="sxs-lookup"><span data-stu-id="d0b84-253">Removes all .NET SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="d0b84-254">Удаляет пакеты SDK и среды выполнения .NET, за исключением самых поздних версий.</span><span class="sxs-lookup"><span data-stu-id="d0b84-254">Removes .NET SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="d0b84-255">Удаляет пакеты SDK и среды выполнения .NET, замененные более поздними исправлениями.</span><span class="sxs-lookup"><span data-stu-id="d0b84-255">Removes .NET SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="d0b84-256">Этот параметр обеспечивает защиту файла global.json.</span><span class="sxs-lookup"><span data-stu-id="d0b84-256">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="d0b84-257">Удаляет пакеты SDK и среды выполнения .NET, помеченные как предварительные версии.</span><span class="sxs-lookup"><span data-stu-id="d0b84-257">Removes .NET SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="d0b84-258">Удаляет пакеты SDK и среды выполнения .NET, помеченные как предварительные версии, за исключением самых поздних.</span><span class="sxs-lookup"><span data-stu-id="d0b84-258">Removes .NET SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="d0b84-259">Удаляет только среды выполнения ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-259">Removes ASP.NET Runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="d0b84-260">Удаляет только пакеты размещения .NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-260">Removes .NET hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="d0b84-261">Удаляет пакеты SDK и среды выполнения .NET, соответствующие указанной версии `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-261">Removes .NET SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="d0b84-262">Удаляет только среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-262">Removes .NET Runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="d0b84-263">Удаляет только пакеты SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-263">Removes .NET SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d0b84-264">Устанавливает уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="d0b84-264">Sets the verbosity level.</span></span> <span data-ttu-id="d0b84-265">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-265">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d0b84-266">Значение по умолчанию — `normal`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-266">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="d0b84-267">Необходимо использовать с `--sdk`, `--runtime` и `--aspnet-runtime` для удаления пакетов SDK или сред выполнения x64.</span><span class="sxs-lookup"><span data-stu-id="d0b84-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="d0b84-268">Необходимо использовать с `--sdk`, `--runtime` и `--aspnet-runtime` для удаления пакетов SDK или сред выполнения x86.</span><span class="sxs-lookup"><span data-stu-id="d0b84-268">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="d0b84-269">**`-y, --yes`** Выполняет команду без подтверждения Yes или No.</span><span class="sxs-lookup"><span data-stu-id="d0b84-269">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="d0b84-270">**`--force`** Принудительно удаляет версии, которые могут использоваться в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0b84-270">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="d0b84-271">Примечания.</span><span class="sxs-lookup"><span data-stu-id="d0b84-271">Notes:</span></span>

1. <span data-ttu-id="d0b84-272">Требуется только один из параметров `--sdk`, `--runtime`, `--aspnet-runtime` или `--hosting-bundle`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-272">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="d0b84-273">Параметры `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor` и `[<VERSION>...]` служат для исключения.</span><span class="sxs-lookup"><span data-stu-id="d0b84-273">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="d0b84-274">Если `--x64` или `--x86` не указаны, будут удалены обе версии.</span><span class="sxs-lookup"><span data-stu-id="d0b84-274">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="d0b84-275">macOS</span><span class="sxs-lookup"><span data-stu-id="d0b84-275">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="d0b84-276">Удаляет все пакеты SDK и среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-276">Removes all .NET SDKs and runtimes.</span></span>

* **`--all-below <VERSION>[ <VERSION>...]`**

  <span data-ttu-id="d0b84-277">Удаляет пакеты SDK и среды выполнения .NET, версия которых вышла ранее, чем указанная.</span><span class="sxs-lookup"><span data-stu-id="d0b84-277">Removes .NET SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="d0b84-278">Указанная версия не будет удалена.</span><span class="sxs-lookup"><span data-stu-id="d0b84-278">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  <span data-ttu-id="d0b84-279">Удаляет пакеты SDK и среды выполнения .NET, за исключением указанных версий.</span><span class="sxs-lookup"><span data-stu-id="d0b84-279">Removes .NET SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="d0b84-280">Удаляет пакеты SDK и среды выполнения .NET, за исключением самых поздних версий.</span><span class="sxs-lookup"><span data-stu-id="d0b84-280">Removes .NET SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="d0b84-281">Удаляет пакеты SDK и среды выполнения .NET, замененные более поздними исправлениями.</span><span class="sxs-lookup"><span data-stu-id="d0b84-281">Removes .NET SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="d0b84-282">Этот параметр обеспечивает защиту файла global.json.</span><span class="sxs-lookup"><span data-stu-id="d0b84-282">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="d0b84-283">Удаляет пакеты SDK и среды выполнения .NET, помеченные как предварительные версии.</span><span class="sxs-lookup"><span data-stu-id="d0b84-283">Removes .NET SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="d0b84-284">Удаляет пакеты SDK и среды выполнения .NET, помеченные как предварительные версии, за исключением самых поздних.</span><span class="sxs-lookup"><span data-stu-id="d0b84-284">Removes .NET SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="d0b84-285">Удаляет пакеты SDK и среды выполнения .NET, соответствующие указанной версии `major.minor`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-285">Removes .NET SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="d0b84-286">Удаляет только среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-286">Removes .NET Runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="d0b84-287">Удаляет только пакеты SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="d0b84-287">Removes .NET SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="d0b84-288">Устанавливает уровень детализации.</span><span class="sxs-lookup"><span data-stu-id="d0b84-288">Sets the verbosity level.</span></span> <span data-ttu-id="d0b84-289">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-289">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d0b84-290">Значение по умолчанию — `normal`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-290">The default value is `normal`.</span></span>

* <span data-ttu-id="d0b84-291">**`-y, --yes`** Выполняет команду без подтверждения Yes или No.</span><span class="sxs-lookup"><span data-stu-id="d0b84-291">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="d0b84-292">**`--force`** Принудительно удаляет версии, которые могут использоваться Visual Studio или пакетами SDK.</span><span class="sxs-lookup"><span data-stu-id="d0b84-292">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="d0b84-293">Примечания.</span><span class="sxs-lookup"><span data-stu-id="d0b84-293">Notes:</span></span>

1. <span data-ttu-id="d0b84-294">Требуется указать только один параметр: `--sdk` или `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-294">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="d0b84-295">Параметры `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor` и `[<VERSION>...]` служат для исключения.</span><span class="sxs-lookup"><span data-stu-id="d0b84-295">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="d0b84-296">Примеры</span><span class="sxs-lookup"><span data-stu-id="d0b84-296">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="d0b84-297">По умолчанию пакеты SDK и среды выполнения .NET, которые могут требоваться для работы Visual Studio или других пакетов SDK, сохраняются.</span><span class="sxs-lookup"><span data-stu-id="d0b84-297">By default, .NET SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="d0b84-298">В примерах ниже могут остаться некоторые из указанных пакетов SDK и сред выполнения в зависимости от состояния компьютера.</span><span class="sxs-lookup"><span data-stu-id="d0b84-298">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="d0b84-299">Чтобы удалить все пакеты и среды выполнения, укажите их явно в качестве аргументов или используйте параметр `--force`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-299">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="d0b84-300">Удаление всех сред выполнения .NET, кроме версии `3.0.0-preview6-27804-01` без подтверждения Yes или No:</span><span class="sxs-lookup"><span data-stu-id="d0b84-300">Remove all .NET Runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="d0b84-301">Удаление всех пакетов SDK для .NET Core 1.1 без подтверждения Yes или No:</span><span class="sxs-lookup"><span data-stu-id="d0b84-301">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="d0b84-302">Удаление пакета SDK для .NET Core 1.1.11 без вывода на консоль:</span><span class="sxs-lookup"><span data-stu-id="d0b84-302">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="d0b84-303">Удаление всех пакетов SDK для .NET, которые можно безопасно удалить с помощью этого средства:</span><span class="sxs-lookup"><span data-stu-id="d0b84-303">Remove all .NET SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="d0b84-304">Удаление всех пакетов SDK для .NET, которые можно безопасно удалить с помощью этого средства, в том числе тех, которые могут требоваться для работы Visual Studio (не рекомендуется):</span><span class="sxs-lookup"><span data-stu-id="d0b84-304">Remove all .NET SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="d0b84-305">Удаление всех пакетов SDK для .NET, указанных в файле ответов `versions.rsp`:</span><span class="sxs-lookup"><span data-stu-id="d0b84-305">Remove all .NET SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="d0b84-306">В файле *versions.rsp* содержится следующее:</span><span class="sxs-lookup"><span data-stu-id="d0b84-306">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="d0b84-307">Шаг 4. Удаление резервной папки NuGet (необязательный)</span><span class="sxs-lookup"><span data-stu-id="d0b84-307">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="d0b84-308">В некоторых случаях папка `NuGetFallbackFolder` может больше не требоваться, и ее понадобится удалить.</span><span class="sxs-lookup"><span data-stu-id="d0b84-308">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="d0b84-309">Дополнительные сведения об удалении папки NuGetFallbackFolder см. в [этом разделе](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="d0b84-309">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="d0b84-310">Удаление средства</span><span class="sxs-lookup"><span data-stu-id="d0b84-310">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="d0b84-311">Windows</span><span class="sxs-lookup"><span data-stu-id="d0b84-311">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="d0b84-312">Откройте окно **Установка и удаление программ**.</span><span class="sxs-lookup"><span data-stu-id="d0b84-312">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="d0b84-313">Найдите `Microsoft .NET SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="d0b84-313">Search for `Microsoft .NET SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="d0b84-314">Выберите **Удалить**.</span><span class="sxs-lookup"><span data-stu-id="d0b84-314">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="d0b84-315">macOS</span><span class="sxs-lookup"><span data-stu-id="d0b84-315">macOS</span></span>](#tab/macos)

<span data-ttu-id="d0b84-316">Удалите скачанный файл *dotnet-core-uninstall.tar.gz* из каталога, в котором он установлен.</span><span class="sxs-lookup"><span data-stu-id="d0b84-316">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="d0b84-317">Если содержимое этого файла распаковано в другой каталог, необходимо также удалить это содержимое.</span><span class="sxs-lookup"><span data-stu-id="d0b84-317">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
