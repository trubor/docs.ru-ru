---
title: Команда dotnet tool install
description: Команда dotnet tool install устанавливает указанное средство .NET на компьютер.
ms.date: 02/14/2020
ms.openlocfilehash: b04e7fd24edce5d5da67cdd83fbea797118689b4
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206485"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="3354b-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="3354b-103">dotnet tool install</span></span>

<span data-ttu-id="3354b-104">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="3354b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3354b-105">name</span><span class="sxs-lookup"><span data-stu-id="3354b-105">Name</span></span>

<span data-ttu-id="3354b-106">`dotnet tool install` устанавливает указанное [средство .NET](global-tools.md) на компьютер.</span><span class="sxs-lookup"><span data-stu-id="3354b-106">`dotnet tool install` - Installs the specified [.NET tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3354b-107">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="3354b-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a><span data-ttu-id="3354b-108">Описание</span><span class="sxs-lookup"><span data-stu-id="3354b-108">Description</span></span>

<span data-ttu-id="3354b-109">Команда `dotnet tool install` предоставляет способ установки средств .NET на компьютере.</span><span class="sxs-lookup"><span data-stu-id="3354b-109">The `dotnet tool install` command provides a way for you to install .NET tools on your machine.</span></span> <span data-ttu-id="3354b-110">Чтобы использовать команду, укажите один из следующих параметров установки:</span><span class="sxs-lookup"><span data-stu-id="3354b-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="3354b-111">Чтобы установить глобальный инструмент в расположение по умолчанию, используйте параметр `--global`.</span><span class="sxs-lookup"><span data-stu-id="3354b-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="3354b-112">Чтобы установить глобальный инструмент в расположение, указанное пользователем, используйте параметр `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="3354b-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="3354b-113">Чтобы установить локальный инструмент, пропустите параметры `--global` и `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="3354b-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="3354b-114">**Локальные средства доступны в пакете SDK для .NET Core, начиная с версии 3.0.**</span><span class="sxs-lookup"><span data-stu-id="3354b-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="3354b-115">Глобальные средства устанавливаются в следующие каталоги по умолчанию при выборе параметра `-g` или `--global`:</span><span class="sxs-lookup"><span data-stu-id="3354b-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="3354b-116">Операционная система</span><span class="sxs-lookup"><span data-stu-id="3354b-116">OS</span></span>          | <span data-ttu-id="3354b-117">Path</span><span class="sxs-lookup"><span data-stu-id="3354b-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="3354b-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="3354b-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="3354b-119">Windows</span><span class="sxs-lookup"><span data-stu-id="3354b-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="3354b-120">Локальные средства добавляются в файл *dotnet-tools.json* в каталоге *. config* в текущем каталоге.</span><span class="sxs-lookup"><span data-stu-id="3354b-120">Local tools are added to a *dotnet-tools.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="3354b-121">Если файл манифеста еще не существует, создайте его, выполнив следующую команду:</span><span class="sxs-lookup"><span data-stu-id="3354b-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="3354b-122">Дополнительные сведения см. в разделе [Установка глобального средства](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="3354b-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="3354b-123">Аргументы</span><span class="sxs-lookup"><span data-stu-id="3354b-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="3354b-124">Имя или идентификатор пакета NuGet, который содержит устанавливаемое средство .NET.</span><span class="sxs-lookup"><span data-stu-id="3354b-124">Name/ID of the NuGet package that contains the .NET tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="3354b-125">Параметры</span><span class="sxs-lookup"><span data-stu-id="3354b-125">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="3354b-126">Добавляет дополнительный источник пакета NuGet для использования во время установки.</span><span class="sxs-lookup"><span data-stu-id="3354b-126">Adds an additional NuGet package source to use during installation.</span></span> <span data-ttu-id="3354b-127">Доступ к каналам осуществляется параллельно, а не последовательно в некотором порядке приоритета.</span><span class="sxs-lookup"><span data-stu-id="3354b-127">Feeds are accessed in parallel, not sequentially in some order of precedence.</span></span> <span data-ttu-id="3354b-128">Если один и тот же пакет и версия находятся в нескольких каналах, используется самый быстрый канал.</span><span class="sxs-lookup"><span data-stu-id="3354b-128">If the same package and version is in multiple feeds, the fastest feed wins.</span></span> <span data-ttu-id="3354b-129">Дополнительные сведения см. в разделе [Процесс установки пакета NuGet](/nuget/concepts/package-installation-process).</span><span class="sxs-lookup"><span data-stu-id="3354b-129">For more information, see [What happens when a NuGet package is installed?](/nuget/concepts/package-installation-process).</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="3354b-130">Файл конфигурации NuGet (*nuget.config*), который будет использоваться.</span><span class="sxs-lookup"><span data-stu-id="3354b-130">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="3354b-131">Указывает [требуемую версию .NET Framework](../../standard/frameworks.md) для установки средства.</span><span class="sxs-lookup"><span data-stu-id="3354b-131">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="3354b-132">По умолчанию пакет SDK для .NET пытается выбрать наиболее подходящую версию .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3354b-132">By default, the .NET SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="3354b-133">Указывает, что установка происходит на уровне пользователя.</span><span class="sxs-lookup"><span data-stu-id="3354b-133">Specifies that the installation is user wide.</span></span> <span data-ttu-id="3354b-134">Не может использоваться вместе с параметром `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="3354b-134">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="3354b-135">Пропуск параметров `--global` и `--tool-path` задает установку локального средства.</span><span class="sxs-lookup"><span data-stu-id="3354b-135">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="3354b-136">Выводит краткую справку по команде.</span><span class="sxs-lookup"><span data-stu-id="3354b-136">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="3354b-137">Указывает место установки глобального средства.</span><span class="sxs-lookup"><span data-stu-id="3354b-137">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="3354b-138">Путь может быть абсолютным или относительным.</span><span class="sxs-lookup"><span data-stu-id="3354b-138">PATH can be absolute or relative.</span></span> <span data-ttu-id="3354b-139">Если путь не существует, команда пытается создать его.</span><span class="sxs-lookup"><span data-stu-id="3354b-139">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="3354b-140">Пропуск параметров `--global` и `--tool-path` задает установку локального средства.</span><span class="sxs-lookup"><span data-stu-id="3354b-140">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="3354b-141">Задает уровень детализации команды.</span><span class="sxs-lookup"><span data-stu-id="3354b-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3354b-142">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="3354b-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="3354b-143">Версия средства для установки.</span><span class="sxs-lookup"><span data-stu-id="3354b-143">The version of the tool to install.</span></span> <span data-ttu-id="3354b-144">По умолчанию устанавливается последняя стабильная версия пакета.</span><span class="sxs-lookup"><span data-stu-id="3354b-144">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="3354b-145">Используйте этот параметр для установки предварительной версии или предыдущей версии средства.</span><span class="sxs-lookup"><span data-stu-id="3354b-145">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="3354b-146">Примеры</span><span class="sxs-lookup"><span data-stu-id="3354b-146">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="3354b-147">Устанавливает глобальное средство [dotnetsay](https://www.nuget.org/packages/dotnetsay/) в расположении по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="3354b-147">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="3354b-148">Устанавливает [dotnetsay](https://www.nuget.org/packages/dotnetsay/) в качестве глобального инструмента в определенном каталоге Windows.</span><span class="sxs-lookup"><span data-stu-id="3354b-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="3354b-149">Устанавливает [dotnetsay](https://www.nuget.org/packages/dotnetsay/) в качестве глобального инструмента в определенном каталоге Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="3354b-149">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="3354b-150">Устанавливает версию 2.0.0 в качестве глобального средства [dotnetsay](https://www.nuget.org/packages/dotnetsay/):</span><span class="sxs-lookup"><span data-stu-id="3354b-150">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="3354b-151">Устанавливает [dotnetsay](https://www.nuget.org/packages/dotnetsay/) в качестве локального средства для текущего каталога.</span><span class="sxs-lookup"><span data-stu-id="3354b-151">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="3354b-152">См. также</span><span class="sxs-lookup"><span data-stu-id="3354b-152">See also</span></span>

- [<span data-ttu-id="3354b-153">Средства .NET</span><span class="sxs-lookup"><span data-stu-id="3354b-153">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="3354b-154">Учебник. Установка и использование глобального средства .NET с помощью интерфейса командной строки .NET</span><span class="sxs-lookup"><span data-stu-id="3354b-154">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="3354b-155">Учебник. Установка и использование локального средства .NET с помощью интерфейса командной строки .NET</span><span class="sxs-lookup"><span data-stu-id="3354b-155">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
