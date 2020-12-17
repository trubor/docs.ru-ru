---
title: Команда dotnet sln
description: Команда dotnet-sln предоставляет удобный способ добавлять проекты в файл решений, удалять или перечислять их.
ms.date: 12/07/2020
ms.openlocfilehash: 480634550f6fa1983bb46f51b439dc8a686ead3c
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851706"
---
# <a name="dotnet-sln"></a><span data-ttu-id="e8b01-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="e8b01-103">dotnet sln</span></span>

<span data-ttu-id="e8b01-104">**Эта статья относится к следующему:** ✔️ пакет SDK для .NET Core 2.x и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="e8b01-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e8b01-105">name</span><span class="sxs-lookup"><span data-stu-id="e8b01-105">Name</span></span>

<span data-ttu-id="e8b01-106">`dotnet sln` — перечисляет или изменяет проекты в файле решения .NET.</span><span class="sxs-lookup"><span data-stu-id="e8b01-106">`dotnet sln` - Lists or modifies the projects in a .NET solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e8b01-107">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="e8b01-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a><span data-ttu-id="e8b01-108">Описание</span><span class="sxs-lookup"><span data-stu-id="e8b01-108">Description</span></span>

<span data-ttu-id="e8b01-109">Команда `dotnet sln` предоставляет удобный способ перечислять и изменять проекты в файле решений.</span><span class="sxs-lookup"><span data-stu-id="e8b01-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="e8b01-110">Для использования команды `dotnet sln` файл решения должен уже существовать.</span><span class="sxs-lookup"><span data-stu-id="e8b01-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="e8b01-111">Если необходимо создать его, используйте команду [dotnet new](dotnet-new.md), как в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="e8b01-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="e8b01-112">Аргументы</span><span class="sxs-lookup"><span data-stu-id="e8b01-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="e8b01-113">Используемый файл решений.</span><span class="sxs-lookup"><span data-stu-id="e8b01-113">The solution file to use.</span></span> <span data-ttu-id="e8b01-114">Если этот аргумент упущен, команда ищет текущий каталог для него.</span><span class="sxs-lookup"><span data-stu-id="e8b01-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="e8b01-115">Если файл решения или несколько файлов решения не найдены, команда завершается ошибкой.</span><span class="sxs-lookup"><span data-stu-id="e8b01-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="e8b01-116">Параметры</span><span class="sxs-lookup"><span data-stu-id="e8b01-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e8b01-117">Выводит описание использования команды.</span><span class="sxs-lookup"><span data-stu-id="e8b01-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="e8b01-118">Команды</span><span class="sxs-lookup"><span data-stu-id="e8b01-118">Commands</span></span>

### `list`

<span data-ttu-id="e8b01-119">Перечисляет все проекты в файле решения.</span><span class="sxs-lookup"><span data-stu-id="e8b01-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="e8b01-120">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="e8b01-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="e8b01-121">Аргументы</span><span class="sxs-lookup"><span data-stu-id="e8b01-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="e8b01-122">Используемый файл решений.</span><span class="sxs-lookup"><span data-stu-id="e8b01-122">The solution file to use.</span></span> <span data-ttu-id="e8b01-123">Если этот аргумент упущен, команда ищет текущий каталог для него.</span><span class="sxs-lookup"><span data-stu-id="e8b01-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="e8b01-124">Если файл решения или несколько файлов решения не найдены, команда завершается ошибкой.</span><span class="sxs-lookup"><span data-stu-id="e8b01-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="e8b01-125">Параметры</span><span class="sxs-lookup"><span data-stu-id="e8b01-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e8b01-126">Выводит описание использования команды.</span><span class="sxs-lookup"><span data-stu-id="e8b01-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="e8b01-127">Добавление проектов в файл решения.</span><span class="sxs-lookup"><span data-stu-id="e8b01-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="e8b01-128">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="e8b01-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="e8b01-129">Аргументы</span><span class="sxs-lookup"><span data-stu-id="e8b01-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="e8b01-130">Используемый файл решений.</span><span class="sxs-lookup"><span data-stu-id="e8b01-130">The solution file to use.</span></span> <span data-ttu-id="e8b01-131">Если он не указан, команда ищет его в текущем каталоге и завершается ошибкой, если имеется несколько файлов решения.</span><span class="sxs-lookup"><span data-stu-id="e8b01-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="e8b01-132">Путь к проекту или проектам, который необходимо добавить в решение.</span><span class="sxs-lookup"><span data-stu-id="e8b01-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="e8b01-133">Расширения [стандартной маски](https://en.wikipedia.org/wiki/Glob_(programming)) оболочки Unix/Linux правильно обрабатываются командой `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="e8b01-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="e8b01-134">Параметры</span><span class="sxs-lookup"><span data-stu-id="e8b01-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e8b01-135">Выводит описание использования команды.</span><span class="sxs-lookup"><span data-stu-id="e8b01-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="e8b01-136">Поместите проекты в корень решения, и вам не нужно будет создавать папку решения.</span><span class="sxs-lookup"><span data-stu-id="e8b01-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="e8b01-137">Доступно, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e8b01-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder <PATH>`**

  <span data-ttu-id="e8b01-138">Путь к папке назначения решения, в которую будут добавлены проекты.</span><span class="sxs-lookup"><span data-stu-id="e8b01-138">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="e8b01-139">Доступно, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e8b01-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="e8b01-140">Удаляет один или несколько проектов из файла решений.</span><span class="sxs-lookup"><span data-stu-id="e8b01-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="e8b01-141">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="e8b01-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="e8b01-142">Аргументы</span><span class="sxs-lookup"><span data-stu-id="e8b01-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="e8b01-143">Используемый файл решений.</span><span class="sxs-lookup"><span data-stu-id="e8b01-143">The solution file to use.</span></span> <span data-ttu-id="e8b01-144">Если он не указан, команда ищет его в текущем каталоге и завершается ошибкой, если имеется несколько файлов решения.</span><span class="sxs-lookup"><span data-stu-id="e8b01-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="e8b01-145">Путь к проекту или проектам, который необходимо добавить в решение.</span><span class="sxs-lookup"><span data-stu-id="e8b01-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="e8b01-146">Расширения [стандартной маски](https://en.wikipedia.org/wiki/Glob_(programming)) оболочки Unix/Linux правильно обрабатываются командой `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="e8b01-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="e8b01-147">Параметры</span><span class="sxs-lookup"><span data-stu-id="e8b01-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e8b01-148">Выводит описание использования команды.</span><span class="sxs-lookup"><span data-stu-id="e8b01-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="e8b01-149">Примеры</span><span class="sxs-lookup"><span data-stu-id="e8b01-149">Examples</span></span>

- <span data-ttu-id="e8b01-150">Перечисление проектов в решении:</span><span class="sxs-lookup"><span data-stu-id="e8b01-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="e8b01-151">Добавление проекта C# в решение:</span><span class="sxs-lookup"><span data-stu-id="e8b01-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="e8b01-152">Удаление проекта C# из решения:</span><span class="sxs-lookup"><span data-stu-id="e8b01-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="e8b01-153">Добавление нескольких проектов C# в корень решения:</span><span class="sxs-lookup"><span data-stu-id="e8b01-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="e8b01-154">Добавление нескольких проектов C# в решение:</span><span class="sxs-lookup"><span data-stu-id="e8b01-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="e8b01-155">Удаление нескольких проектов C# из решения:</span><span class="sxs-lookup"><span data-stu-id="e8b01-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="e8b01-156">Добавление нескольких проектов C# в решение с помощью стандартной маски (только Unix/Linux):</span><span class="sxs-lookup"><span data-stu-id="e8b01-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="e8b01-157">Добавление нескольких проектов C# в решение с помощью стандартной маски (только Windows PowerShell):</span><span class="sxs-lookup"><span data-stu-id="e8b01-157">Add multiple C# projects to a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add (ls -r **/*.csproj)
  ```

- <span data-ttu-id="e8b01-158">Удаление нескольких проектов C# из решения с помощью стандартной маски (только Unix/Linux):</span><span class="sxs-lookup"><span data-stu-id="e8b01-158">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- <span data-ttu-id="e8b01-159">Удаление нескольких проектов C# из решения с помощью стандартной маски (только Windows PowerShell):</span><span class="sxs-lookup"><span data-stu-id="e8b01-159">Remove multiple C# projects from a solution using a globbing pattern (Windows PowerShell only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove (ls -r **/*.csproj)
  ```

- <span data-ttu-id="e8b01-160">Создайте решение, консольное приложение и две библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="e8b01-160">Create a solution, a console app, and two class libraries.</span></span> <span data-ttu-id="e8b01-161">Добавьте проекты в решение и используйте параметр `--solution-folder` `dotnet sln`, чтобы сгруппировать библиотеки классов в папку решения.</span><span class="sxs-lookup"><span data-stu-id="e8b01-161">Add the projects to the solution, and use the `--solution-folder` option of `dotnet sln` to organize the class libraries into a solution folder.</span></span>

  ```dotnetcli
  dotnet new sln -n mysolution
  dotnet new console -o myapp
  dotnet new classlib -o mylib1
  dotnet new classlib -o mylib2
  dotnet sln mysolution.sln add myapp\myapp.csproj
  dotnet sln mysolution.sln add mylib1\mylib1.csproj --solution-folder mylibs
  dotnet sln mysolution.sln add mylib2\mylib2.csproj --solution-folder mylibs
  ```

  <span data-ttu-id="e8b01-162">На следующем снимке экрана показан результат в **обозревателе решений** Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="e8b01-162">The following screenshot shows the result in Visual Studio 2019 **Solution Explorer**:</span></span>

  :::image type="content" source="media/dotnet-sln/dotnet-sln-solution-folder.png" alt-text="Обозреватель решений, показывающий проекты библиотек классов, сгруппированные в папке решения.":::
