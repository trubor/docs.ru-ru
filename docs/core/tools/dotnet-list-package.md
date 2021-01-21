---
title: Команда dotnet add package
description: Команду dotnet list package удобно использовать для получения списка ссылок на пакеты для проекта или решения.
ms.date: 11/11/2020
ms.openlocfilehash: 684b73dec553a424252e1368c265847622fb7850
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189900"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="99113-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="99113-103">dotnet list package</span></span>

<span data-ttu-id="99113-104">**Эта статья относится к следующему** ✔️ SDK для .NET Core 2.2 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="99113-104">**This article applies to:** ✔️ .NET Core 2.2 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="99113-105">name</span><span class="sxs-lookup"><span data-stu-id="99113-105">Name</span></span>

<span data-ttu-id="99113-106">`dotnet list package` — перечисляет ссылки на пакет для проекта или решения.</span><span class="sxs-lookup"><span data-stu-id="99113-106">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="99113-107">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="99113-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config <SOURCE>]
    [--deprecated]
    [--framework <FRAMEWORK>] [--highest-minor] [--highest-patch]
    [--include-prerelease] [--include-transitive] [--interactive]
    [--outdated] [--source <SOURCE>] [-v|--verbosity <LEVEL>]

dotnet list package -h|--help
```

## <a name="description"></a><span data-ttu-id="99113-108">Описание</span><span class="sxs-lookup"><span data-stu-id="99113-108">Description</span></span>

<span data-ttu-id="99113-109">Команду `dotnet list package` удобно использовать для получения списка всех ссылок на пакеты NuGet для определенного проекта или решения.</span><span class="sxs-lookup"><span data-stu-id="99113-109">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="99113-110">Сначала нужно создать проект, чтобы получить ресурсы, необходимые для обработки этой командой.</span><span class="sxs-lookup"><span data-stu-id="99113-110">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="99113-111">В следующем примере показаны выходные данные команды `dotnet list package` для проекта [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis):</span><span class="sxs-lookup"><span data-stu-id="99113-111">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="99113-112">В столбце **Requested** приводится ссылка на версию пакета, указанную в файле проекта. Это может быть и диапазон версий.</span><span class="sxs-lookup"><span data-stu-id="99113-112">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="99113-113">В столбце **Resolved** указана версия, которая сейчас используется в проекте. Это значение всегда является одиночным.</span><span class="sxs-lookup"><span data-stu-id="99113-113">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="99113-114">Символ `(A)`, отображающийся рядом с именами пакетов, обозначает неявные ссылки на пакеты. Такие ссылки получены из параметров проекта (тип `Sdk`, свойство `<TargetFramework>` или `<TargetFrameworks>` и т. д.)</span><span class="sxs-lookup"><span data-stu-id="99113-114">The packages displaying an `(A)` right next to their names represent implicit package references that are inferred from your project settings (`Sdk` type, or `<TargetFramework>` or `<TargetFrameworks>` property).</span></span>

<span data-ttu-id="99113-115">Используйте параметр `--outdated`, чтобы узнать, доступны ли новые версии пакетов, которые вы используете в проектах.</span><span class="sxs-lookup"><span data-stu-id="99113-115">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="99113-116">По умолчанию параметр `--outdated` выводит список последних стабильных версий пакетов, если разрешенная версия не является предварительной версией.</span><span class="sxs-lookup"><span data-stu-id="99113-116">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="99113-117">Чтобы при отображении списка новых версий отображались и предварительные версии, укажите параметр `--include-prerelease`.</span><span class="sxs-lookup"><span data-stu-id="99113-117">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="99113-118">Ниже приведены выходные данные команды `dotnet list package --outdated --include-prerelease` для тоже же проекта, как и в предыдущем примере:</span><span class="sxs-lookup"><span data-stu-id="99113-118">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

<span data-ttu-id="99113-119">Чтобы узнать, есть ли у проекта транзитивные зависимости, воспользуйтесь параметром `--include-transitive`.</span><span class="sxs-lookup"><span data-stu-id="99113-119">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="99113-120">Транзитивные зависимости возникают при добавлении пакета в проект, который в свою очередь зависит от другого пакета.</span><span class="sxs-lookup"><span data-stu-id="99113-120">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="99113-121">В следующем примере показаны выходные данные выполнения команды `dotnet list package --include-transitive` для проекта [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin), в которых отображаются пакеты верхнего уровня и пакеты, от которых они зависят:</span><span class="sxs-lookup"><span data-stu-id="99113-121">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a><span data-ttu-id="99113-122">Аргументы</span><span class="sxs-lookup"><span data-stu-id="99113-122">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="99113-123">Файл проекта или решения для выполнения операции.</span><span class="sxs-lookup"><span data-stu-id="99113-123">The project or solution file to operate on.</span></span> <span data-ttu-id="99113-124">Если он не указан, команда ищет текущий каталог для него.</span><span class="sxs-lookup"><span data-stu-id="99113-124">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="99113-125">Если найдено несколько решений или проектов, появится сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="99113-125">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="99113-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="99113-126">Options</span></span>

- **`--config <SOURCE>`**

  <span data-ttu-id="99113-127">Источники NuGet, используемые при поиске более новых версий пакетов.</span><span class="sxs-lookup"><span data-stu-id="99113-127">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="99113-128">Требует указать параметр `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="99113-128">Requires the `--outdated` option.</span></span>

- **`--deprecated`**

  <span data-ttu-id="99113-129">Отображает нерекомендуемые пакеты.</span><span class="sxs-lookup"><span data-stu-id="99113-129">Displays packages that have been deprecated.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="99113-130">Отображает только пакеты для указанной [целевой платформы](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="99113-130">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="99113-131">Чтобы указать несколько платформ, задайте параметр несколько раз.</span><span class="sxs-lookup"><span data-stu-id="99113-131">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="99113-132">Например, `--framework netcoreapp2.2 --framework netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="99113-132">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

- **`-h|--help`**

  <span data-ttu-id="99113-133">Выводит краткую справку по команде.</span><span class="sxs-lookup"><span data-stu-id="99113-133">Prints out a short help for the command.</span></span>

- **`--highest-minor`**

  <span data-ttu-id="99113-134">Учитывает только пакеты с соответствующим номером основной версии при поиске более новых версий пакетов.</span><span class="sxs-lookup"><span data-stu-id="99113-134">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="99113-135">Требует указать параметр `--outdated` или `--deprecated`.</span><span class="sxs-lookup"><span data-stu-id="99113-135">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--highest-patch`**

  <span data-ttu-id="99113-136">Учитывает только пакеты с соответствующими номерами основной и дополнительной версий при поиске более новых версий пакетов.</span><span class="sxs-lookup"><span data-stu-id="99113-136">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="99113-137">Требует указать параметр `--outdated` или `--deprecated`.</span><span class="sxs-lookup"><span data-stu-id="99113-137">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--include-prerelease`**

  <span data-ttu-id="99113-138">Учитывает пакеты с предварительными версиями при поиске более новых версий пакетов.</span><span class="sxs-lookup"><span data-stu-id="99113-138">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="99113-139">Требует указать параметр `--outdated` или `--deprecated`.</span><span class="sxs-lookup"><span data-stu-id="99113-139">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`--include-transitive`**

  <span data-ttu-id="99113-140">Выводит список транзитивных пакетов, кроме пакетов верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="99113-140">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="99113-141">Указав этот параметр, вы получите список пакетов, от которых зависят пакеты верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="99113-141">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

- **`--interactive`**

  <span data-ttu-id="99113-142">Позволяет команде остановиться и дождаться, пока пользователь выполнит действие или введет данные.</span><span class="sxs-lookup"><span data-stu-id="99113-142">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="99113-143">Например, чтобы завершить проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="99113-143">For example, to complete authentication.</span></span> <span data-ttu-id="99113-144">Доступно, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="99113-144">Available since .NET Core 3.0 SDK.</span></span>

- **`--outdated`**

  <span data-ttu-id="99113-145">Позволяет получить список пакетов, для которых доступны более новые версии.</span><span class="sxs-lookup"><span data-stu-id="99113-145">Lists packages that have newer versions available.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="99113-146">Источники NuGet, используемые при поиске более новых версий пакетов.</span><span class="sxs-lookup"><span data-stu-id="99113-146">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="99113-147">Требует указать параметр `--outdated` или `--deprecated`.</span><span class="sxs-lookup"><span data-stu-id="99113-147">Requires the `--outdated` or `--deprecated` option.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="99113-148">Задает уровень детализации MSBuild.</span><span class="sxs-lookup"><span data-stu-id="99113-148">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="99113-149">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="99113-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="99113-150">Значение по умолчанию — `minimal`.</span><span class="sxs-lookup"><span data-stu-id="99113-150">The default is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="99113-151">Примеры</span><span class="sxs-lookup"><span data-stu-id="99113-151">Examples</span></span>

- <span data-ttu-id="99113-152">Вывод списка ссылок на пакеты определенного проекта:</span><span class="sxs-lookup"><span data-stu-id="99113-152">List package references of a specific project:</span></span>

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- <span data-ttu-id="99113-153">Вывод списка ссылок на пакеты, для которых доступны более новые версии, включая предварительные версии:</span><span class="sxs-lookup"><span data-stu-id="99113-153">List package references that have newer versions available, including prerelease versions:</span></span>

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- <span data-ttu-id="99113-154">Вывод списка ссылок на пакеты для определенной целевой платформы:</span><span class="sxs-lookup"><span data-stu-id="99113-154">List package references for a specific target framework:</span></span>

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
