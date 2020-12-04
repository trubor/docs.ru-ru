---
title: Команда dotnet pack
description: Команда dotnet pack создает пакеты NuGet для проекта .NET.
ms.date: 04/28/2020
ms.openlocfilehash: 3ca7947b4ed9902b163f09a7b57696f304610cce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674805"
---
# <a name="dotnet-pack"></a><span data-ttu-id="f701c-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="f701c-103">dotnet pack</span></span>

<span data-ttu-id="f701c-104">**Эта статья относится к следующему:** ✔️ пакет SDK для .NET Core 2.x и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="f701c-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f701c-105">name</span><span class="sxs-lookup"><span data-stu-id="f701c-105">Name</span></span>

<span data-ttu-id="f701c-106">`dotnet pack` — упаковывает код в пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="f701c-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f701c-107">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="f701c-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output <OUTPUT_DIRECTORY>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--serviceable] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet pack -h|--help
```

## <a name="description"></a><span data-ttu-id="f701c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="f701c-108">Description</span></span>

<span data-ttu-id="f701c-109">Команда `dotnet pack` выполняет сборку проекта и создает пакеты NuGet.</span><span class="sxs-lookup"><span data-stu-id="f701c-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="f701c-110">Результат выполнения команды — пакет NuGet (то есть файл *NUPKG*).</span><span class="sxs-lookup"><span data-stu-id="f701c-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="f701c-111">Если вы хотите создать пакет, содержащий отладочные символы, доступны два варианта:</span><span class="sxs-lookup"><span data-stu-id="f701c-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="f701c-112">`--include-symbols` — создает пакет символов.</span><span class="sxs-lookup"><span data-stu-id="f701c-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="f701c-113">`--include-source` — создает пакет символов с папкой `src`, содержащей исходные файлы.</span><span class="sxs-lookup"><span data-stu-id="f701c-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="f701c-114">Зависимости NuGet упакованного проекта добавляются в файл *NUSPEC*, чтобы их можно было разрешить при установке пакета.</span><span class="sxs-lookup"><span data-stu-id="f701c-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="f701c-115">Межпроектные ссылки не упаковываются в проекте.</span><span class="sxs-lookup"><span data-stu-id="f701c-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="f701c-116">Сейчас при наличии межпроектных зависимостей требуется один пакет на каждый проект.</span><span class="sxs-lookup"><span data-stu-id="f701c-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="f701c-117">`dotnet pack` по умолчанию сначала выполняет сборку проекта.</span><span class="sxs-lookup"><span data-stu-id="f701c-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="f701c-118">Чтобы избежать этого, передайте параметр `--no-build`.</span><span class="sxs-lookup"><span data-stu-id="f701c-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="f701c-119">Этот вариант часто бывает полезен, например в сценариях сборки с непрерывной интеграцией (CI), когда вы знаете, что код был собран недавно.</span><span class="sxs-lookup"><span data-stu-id="f701c-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

> [!NOTE]
> <span data-ttu-id="f701c-120">В некоторых случаях выполнить неявную сборку невозможно.</span><span class="sxs-lookup"><span data-stu-id="f701c-120">In some cases, the implicit build cannot be performed.</span></span> <span data-ttu-id="f701c-121">Это может произойти, если задано свойство `GeneratePackageOnBuild`, позволяющее избежать циклической зависимости между целевыми объектами сборки и упаковки.</span><span class="sxs-lookup"><span data-stu-id="f701c-121">This can occur when `GeneratePackageOnBuild` is set, to avoid a cyclic dependency between build and pack targets.</span></span> <span data-ttu-id="f701c-122">Кроме того, сборка может завершиться ошибкой при наличии заблокированного файла или другой проблемы.</span><span class="sxs-lookup"><span data-stu-id="f701c-122">The build can also fail if there is a locked file or other issue.</span></span>

<span data-ttu-id="f701c-123">Может предоставлять свойства MSBuild команде `dotnet pack` для процесса упаковки.</span><span class="sxs-lookup"><span data-stu-id="f701c-123">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="f701c-124">Дополнительные сведения см. в разделах [Свойства метаданных NuGet](csproj.md#nuget-metadata-properties) и [Справочник по командной строке MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="f701c-124">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="f701c-125">В разделе [Примеры](#examples) показано, как использовать параметр -p MSBuild в различных сценариях.</span><span class="sxs-lookup"><span data-stu-id="f701c-125">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="f701c-126">Веб-проекты по умолчанию не упаковываются.</span><span class="sxs-lookup"><span data-stu-id="f701c-126">Web projects aren't packable by default.</span></span> <span data-ttu-id="f701c-127">Чтобы переопределить такое поведение по умолчанию, добавьте следующее свойство в файл с расширением *.csproj*:</span><span class="sxs-lookup"><span data-stu-id="f701c-127">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

### <a name="implicit-restore"></a><span data-ttu-id="f701c-128">Неявное восстановление</span><span class="sxs-lookup"><span data-stu-id="f701c-128">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="f701c-129">Аргументы</span><span class="sxs-lookup"><span data-stu-id="f701c-129">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="f701c-130">Проект или решение для упаковки.</span><span class="sxs-lookup"><span data-stu-id="f701c-130">The project or solution to pack.</span></span> <span data-ttu-id="f701c-131">Это путь к файлу [.csproj](csproj.md), .vbproj или .fsproj либо файлу решения или каталогу.</span><span class="sxs-lookup"><span data-stu-id="f701c-131">It's either a path to a [csproj file](csproj.md), vbproj file, fsproj file, a solution file, or to a directory.</span></span> <span data-ttu-id="f701c-132">Если он не указан, команда ищет текущий каталог для файла решения или проекта.</span><span class="sxs-lookup"><span data-stu-id="f701c-132">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="f701c-133">Параметры</span><span class="sxs-lookup"><span data-stu-id="f701c-133">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="f701c-134">Определяет конфигурацию сборки.</span><span class="sxs-lookup"><span data-stu-id="f701c-134">Defines the build configuration.</span></span> <span data-ttu-id="f701c-135">По умолчанию для большинства проектов используется `Debug`, но можно переопределить параметры конфигурации сборки в проекте.</span><span class="sxs-lookup"><span data-stu-id="f701c-135">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="f701c-136">Принудительное разрешение всех зависимостей, даже если последнее восстановление прошло успешно.</span><span class="sxs-lookup"><span data-stu-id="f701c-136">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="f701c-137">Указание этого флага дает тот же результат, что удаление файла *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="f701c-137">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f701c-138">Выводит краткую справку по команде.</span><span class="sxs-lookup"><span data-stu-id="f701c-138">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="f701c-139">Включает пакеты NuGet отладочных символов в дополнение к обычным пакетам NuGet в выходном каталоге.</span><span class="sxs-lookup"><span data-stu-id="f701c-139">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="f701c-140">Исходные файлы включены в папку `src` пакета символов.</span><span class="sxs-lookup"><span data-stu-id="f701c-140">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="f701c-141">Включает пакеты NuGet отладочных символов в дополнение к обычным пакетам NuGet в выходном каталоге.</span><span class="sxs-lookup"><span data-stu-id="f701c-141">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="f701c-142">Позволяет остановить команду и дождаться, пока пользователь введет данные или выполнит действие (например, завершит проверку подлинности).</span><span class="sxs-lookup"><span data-stu-id="f701c-142">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="f701c-143">Доступно, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f701c-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="f701c-144">Не выполняет сборку проекта перед упаковкой.</span><span class="sxs-lookup"><span data-stu-id="f701c-144">Doesn't build the project before packing.</span></span> <span data-ttu-id="f701c-145">Он также неявно задает флаг `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="f701c-145">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="f701c-146">Межпроектные ссылки игнорируются, и восстанавливается только корневой проект.</span><span class="sxs-lookup"><span data-stu-id="f701c-146">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f701c-147">Не выполняет неявное восстановление при выполнении команды.</span><span class="sxs-lookup"><span data-stu-id="f701c-147">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="f701c-148">Скрывает загрузочный баннер или сообщение об авторских правах.</span><span class="sxs-lookup"><span data-stu-id="f701c-148">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="f701c-149">Доступно, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f701c-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f701c-150">Собранные пакеты помещаются в указанный каталог.</span><span class="sxs-lookup"><span data-stu-id="f701c-150">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="f701c-151">Задает целевую среду выполнения для восстановления пакетов.</span><span class="sxs-lookup"><span data-stu-id="f701c-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="f701c-152">Список идентификаторов сред выполнения (RID) см. в [каталоге RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="f701c-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="f701c-153">Задает флаг "подлежит обслуживанию" в пакете.</span><span class="sxs-lookup"><span data-stu-id="f701c-153">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="f701c-154">Дополнительные сведения см. в записи блога о том, что [.NET Framework 4.5.1 поддерживает обновления системы безопасности Майкрософт для библиотек .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="f701c-154">For more information, see [.NET Blog: .NET Framework 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="f701c-155">Определяет значение для свойства `$(VersionSuffix)` MSBuild в проекте.</span><span class="sxs-lookup"><span data-stu-id="f701c-155">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f701c-156">Задает уровень детализации команды.</span><span class="sxs-lookup"><span data-stu-id="f701c-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f701c-157">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f701c-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="f701c-158">Примеры</span><span class="sxs-lookup"><span data-stu-id="f701c-158">Examples</span></span>

- <span data-ttu-id="f701c-159">Упаковка проекта в текущем каталоге:</span><span class="sxs-lookup"><span data-stu-id="f701c-159">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="f701c-160">Упаковка проекта `app1`:</span><span class="sxs-lookup"><span data-stu-id="f701c-160">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="f701c-161">Упаковка проекта в текущем каталоге; полученные пакеты помещаются в папку `nupkgs`:</span><span class="sxs-lookup"><span data-stu-id="f701c-161">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="f701c-162">Упаковка проекта в текущем каталоге в папку `nupkgs` и пропуск этапа сборки:</span><span class="sxs-lookup"><span data-stu-id="f701c-162">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="f701c-163">Если суффикс версии пакета в файле *CSPROJ* настроен как `<VersionSuffix>$(VersionSuffix)</VersionSuffix>`, упаковка текущего проекта и обновление версии полученных пакетов с использованием указанного суффикса:</span><span class="sxs-lookup"><span data-stu-id="f701c-163">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="f701c-164">Устанавливает версию пакета в `2.1.0` с использованием свойства MSBuild `PackageVersion`:</span><span class="sxs-lookup"><span data-stu-id="f701c-164">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="f701c-165">Упакуйте проект для [требуемой версии .NET Framework](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="f701c-165">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="f701c-166">Упакуйте проект и используйте определенную среду выполнения (Windows 10) для операции восстановления:</span><span class="sxs-lookup"><span data-stu-id="f701c-166">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="f701c-167">Упакуйте проект с помощью *NUSPEC-файла*:</span><span class="sxs-lookup"><span data-stu-id="f701c-167">Pack the project using a *.nuspec* file:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```

  <span data-ttu-id="f701c-168">Дополнительные сведения об использовании `NuspecFile`, `NuspecBasePath` и `NuspecProperties` см. в следующих документах:</span><span class="sxs-lookup"><span data-stu-id="f701c-168">For information about how to use `NuspecFile`, `NuspecBasePath`, and `NuspecProperties`, see the following resources:</span></span>

  - [<span data-ttu-id="f701c-169">Упаковка с помощью NUSPEC</span><span class="sxs-lookup"><span data-stu-id="f701c-169">Packing using a .nuspec</span></span>](/nuget/reference/msbuild-targets#packing-using-a-nuspec)
  - [<span data-ttu-id="f701c-170">Улучшенные точки расширения для создания настраиваемого пакета</span><span class="sxs-lookup"><span data-stu-id="f701c-170">Advanced extension points to create customized package</span></span>](/nuget/reference/msbuild-targets#advanced-extension-points-to-create-customized-package)
  - [<span data-ttu-id="f701c-171">Глобальные свойства</span><span class="sxs-lookup"><span data-stu-id="f701c-171">Global properties</span></span>](/visualstudio/msbuild/msbuild-properties#global-properties)
