---
title: Команда dotnet restore
description: Вы узнаете, как восстановить зависимости и связанные с проектом средства при помощи команды dotnet restore.
ms.date: 02/27/2020
ms.openlocfilehash: 14bcf65bb78e6d1d96604c8a10a3ba94fab80db8
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874840"
---
# <a name="dotnet-restore"></a><span data-ttu-id="23638-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="23638-103">dotnet restore</span></span>

<span data-ttu-id="23638-104">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="23638-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="23638-105">name</span><span class="sxs-lookup"><span data-stu-id="23638-105">Name</span></span>

<span data-ttu-id="23638-106">`dotnet restore` — восстанавливает зависимости и средства проекта.</span><span class="sxs-lookup"><span data-stu-id="23638-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="23638-107">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="23638-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lock-file] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="23638-108">Описание</span><span class="sxs-lookup"><span data-stu-id="23638-108">Description</span></span>

<span data-ttu-id="23638-109">Команда `dotnet restore` использует NuGet для восстановления зависимостей, а также связанных с проектом средств, которые указаны в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="23638-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span>  <span data-ttu-id="23638-110">В большинстве случаев не требуется явно использовать команду `dotnet restore`, так как в случае необходимости восстановление NuGet происходит неявным образом при выполнении следующих команд:</span><span class="sxs-lookup"><span data-stu-id="23638-110">In most cases, you don't need to explicitly use the `dotnet restore` command, since a NuGet restore is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="23638-111">В некоторых случаях выполнять неявное восстановление NuGet с помощью этих команд неудобно.</span><span class="sxs-lookup"><span data-stu-id="23638-111">Sometimes, it might be inconvenient to run the implicit NuGet restore with these commands.</span></span> <span data-ttu-id="23638-112">Например, некоторые автоматизированные системы, такие как системы сборки, должны явно вызывать `dotnet restore`, чтобы контролировать процесс восстановления и, следовательно, отслеживать использование сетевых ресурсов.</span><span class="sxs-lookup"><span data-stu-id="23638-112">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="23638-113">Чтобы избежать неявного восстановления NuGet, с любой из приведенных выше команд можно использовать флаг `--no-restore` для отключения неявного восстановления.</span><span class="sxs-lookup"><span data-stu-id="23638-113">To prevent the implicit NuGet restore, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

### <a name="specify-feeds"></a><span data-ttu-id="23638-114">Указание каналов</span><span class="sxs-lookup"><span data-stu-id="23638-114">Specify feeds</span></span>

<span data-ttu-id="23638-115">Для восстановления зависимостей NuGet требуются каналы, где находятся пакеты.</span><span class="sxs-lookup"><span data-stu-id="23638-115">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="23638-116">Каналы обычно предоставляются посредством файла конфигурации *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="23638-116">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="23638-117">Файл конфигурации по умолчанию предоставляется при установке пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="23638-117">A default configuration file is provided when the .NET SDK is installed.</span></span> <span data-ttu-id="23638-118">Чтобы указать дополнительные каналы, выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="23638-118">To specify additional feeds, do one of the following:</span></span>

- <span data-ttu-id="23638-119">Создайте собственный файл *nuget.config* в каталоге проекта.</span><span class="sxs-lookup"><span data-stu-id="23638-119">Create your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="23638-120">Дополнительные сведения см. в статье [Распространенные конфигурации NuGet](/nuget/consume-packages/configuring-nuget-behavior) и разделе [Различия nuget.config](#nugetconfig-differences) далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="23638-120">For more information, see [Common NuGet configurations](/nuget/consume-packages/configuring-nuget-behavior) and [nuget.config differences](#nugetconfig-differences) later in this article.</span></span>
- <span data-ttu-id="23638-121">Используйте команды `dotnet nuget`, такие как [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span><span class="sxs-lookup"><span data-stu-id="23638-121">Use `dotnet nuget` commands such as [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="23638-122">Вы можете переопределить веб-каналы *nuget.config* с помощью свойства `-s`.</span><span class="sxs-lookup"><span data-stu-id="23638-122">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="23638-123">Сведения об использовании веб-каналов, прошедших проверку подлинности, см. в статье [Использование пакетов из веб-каналов, прошедших проверку подлинности](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span><span class="sxs-lookup"><span data-stu-id="23638-123">For information about how to use authenticated feeds, see [Consuming packages from authenticated feeds](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span></span>

### <a name="global-packages-folder"></a><span data-ttu-id="23638-124">Глобальный каталог пакетов</span><span class="sxs-lookup"><span data-stu-id="23638-124">Global packages folder</span></span>

<span data-ttu-id="23638-125">Для зависимостей можно указать, куда помещаются восстанавливаемые пакеты во время операции восстановления, с помощью аргумента `--packages`.</span><span class="sxs-lookup"><span data-stu-id="23638-125">For dependencies, you can specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="23638-126">Если значение не указано, используется кэш пакетов NuGet по умолчанию. Он находится в каталоге `.nuget/packages` в домашнем каталоге пользователя во всех операционных системах.</span><span class="sxs-lookup"><span data-stu-id="23638-126">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="23638-127">Например, */home/user1* на Linux или *C:\Users\user1* в Windows.</span><span class="sxs-lookup"><span data-stu-id="23638-127">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

### <a name="project-specific-tooling"></a><span data-ttu-id="23638-128">Связанные с проектом средства</span><span class="sxs-lookup"><span data-stu-id="23638-128">Project-specific tooling</span></span>

<span data-ttu-id="23638-129">Для связанных с проектом средств `dotnet restore` сначала восстанавливает пакет, в котором упаковано средство, а затем — зависимости средства, указанные в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="23638-129">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="23638-130">Различия nuget.config</span><span class="sxs-lookup"><span data-stu-id="23638-130">nuget.config differences</span></span>

<span data-ttu-id="23638-131">На поведение команды `dotnet restore` влияют параметры в файле *nuget.config*, если он существует.</span><span class="sxs-lookup"><span data-stu-id="23638-131">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="23638-132">Например, если установить параметр `globalPackagesFolder` в файле *nuget.config*, то восстановленные пакеты NuGet будут помещены в указанную папку.</span><span class="sxs-lookup"><span data-stu-id="23638-132">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="23638-133">Для получения того же результата можно указать параметр `--packages` команды `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="23638-133">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="23638-134">Дополнительные сведения см. в [справочнике по файлу nuget.config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="23638-134">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="23638-135">Существует три конкретных параметра, которые `dotnet restore` игнорирует:</span><span class="sxs-lookup"><span data-stu-id="23638-135">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="23638-136">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="23638-136">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="23638-137">Перенаправления привязок не работают с элементами `<PackageReference>`, а .NET поддерживает только элементы `<PackageReference>` для пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="23638-137">Binding redirects don't work with `<PackageReference>` elements and .NET only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="23638-138">solution</span><span class="sxs-lookup"><span data-stu-id="23638-138">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="23638-139">Этот параметр относится только к Visual Studio и не применяется к .NET.</span><span class="sxs-lookup"><span data-stu-id="23638-139">This setting is Visual Studio specific and doesn't apply to .NET.</span></span> <span data-ttu-id="23638-140">.NET не использует файл `packages.config`. Вместо этого он использует элементы `<PackageReference>` для пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="23638-140">.NET doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="23638-141">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="23638-141">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="23638-142">В пакете SDK для .NET 5.0.100 добавлена поддержка кроссплатформенной проверки подписей пакетов.</span><span class="sxs-lookup"><span data-stu-id="23638-142">Support for cross-platform package signature verification was added in the .NET 5.0.100 SDK.</span></span>

## <a name="arguments"></a><span data-ttu-id="23638-143">Аргументы</span><span class="sxs-lookup"><span data-stu-id="23638-143">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="23638-144">Дополнительный путь к файлу проекта для восстановления.</span><span class="sxs-lookup"><span data-stu-id="23638-144">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="23638-145">Параметры</span><span class="sxs-lookup"><span data-stu-id="23638-145">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="23638-146">Файл конфигурации NuGet (*nuget.config*), используемый для операции восстановления.</span><span class="sxs-lookup"><span data-stu-id="23638-146">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="23638-147">Отключает параллельное восстановление нескольких проектов.</span><span class="sxs-lookup"><span data-stu-id="23638-147">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="23638-148">Принудительное разрешение всех зависимостей, даже если последнее восстановление прошло успешно.</span><span class="sxs-lookup"><span data-stu-id="23638-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="23638-149">Указание этого флага дает тот же результат, что удаление файла *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="23638-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="23638-150">Принудительно применяет восстановление, чтобы повторно рассчитать все зависимости, если файл блокировки уже существует.</span><span class="sxs-lookup"><span data-stu-id="23638-150">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="23638-151">Выводит краткую справку по команде.</span><span class="sxs-lookup"><span data-stu-id="23638-151">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="23638-152">Предупреждение о сбоях источников выдается только при наличии пакетов, соответствующих требованию к версии.</span><span class="sxs-lookup"><span data-stu-id="23638-152">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="23638-153">Позволяет остановить команду и дождаться, пока пользователь введет данные или выполнит действие (например, завершит проверку подлинности).</span><span class="sxs-lookup"><span data-stu-id="23638-153">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="23638-154">Начиная с .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="23638-154">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="23638-155">Расположение выходных данных для записи файла блокировки проекта.</span><span class="sxs-lookup"><span data-stu-id="23638-155">Output location where project lock file is written.</span></span> <span data-ttu-id="23638-156">По умолчанию используется *PROJECT_ROOT\packages.lock.json*.</span><span class="sxs-lookup"><span data-stu-id="23638-156">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="23638-157">Не разрешать обновление файла блокировки проекта.</span><span class="sxs-lookup"><span data-stu-id="23638-157">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="23638-158">Отключает кэширование HTTP-запросов.</span><span class="sxs-lookup"><span data-stu-id="23638-158">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="23638-159">При восстановлении проекта с перекрестными ссылками между проектами восстанавливает только корневой проект, но не ссылки.</span><span class="sxs-lookup"><span data-stu-id="23638-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="23638-160">Задает каталог для восстановленных пакетов.</span><span class="sxs-lookup"><span data-stu-id="23638-160">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="23638-161">Задает среду выполнения для восстановления пакетов.</span><span class="sxs-lookup"><span data-stu-id="23638-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="23638-162">Это позволяет восстановить пакеты для сред выполнения, явно не указанных в теге `<RuntimeIdentifiers>` файла *CSPROJ*.</span><span class="sxs-lookup"><span data-stu-id="23638-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="23638-163">Список идентификаторов сред выполнения (RID) см. в [каталоге RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="23638-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="23638-164">Чтобы указать несколько идентификаторов RID, задайте этот параметр несколько раз.</span><span class="sxs-lookup"><span data-stu-id="23638-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="23638-165">Указывает URI источника пакета NuGet для использования во время операции восстановления.</span><span class="sxs-lookup"><span data-stu-id="23638-165">Specifies the URI of the NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="23638-166">Этот параметр переопределяет все источники, указанные в файлах *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="23638-166">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="23638-167">Чтобы указать несколько источников, задайте этот параметр несколько раз.</span><span class="sxs-lookup"><span data-stu-id="23638-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lock-file`**

  <span data-ttu-id="23638-168">Включает создание файла блокировки проекта и использование этого файла при восстановлении.</span><span class="sxs-lookup"><span data-stu-id="23638-168">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="23638-169">Задает уровень детализации команды.</span><span class="sxs-lookup"><span data-stu-id="23638-169">Sets the verbosity level of the command.</span></span> <span data-ttu-id="23638-170">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="23638-170">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="23638-171">Значение по умолчанию — `minimal`.</span><span class="sxs-lookup"><span data-stu-id="23638-171">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="23638-172">Примеры</span><span class="sxs-lookup"><span data-stu-id="23638-172">Examples</span></span>

- <span data-ttu-id="23638-173">Восстановление зависимостей и средств для проекта в текущем каталоге:</span><span class="sxs-lookup"><span data-stu-id="23638-173">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="23638-174">Восстановление зависимостей и средств для проекта `app1` по указанному пути:</span><span class="sxs-lookup"><span data-stu-id="23638-174">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

  ```dotnetcli
  dotnet restore ./projects/app1/app1.csproj
  ```

- <span data-ttu-id="23638-175">Восстановление зависимостей и средств для проекта в текущем каталоге с использованием пути к файлу, заданного в качестве источника:</span><span class="sxs-lookup"><span data-stu-id="23638-175">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="23638-176">Восстановление зависимостей и средств для проекта в текущем каталоге с использованием двух путей к файлу, заданных в качестве источника:</span><span class="sxs-lookup"><span data-stu-id="23638-176">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="23638-177">Восстановление зависимостей и средств для проекта в текущем каталоге с подробными выходными данными:</span><span class="sxs-lookup"><span data-stu-id="23638-177">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
