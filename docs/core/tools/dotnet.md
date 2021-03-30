---
title: Команда dotnet
description: Узнайте о команде dotnet (универсальном драйвере для CLI .NET) и о том, как ее использовать.
ms.date: 11/11/2020
ms.openlocfilehash: 33c5f9d22166b818f5c860c4f4632d359f686919
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874541"
---
# <a name="dotnet-command"></a><span data-ttu-id="f323c-103">Команда dotnet</span><span class="sxs-lookup"><span data-stu-id="f323c-103">dotnet command</span></span>

<span data-ttu-id="f323c-104">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="f323c-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f323c-105">name</span><span class="sxs-lookup"><span data-stu-id="f323c-105">Name</span></span>

<span data-ttu-id="f323c-106">`dotnet` — универсальный драйвер для интерфейса командной строки .NET (CLI).</span><span class="sxs-lookup"><span data-stu-id="f323c-106">`dotnet` - The generic driver for the .NET CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f323c-107">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="f323c-107">Synopsis</span></span>

<span data-ttu-id="f323c-108">Чтобы получить сведения о среде и доступных командах, выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="f323c-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

<span data-ttu-id="f323c-109">Выполнение команды (требуется установка пакета SDK):</span><span class="sxs-lookup"><span data-stu-id="f323c-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

<span data-ttu-id="f323c-110">Запуск приложения:</span><span class="sxs-lookup"><span data-stu-id="f323c-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="f323c-111">Команда `--roll-forward` доступна, начиная с версии .NET Core 3.x.</span><span class="sxs-lookup"><span data-stu-id="f323c-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="f323c-112">Для .NET Core 2.x следует использовать `--roll-forward-on-no-candidate-fx`.</span><span class="sxs-lookup"><span data-stu-id="f323c-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="f323c-113">Описание</span><span class="sxs-lookup"><span data-stu-id="f323c-113">Description</span></span>

<span data-ttu-id="f323c-114">Команда `dotnet` выполняет две функции:</span><span class="sxs-lookup"><span data-stu-id="f323c-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="f323c-115">Она предоставляет команды для работы с проектами .NET.</span><span class="sxs-lookup"><span data-stu-id="f323c-115">It provides commands for working with .NET projects.</span></span>

  <span data-ttu-id="f323c-116">Например, команда [`dotnet build`](dotnet-build.md) выполняет построение проекта.</span><span class="sxs-lookup"><span data-stu-id="f323c-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="f323c-117">Каждая команда определяет свои параметры и аргументы.</span><span class="sxs-lookup"><span data-stu-id="f323c-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="f323c-118">Все команды поддерживают параметр `--help`, позволяющий вывести краткую справку по их использованию.</span><span class="sxs-lookup"><span data-stu-id="f323c-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="f323c-119">Она запускает приложения .NET.</span><span class="sxs-lookup"><span data-stu-id="f323c-119">It runs .NET applications.</span></span>

  <span data-ttu-id="f323c-120">Для запуска приложения необходимо указать путь к его файлу `.dll`.</span><span class="sxs-lookup"><span data-stu-id="f323c-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="f323c-121">Чтобы запустить приложение, необходимо найти и выполнить точку входа, которая в случае использования консольных приложений является методом `Main`.</span><span class="sxs-lookup"><span data-stu-id="f323c-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="f323c-122">Например, команда `dotnet myapp.dll` запускает приложение `myapp`.</span><span class="sxs-lookup"><span data-stu-id="f323c-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="f323c-123">Дополнительные сведения о параметрах развертывания см. в статье [Развертывание приложений .NET](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="f323c-123">See [.NET application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="f323c-124">Параметры</span><span class="sxs-lookup"><span data-stu-id="f323c-124">Options</span></span>

<span data-ttu-id="f323c-125">Доступны параметры для `dotnet`, для выполнения команды, а также для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="f323c-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="f323c-126">Параметры для dotnet</span><span class="sxs-lookup"><span data-stu-id="f323c-126">Options for dotnet by itself</span></span>

<span data-ttu-id="f323c-127">Для `dotnet` доступны следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="f323c-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="f323c-128">Например, `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="f323c-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="f323c-129">Выводит сведения о среде.</span><span class="sxs-lookup"><span data-stu-id="f323c-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="f323c-130">Выводит подробные сведения об установке .NET и среде компьютера, например текущую операционную систему и фиксацию SHA версии .NET.</span><span class="sxs-lookup"><span data-stu-id="f323c-130">Prints out detailed information about a .NET installation and the machine environment, such as the current operating system, and commit SHA of the .NET version.</span></span>

- **`--version`**

  <span data-ttu-id="f323c-131">Выводит версию используемого пакета SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="f323c-131">Prints out the version of the .NET SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="f323c-132">Выводит список установленных сред выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="f323c-132">Prints out a list of the installed .NET runtimes.</span></span> <span data-ttu-id="f323c-133">Версия x86 пакета SDK содержит только среды выполнения x86, а в версии x64 пакета SDK содержатся только среды выполнения x64.</span><span class="sxs-lookup"><span data-stu-id="f323c-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="f323c-134">Выводит список установленных пакетов SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="f323c-134">Prints out a list of the installed .NET SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f323c-135">Выводит список доступных команд.</span><span class="sxs-lookup"><span data-stu-id="f323c-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="f323c-136">Параметры пакета SDK для выполнения команды</span><span class="sxs-lookup"><span data-stu-id="f323c-136">SDK options for running a command</span></span>

<span data-ttu-id="f323c-137">Для `dotnet` с командой доступны следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="f323c-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="f323c-138">Например, `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="f323c-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="f323c-139">Включает вывод диагностических данных.</span><span class="sxs-lookup"><span data-stu-id="f323c-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f323c-140">Задает уровень детализации команды.</span><span class="sxs-lookup"><span data-stu-id="f323c-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f323c-141">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f323c-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f323c-142">Поддерживается не во всех командах.</span><span class="sxs-lookup"><span data-stu-id="f323c-142">Not supported in every command.</span></span> <span data-ttu-id="f323c-143">Дополнительные сведения см. на странице соответствующей команды.</span><span class="sxs-lookup"><span data-stu-id="f323c-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f323c-144">Выводит на экран документацию для определенной команды, например `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="f323c-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="f323c-145">Для каждой команды определяются относящиеся к ней параметры.</span><span class="sxs-lookup"><span data-stu-id="f323c-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="f323c-146">Список доступных для команды параметров можно просмотреть на соответствующей ей странице.</span><span class="sxs-lookup"><span data-stu-id="f323c-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="f323c-147">Параметры среды выполнения</span><span class="sxs-lookup"><span data-stu-id="f323c-147">Runtime options</span></span>

<span data-ttu-id="f323c-148">При запуске приложения в `dotnet` доступны следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="f323c-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="f323c-149">Например, `dotnet myapp.dll --roll-forward Major`.</span><span class="sxs-lookup"><span data-stu-id="f323c-149">For example, `dotnet myapp.dll --roll-forward Major`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="f323c-150">Путь, содержащий политику проверки и проверяемые сборки.</span><span class="sxs-lookup"><span data-stu-id="f323c-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="f323c-151">Путь к дополнительному файлу *.deps.json*.</span><span class="sxs-lookup"><span data-stu-id="f323c-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="f323c-152">Файл *deps.json* содержит список зависимостей, зависимости компиляции и сведения о версии, используемые для устранения конфликтов сборок.</span><span class="sxs-lookup"><span data-stu-id="f323c-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="f323c-153">Дополнительные сведения см. в разделе [Файлы конфигурации среды выполнения](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md) на GitHub.</span><span class="sxs-lookup"><span data-stu-id="f323c-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--depsfile <PATH_TO_DEPSFILE>`**

  <span data-ttu-id="f323c-154">Путь к файлу *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="f323c-154">Path to the *deps.json* file.</span></span> <span data-ttu-id="f323c-155">Файл конфигурации *deps.json* содержит информацию о зависимостях, необходимых для выполнения приложения.</span><span class="sxs-lookup"><span data-stu-id="f323c-155">A *deps.json* file is a configuration file that contains information about dependencies necessary to run the application.</span></span> <span data-ttu-id="f323c-156">Этот файл создается пакетом SDK для .NET.</span><span class="sxs-lookup"><span data-stu-id="f323c-156">This file is generated by the .NET SDK.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="f323c-157">Путь к файлу *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="f323c-157">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="f323c-158">Файл *runtimeconfig.json* представляет собой файл конфигурации, содержащий параметры среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="f323c-158">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="f323c-159">Дополнительные сведения см. в статье [Параметры конфигурации среды выполнения .NET](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="f323c-159">For more information, see [.NET run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="f323c-160">**`--roll-forward <SETTING>`** **Доступно, начиная с пакета SDK для .NET Core 3.0.**</span><span class="sxs-lookup"><span data-stu-id="f323c-160">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="f323c-161">Управляет применением наката к приложению.</span><span class="sxs-lookup"><span data-stu-id="f323c-161">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="f323c-162">`SETTING` может иметь одно из следующих значений.</span><span class="sxs-lookup"><span data-stu-id="f323c-162">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="f323c-163">Если тип не указан, по умолчанию используется вариант `Minor`.</span><span class="sxs-lookup"><span data-stu-id="f323c-163">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="f323c-164">`LatestPatch` — накат до версии с наибольшим номером исправления.</span><span class="sxs-lookup"><span data-stu-id="f323c-164">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="f323c-165">Отключает накат дополнительных версий.</span><span class="sxs-lookup"><span data-stu-id="f323c-165">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="f323c-166">`Minor` — накат до дополнительной версии со следующим по порядку возрастания номером, если запрошенная дополнительная версия отсутствует.</span><span class="sxs-lookup"><span data-stu-id="f323c-166">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="f323c-167">Если запрошенная дополнительная версия присутствует, используется политика LatestPatch.</span><span class="sxs-lookup"><span data-stu-id="f323c-167">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="f323c-168">`Major` — накат до основной версии со следующим по порядку возрастания или дополнительной версии с наименьшим номером, если запрошенная дополнительная версия отсутствует.</span><span class="sxs-lookup"><span data-stu-id="f323c-168">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="f323c-169">Если запрошенная основная версия присутствует, используется политика Minor.</span><span class="sxs-lookup"><span data-stu-id="f323c-169">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="f323c-170">`LatestMinor` — накат до дополнительной версии с наибольшим номером, даже если запрошенная дополнительная версия присутствует.</span><span class="sxs-lookup"><span data-stu-id="f323c-170">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="f323c-171">Предназначен для сценариев размещения компонентов.</span><span class="sxs-lookup"><span data-stu-id="f323c-171">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="f323c-172">`LatestMajor` — накат до основной версии с наибольшим номером и дополнительной версии с наибольшим номером, даже если запрошенная основная версия присутствует.</span><span class="sxs-lookup"><span data-stu-id="f323c-172">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="f323c-173">Предназначен для сценариев размещения компонентов.</span><span class="sxs-lookup"><span data-stu-id="f323c-173">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="f323c-174">`Disable` — накат не выполняется.</span><span class="sxs-lookup"><span data-stu-id="f323c-174">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="f323c-175">Привязка только к указанной версии.</span><span class="sxs-lookup"><span data-stu-id="f323c-175">Only bind to specified version.</span></span> <span data-ttu-id="f323c-176">Эта политика не рекомендуется для общего использования, поскольку отключает возможность наката до последних исправлений.</span><span class="sxs-lookup"><span data-stu-id="f323c-176">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="f323c-177">Это значение рекомендуется использовать только для тестирования.</span><span class="sxs-lookup"><span data-stu-id="f323c-177">This value is only recommended for testing.</span></span>

  <span data-ttu-id="f323c-178">Все параметры, кроме параметра `Disable`, будут использовать версию с последним доступным исправлением.</span><span class="sxs-lookup"><span data-stu-id="f323c-178">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

  <span data-ttu-id="f323c-179">Поведение наката также можно настроить в свойствах файла проекта, файла конфигурации среды выполнения и переменной среды.</span><span class="sxs-lookup"><span data-stu-id="f323c-179">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="f323c-180">Дополнительные сведения см. в разделе [Накат основной версии среды выполнения](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="f323c-180">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="f323c-181">**`--roll-forward-on-no-candidate-fx <N>`** **Доступно в пакете SDK для .NET Core 2.x.**</span><span class="sxs-lookup"><span data-stu-id="f323c-181">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="f323c-182">Определяет поведение, когда требуемая общая платформа недоступна.</span><span class="sxs-lookup"><span data-stu-id="f323c-182">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="f323c-183">Параметр `N` может принимать следующие значения:</span><span class="sxs-lookup"><span data-stu-id="f323c-183">`N` can be:</span></span>

  - <span data-ttu-id="f323c-184">`0` — отключает увеличение дополнительных версий.</span><span class="sxs-lookup"><span data-stu-id="f323c-184">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="f323c-185">`1` — позволяет увеличивать дополнительный номер версии, но не основной.</span><span class="sxs-lookup"><span data-stu-id="f323c-185">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="f323c-186">Это поведение установлено по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f323c-186">This is the default behavior.</span></span>
  - <span data-ttu-id="f323c-187">`2` — включает увеличение основных и дополнительных версий.</span><span class="sxs-lookup"><span data-stu-id="f323c-187">`2` - Roll forward on minor and major versions.</span></span>

  <span data-ttu-id="f323c-188">Дополнительные сведения о накате можно найти в [этой статье](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="f323c-188">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="f323c-189">Начиная с .NET Core 3.0, этот параметр заменяется параметром `--roll-forward`, который следует использовать вместо него.</span><span class="sxs-lookup"><span data-stu-id="f323c-189">Starting with .NET Core 3.0, this option is superseded by `--roll-forward`, and that option should be used instead.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="f323c-190">Версия среды выполнения .NET, используемой для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="f323c-190">Version of the .NET runtime to use to run the application.</span></span>

  <span data-ttu-id="f323c-191">Этот параметр переопределяет версию первой ссылки на платформу в файле `.runtimeconfig.json` приложения.</span><span class="sxs-lookup"><span data-stu-id="f323c-191">This option overrides the version of the first framework reference in the application's `.runtimeconfig.json` file.</span></span> <span data-ttu-id="f323c-192">Таким образом, он работает правильно только с одной ссылкой на платформу.</span><span class="sxs-lookup"><span data-stu-id="f323c-192">This means it only works as expected if there's just one framework reference.</span></span> <span data-ttu-id="f323c-193">Если приложение содержит более одной ссылки на платформы, использование этого параметра может приводить к ошибкам.</span><span class="sxs-lookup"><span data-stu-id="f323c-193">If the application has more than one framework reference, using this option may cause errors.</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="f323c-194">Команды dotnet</span><span class="sxs-lookup"><span data-stu-id="f323c-194">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="f323c-195">Общее</span><span class="sxs-lookup"><span data-stu-id="f323c-195">General</span></span>

| <span data-ttu-id="f323c-196">Команда</span><span class="sxs-lookup"><span data-stu-id="f323c-196">Command</span></span>                                       | <span data-ttu-id="f323c-197">Функция</span><span class="sxs-lookup"><span data-stu-id="f323c-197">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="f323c-198">dotnet build</span><span class="sxs-lookup"><span data-stu-id="f323c-198">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="f323c-199">Выполняет сборку приложения .NET.</span><span class="sxs-lookup"><span data-stu-id="f323c-199">Builds a .NET application.</span></span>                                     |
| [<span data-ttu-id="f323c-200">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="f323c-200">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="f323c-201">Взаимодействует с серверами, запущенными сборкой.</span><span class="sxs-lookup"><span data-stu-id="f323c-201">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="f323c-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="f323c-202">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="f323c-203">Очищает выходные данные сборки.</span><span class="sxs-lookup"><span data-stu-id="f323c-203">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="f323c-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="f323c-204">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="f323c-205">Выводит более подробную документацию из Интернета для команды.</span><span class="sxs-lookup"><span data-stu-id="f323c-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="f323c-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="f323c-206">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="f323c-207">Переносит допустимый проект предварительной версии 2 в проект пакета SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="f323c-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="f323c-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="f323c-208">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="f323c-209">Обеспечивает доступ к командной строке MSBuild.</span><span class="sxs-lookup"><span data-stu-id="f323c-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="f323c-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="f323c-210">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="f323c-211">Инициализирует проект C# или F# для заданного шаблона.</span><span class="sxs-lookup"><span data-stu-id="f323c-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="f323c-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="f323c-212">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="f323c-213">Создает пакет NuGet с кодом.</span><span class="sxs-lookup"><span data-stu-id="f323c-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="f323c-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="f323c-214">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="f323c-215">Публикует платформозависимое или автономное приложение .NET.</span><span class="sxs-lookup"><span data-stu-id="f323c-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="f323c-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="f323c-216">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="f323c-217">Восстанавливает зависимости для данного приложения.</span><span class="sxs-lookup"><span data-stu-id="f323c-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="f323c-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="f323c-218">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="f323c-219">Запускает приложение из источника.</span><span class="sxs-lookup"><span data-stu-id="f323c-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="f323c-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="f323c-220">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="f323c-221">Параметры для добавления, удаления и перечисления проектов в файле решения.</span><span class="sxs-lookup"><span data-stu-id="f323c-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="f323c-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="f323c-222">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="f323c-223">Сохраняет сборки в хранилище пакетов среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="f323c-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="f323c-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="f323c-224">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="f323c-225">Выполняет тесты с помощью средства запуска тестов.</span><span class="sxs-lookup"><span data-stu-id="f323c-225">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="f323c-226">Ссылки на проекты</span><span class="sxs-lookup"><span data-stu-id="f323c-226">Project references</span></span>

<span data-ttu-id="f323c-227">Команда</span><span class="sxs-lookup"><span data-stu-id="f323c-227">Command</span></span> | <span data-ttu-id="f323c-228">Функция</span><span class="sxs-lookup"><span data-stu-id="f323c-228">Function</span></span>
--- | ---
[<span data-ttu-id="f323c-229">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="f323c-229">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="f323c-230">Добавляет ссылку на проект.</span><span class="sxs-lookup"><span data-stu-id="f323c-230">Adds a project reference.</span></span>
[<span data-ttu-id="f323c-231">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="f323c-231">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="f323c-232">Перечисляет ссылки на проекты.</span><span class="sxs-lookup"><span data-stu-id="f323c-232">Lists project references.</span></span>
[<span data-ttu-id="f323c-233">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="f323c-233">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="f323c-234">Удаляет ссылку на проект.</span><span class="sxs-lookup"><span data-stu-id="f323c-234">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="f323c-235">Пакеты NuGet</span><span class="sxs-lookup"><span data-stu-id="f323c-235">NuGet packages</span></span>

<span data-ttu-id="f323c-236">Команда</span><span class="sxs-lookup"><span data-stu-id="f323c-236">Command</span></span> | <span data-ttu-id="f323c-237">Функция</span><span class="sxs-lookup"><span data-stu-id="f323c-237">Function</span></span>
--- | ---
[<span data-ttu-id="f323c-238">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="f323c-238">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="f323c-239">Добавляет пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="f323c-239">Adds a NuGet package.</span></span>
[<span data-ttu-id="f323c-240">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="f323c-240">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="f323c-241">Удаляет пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="f323c-241">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="f323c-242">Команды NuGet</span><span class="sxs-lookup"><span data-stu-id="f323c-242">NuGet commands</span></span>

<span data-ttu-id="f323c-243">Команда</span><span class="sxs-lookup"><span data-stu-id="f323c-243">Command</span></span> | <span data-ttu-id="f323c-244">Функция</span><span class="sxs-lookup"><span data-stu-id="f323c-244">Function</span></span>
--- | ---
[<span data-ttu-id="f323c-245">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="f323c-245">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="f323c-246">Удаляет пакет с сервера или из списка.</span><span class="sxs-lookup"><span data-stu-id="f323c-246">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="f323c-247">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="f323c-247">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="f323c-248">Отправляет пакет на сервер и публикует его.</span><span class="sxs-lookup"><span data-stu-id="f323c-248">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="f323c-249">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="f323c-249">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="f323c-250">Очищает или перечисляет локальные ресурсы NuGet в кэше HTTP-запросов, временном кэше или папке пакетов, используемой на уровне компьютера.</span><span class="sxs-lookup"><span data-stu-id="f323c-250">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="f323c-251">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="f323c-251">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="f323c-252">Добавляет источник NuGet.</span><span class="sxs-lookup"><span data-stu-id="f323c-252">Adds a NuGet source.</span></span>
[<span data-ttu-id="f323c-253">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="f323c-253">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="f323c-254">Отключает источник NuGet.</span><span class="sxs-lookup"><span data-stu-id="f323c-254">Disables a NuGet source.</span></span>
[<span data-ttu-id="f323c-255">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="f323c-255">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="f323c-256">Включает источник NuGet.</span><span class="sxs-lookup"><span data-stu-id="f323c-256">Enables a NuGet source.</span></span>
[<span data-ttu-id="f323c-257">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="f323c-257">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="f323c-258">Перечисляет все настроенные источники NuGet.</span><span class="sxs-lookup"><span data-stu-id="f323c-258">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="f323c-259">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="f323c-259">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="f323c-260">Удаляет источник NuGet.</span><span class="sxs-lookup"><span data-stu-id="f323c-260">Removes a NuGet source.</span></span>
[<span data-ttu-id="f323c-261">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="f323c-261">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="f323c-262">Обновляет источник NuGet.</span><span class="sxs-lookup"><span data-stu-id="f323c-262">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="f323c-263">Команды глобального, установочного и локального средства</span><span class="sxs-lookup"><span data-stu-id="f323c-263">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="f323c-264">Средства — это консольные приложения, которые устанавливаются из пакетов NuGet и вызываются из командной строки.</span><span class="sxs-lookup"><span data-stu-id="f323c-264">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="f323c-265">Вы можете писать средства самостоятельно или устанавливать средства, написанные другими.</span><span class="sxs-lookup"><span data-stu-id="f323c-265">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="f323c-266">Средства также называются глобальными средствами, средствами пути к средству и локальными средствами.</span><span class="sxs-lookup"><span data-stu-id="f323c-266">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="f323c-267">Дополнительные сведения см. в [обзоре средств .NET](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="f323c-267">For more information, see [.NET tools overview](global-tools.md).</span></span> <span data-ttu-id="f323c-268">Глобальные и установочные средства доступны, начиная с версии пакета SDK .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="f323c-268">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="f323c-269">Локальные средства доступны в пакете SDK для .NET Core, начиная с версии 3.0.</span><span class="sxs-lookup"><span data-stu-id="f323c-269">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="f323c-270">Команда</span><span class="sxs-lookup"><span data-stu-id="f323c-270">Command</span></span> | <span data-ttu-id="f323c-271">Функция</span><span class="sxs-lookup"><span data-stu-id="f323c-271">Function</span></span>
--- | ---
[<span data-ttu-id="f323c-272">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="f323c-272">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="f323c-273">Устанавливает средство на компьютере.</span><span class="sxs-lookup"><span data-stu-id="f323c-273">Installs a tool on your machine.</span></span>
[<span data-ttu-id="f323c-274">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="f323c-274">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="f323c-275">Выводит все глобальные, установочные и локальные средства, установленные на компьютере.</span><span class="sxs-lookup"><span data-stu-id="f323c-275">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="f323c-276">dotnet tool search</span><span class="sxs-lookup"><span data-stu-id="f323c-276">dotnet tool search</span></span>](dotnet-tool-list.md) | <span data-ttu-id="f323c-277">Ищет в NuGet.org средства, в названии или метаданных которых есть указанный поисковый запрос.</span><span class="sxs-lookup"><span data-stu-id="f323c-277">Searches NuGet.org for tools that have the specified search term in their name or metadata.</span></span>
[<span data-ttu-id="f323c-278">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="f323c-278">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="f323c-279">Удаляет средство с компьютера.</span><span class="sxs-lookup"><span data-stu-id="f323c-279">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="f323c-280">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="f323c-280">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="f323c-281">Обновляет средство, установленное на компьютере.</span><span class="sxs-lookup"><span data-stu-id="f323c-281">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="f323c-282">Дополнительные средства</span><span class="sxs-lookup"><span data-stu-id="f323c-282">Additional tools</span></span>

<span data-ttu-id="f323c-283">Ряд средств, которые ранее были доступны только для отдельных проектов через `DotnetCliToolReference`, стали частью пакета SDK для .NET начиная с версии 2.1.300.</span><span class="sxs-lookup"><span data-stu-id="f323c-283">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET SDK.</span></span> <span data-ttu-id="f323c-284">Эти средства перечислены в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="f323c-284">These tools are listed in the following table:</span></span>

| <span data-ttu-id="f323c-285">Средство</span><span class="sxs-lookup"><span data-stu-id="f323c-285">Tool</span></span>                                              | <span data-ttu-id="f323c-286">Функция</span><span class="sxs-lookup"><span data-stu-id="f323c-286">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="f323c-287">dev-certs</span><span class="sxs-lookup"><span data-stu-id="f323c-287">dev-certs</span></span>                                         | <span data-ttu-id="f323c-288">Создает сертификаты разработки и управляет ими.</span><span class="sxs-lookup"><span data-stu-id="f323c-288">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="f323c-289">ef</span><span class="sxs-lookup"><span data-stu-id="f323c-289">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="f323c-290">Средства командной строки для Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="f323c-290">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="f323c-291">sql-cache</span><span class="sxs-lookup"><span data-stu-id="f323c-291">sql-cache</span></span>                                         | <span data-ttu-id="f323c-292">Средства командной строки для кэша SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f323c-292">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="f323c-293">user-secrets</span><span class="sxs-lookup"><span data-stu-id="f323c-293">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="f323c-294">Управляет секретами пользователей для разработки.</span><span class="sxs-lookup"><span data-stu-id="f323c-294">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="f323c-295">watch</span><span class="sxs-lookup"><span data-stu-id="f323c-295">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="f323c-296">Запускает наблюдатель за файлами, который выполняет команду при изменении файлов.</span><span class="sxs-lookup"><span data-stu-id="f323c-296">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="f323c-297">Дополнительные сведения о каждом средстве можно получить с помощью команды `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="f323c-297">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="f323c-298">Примеры</span><span class="sxs-lookup"><span data-stu-id="f323c-298">Examples</span></span>

<span data-ttu-id="f323c-299">Создание нового консольного приложения .NET:</span><span class="sxs-lookup"><span data-stu-id="f323c-299">Create a new .NET console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="f323c-300">Сборка проекта и его зависимостей в указанном каталоге:</span><span class="sxs-lookup"><span data-stu-id="f323c-300">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="f323c-301">Запуск приложения:</span><span class="sxs-lookup"><span data-stu-id="f323c-301">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="f323c-302">Переменные среды</span><span class="sxs-lookup"><span data-stu-id="f323c-302">Environment variables</span></span>

- <span data-ttu-id="f323c-303">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="f323c-303">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="f323c-304">Указывает расположение сред выполнения .NET, если оно отличается от задаваемого по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f323c-304">Specifies the location of the .NET runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="f323c-305">В ОС Windows по умолчанию используется расположение `C:\Program Files\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="f323c-305">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="f323c-306">В ОС Linux и macOS по умолчанию используется расположение `/usr/share/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="f323c-306">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="f323c-307">Эта переменная среды используется только при запуске приложений с помощью созданных исполняемых файлов (apphost).</span><span class="sxs-lookup"><span data-stu-id="f323c-307">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="f323c-308">При запуске 32-разрядного исполняемого файла в 64-разрядной ОС вместо нее используется `DOTNET_ROOT(x86)`.</span><span class="sxs-lookup"><span data-stu-id="f323c-308">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `NUGET_PACKAGES`

  <span data-ttu-id="f323c-309">Папка глобальных пакетов.</span><span class="sxs-lookup"><span data-stu-id="f323c-309">The global packages folder.</span></span> <span data-ttu-id="f323c-310">Если значение не задано, то по умолчанию в Unix используется `~/.nuget/packages`, а в Windows — `%userprofile%\.nuget\packages`.</span><span class="sxs-lookup"><span data-stu-id="f323c-310">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="f323c-311">Задает расположение служебного индекса, который будет использоваться общим узлом при загрузке среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="f323c-311">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="f323c-312">Указывает, отображаются ли сообщения приветствия и данные телеметрии .NET при первом запуске.</span><span class="sxs-lookup"><span data-stu-id="f323c-312">Specifies whether .NET welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="f323c-313">Установите значение `true` для отключения звука этих сообщений (принимаются значения `true`, `1` или `yes`) или установите значение `false` для разрешения звука (принимаются значения `false`, `0` или `no`).</span><span class="sxs-lookup"><span data-stu-id="f323c-313">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="f323c-314">Если не задано, по умолчанию используется `false` и при первом запуске будут отображаться сообщения.</span><span class="sxs-lookup"><span data-stu-id="f323c-314">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="f323c-315">Этот флаг не влияет на данные телеметрии (см. `DOTNET_CLI_TELEMETRY_OPTOUT`, чтобы отменить отправку телеметрии).</span><span class="sxs-lookup"><span data-stu-id="f323c-315">This flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="f323c-316">Указывает, собираются ли данные по использованию средств .NET для отправки в корпорацию Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="f323c-316">Specifies whether data about the .NET tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="f323c-317">Установите значение `true`, чтобы отказаться от функций телеметрии (поддерживаются значения `true`, `1` или `yes`).</span><span class="sxs-lookup"><span data-stu-id="f323c-317">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="f323c-318">Также можно установить значение `false`, чтобы согласиться на функции телеметрии (поддерживаются значения `false`, `0` или `no`).</span><span class="sxs-lookup"><span data-stu-id="f323c-318">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="f323c-319">Если значение не задано, то по умолчанию используется `false`, то есть функция телеметрии включена.</span><span class="sxs-lookup"><span data-stu-id="f323c-319">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="f323c-320">Указывает, разрешается ли из глобального расположения среда выполнения .NET, общая платформа или пакет SDK.</span><span class="sxs-lookup"><span data-stu-id="f323c-320">Specifies whether .NET runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="f323c-321">Если не задано, используется значение по умолчанию 1 (логическое значение `true`).</span><span class="sxs-lookup"><span data-stu-id="f323c-321">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="f323c-322">Задайте значение 0 (логическое значение `false`), чтобы не разрешать эти сущности из глобального расположения и использовать изолированные установки .NET.</span><span class="sxs-lookup"><span data-stu-id="f323c-322">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET installations.</span></span> <span data-ttu-id="f323c-323">Дополнительные сведения о многоуровневом поиске см. в разделе [Многоуровневый поиск SharedFX](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="f323c-323">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="f323c-324">`DOTNET_ROLL_FORWARD` **Доступно, начиная с .NET Core версии 3.x**.</span><span class="sxs-lookup"><span data-stu-id="f323c-324">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="f323c-325">Определяет поведение наката.</span><span class="sxs-lookup"><span data-stu-id="f323c-325">Determines roll forward behavior.</span></span> <span data-ttu-id="f323c-326">Дополнительные сведения см. в описании параметра `--roll-forward`, приведенном выше в этой статье.</span><span class="sxs-lookup"><span data-stu-id="f323c-326">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="f323c-327">`DOTNET_ROLL_FORWARD_TO_PRERELEASE` **Доступно, начиная с .NET Core версии 3.x**.</span><span class="sxs-lookup"><span data-stu-id="f323c-327">`DOTNET_ROLL_FORWARD_TO_PRERELEASE` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="f323c-328">Если задано значение `1` (включено), поддерживается накат версии выпуска на предварительную версию.</span><span class="sxs-lookup"><span data-stu-id="f323c-328">If set to `1` (enabled), enables rolling forward to a pre-release version from a release version.</span></span> <span data-ttu-id="f323c-329">По умолчанию (если `0` отключено) при запросе версии выпуска среды выполнения .NET накат будет выполняться только для установленных версий выпуска.</span><span class="sxs-lookup"><span data-stu-id="f323c-329">By default (`0` - disabled), when a release version of .NET runtime is requested, roll-forward will only consider installed release versions.</span></span>

  <span data-ttu-id="f323c-330">Дополнительные сведения о накате можно найти в [этой статье](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="f323c-330">For more information, see [Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="f323c-331">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Доступно в пакете SDK для .NET Core версии 2.x.**</span><span class="sxs-lookup"><span data-stu-id="f323c-331">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x.**</span></span>

  <span data-ttu-id="f323c-332">Отключает накат дополнительных версий, если установлено `0`.</span><span class="sxs-lookup"><span data-stu-id="f323c-332">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="f323c-333">Дополнительные сведения о накате можно найти в [этой статье](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="f323c-333">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="f323c-334">Этот параметр в .NET Core 3.0 заменяется `DOTNET_ROLL_FORWARD`.</span><span class="sxs-lookup"><span data-stu-id="f323c-334">This setting is superseded in .NET Core 3.0 by `DOTNET_ROLL_FORWARD`.</span></span> <span data-ttu-id="f323c-335">Вместо этого следует использовать новый параметр.</span><span class="sxs-lookup"><span data-stu-id="f323c-335">The new settings should be used instead.</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="f323c-336">Задает язык пользовательского интерфейса CLI с помощью значения языкового стандарта, например `en-us`.</span><span class="sxs-lookup"><span data-stu-id="f323c-336">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="f323c-337">Поддерживаются те же значения, что и для Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f323c-337">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="f323c-338">Дополнительные сведения см. в разделе, посвященном изменению языка установщика, в [документации по установке Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f323c-338">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="f323c-339">Применяются правила диспетчера ресурсов .NET, в связи с чем вам не нужно выбирать точное соответствие &mdash; можно также выбрать потомков в дереве `CultureInfo`.</span><span class="sxs-lookup"><span data-stu-id="f323c-339">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="f323c-340">Например, если задать значение `fr-CA`, интерфейс командной строки будет находить и использовать переводы `fr`.</span><span class="sxs-lookup"><span data-stu-id="f323c-340">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="f323c-341">Если задать язык, который не поддерживается, для интерфейса командной строки будет использоваться английский язык.</span><span class="sxs-lookup"><span data-stu-id="f323c-341">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="f323c-342">Для создаваемых исполняемых файлов с поддержкой графического пользовательского интерфейса отключает всплывающее диалоговое окно, которое обычно выводится для определенных классов ошибок.</span><span class="sxs-lookup"><span data-stu-id="f323c-342">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="f323c-343">В таких случаях выполняются только запись в `stderr` и выход.</span><span class="sxs-lookup"><span data-stu-id="f323c-343">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="f323c-344">Эквивалентно параметру `--additional-deps` интерфейса командной строки.</span><span class="sxs-lookup"><span data-stu-id="f323c-344">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="f323c-345">Переопределяет обнаруженный RID.</span><span class="sxs-lookup"><span data-stu-id="f323c-345">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="f323c-346">Расположение общего хранилища, которое в некоторых случаях используется для разрешения сборки.</span><span class="sxs-lookup"><span data-stu-id="f323c-346">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="f323c-347">Список сборок, из которого осуществляется загрузка и выполнение перехватчиков запуска.</span><span class="sxs-lookup"><span data-stu-id="f323c-347">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="f323c-348">`DOTNET_BUNDLE_EXTRACT_BASE_DIR` **Доступно, начиная с пакета .NET Core версии 3.x**.</span><span class="sxs-lookup"><span data-stu-id="f323c-348">`DOTNET_BUNDLE_EXTRACT_BASE_DIR` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="f323c-349">Указывает каталог, в который извлекается однофайловое приложение перед выполнением.</span><span class="sxs-lookup"><span data-stu-id="f323c-349">Specifies a directory to which a single-file application is extracted before it is executed.</span></span>

  <span data-ttu-id="f323c-350">Дополнительные сведения об однофайловых исполняемых файлах см. [здесь](../whats-new/dotnet-core-3-0.md#single-file-executables).</span><span class="sxs-lookup"><span data-stu-id="f323c-350">For more information, see [Single-file executables](../whats-new/dotnet-core-3-0.md#single-file-executables).</span></span>

- <span data-ttu-id="f323c-351">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="f323c-351">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="f323c-352">Управляет диагностической трассировкой из компонентов размещения, таких как `dotnet.exe`, `hostfxr` и `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="f323c-352">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

  * <span data-ttu-id="f323c-353">`COREHOST_TRACE=[0/1]` — по умолчанию имеет значение `0` — трассировка отключена.</span><span class="sxs-lookup"><span data-stu-id="f323c-353">`COREHOST_TRACE=[0/1]` - default is `0` - tracing disabled.</span></span> <span data-ttu-id="f323c-354">Значение `1` включает диагностическую трассировку.</span><span class="sxs-lookup"><span data-stu-id="f323c-354">If set to `1`, diagnostics tracing is enabled.</span></span>
  * <span data-ttu-id="f323c-355">`COREHOST_TRACEFILE=<file path>` — действует, только если трассировка включена параметром `COREHOST_TRACE=1`.</span><span class="sxs-lookup"><span data-stu-id="f323c-355">`COREHOST_TRACEFILE=<file path>` - only has effect if tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="f323c-356">Если включен этот параметр, трассировочные сведения записываются в указанный файл, а в противном случае передаются в `stderr`.</span><span class="sxs-lookup"><span data-stu-id="f323c-356">When set, the tracing information is written to the specified file, otherwise the tracing information is written to `stderr`.</span></span> <span data-ttu-id="f323c-357">**Доступно, начиная с пакета .NET Core версии 3.x**.</span><span class="sxs-lookup"><span data-stu-id="f323c-357">**Available starting with .NET Core 3.x.**</span></span>
  * <span data-ttu-id="f323c-358">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` — по умолчанию имеет значение `4`.</span><span class="sxs-lookup"><span data-stu-id="f323c-358">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` - default is `4`.</span></span> <span data-ttu-id="f323c-359">Этот параметр используется, только если трассировка включена параметром `COREHOST_TRACE=1`.</span><span class="sxs-lookup"><span data-stu-id="f323c-359">The setting is used only when tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="f323c-360">**Доступно, начиная с пакета .NET Core версии 3.x**.</span><span class="sxs-lookup"><span data-stu-id="f323c-360">**Available starting with .NET Core 3.x.**</span></span>
    * <span data-ttu-id="f323c-361">`4` — записываются все трассировочные данные.</span><span class="sxs-lookup"><span data-stu-id="f323c-361">`4` - all tracing information is written</span></span>
    * <span data-ttu-id="f323c-362">`3` — записываются только информационные сообщения, предупреждения и ошибки.</span><span class="sxs-lookup"><span data-stu-id="f323c-362">`3` - only informational, warning and error messages are written</span></span>
    * <span data-ttu-id="f323c-363">`2` — записываются только предупреждения и ошибки.</span><span class="sxs-lookup"><span data-stu-id="f323c-363">`2` - only warning and error messages are written</span></span>
    * <span data-ttu-id="f323c-364">`1` — записываются только сообщения об ошибках.</span><span class="sxs-lookup"><span data-stu-id="f323c-364">`1` - only error messages are written</span></span>

  <span data-ttu-id="f323c-365">Для получения подробных трассировочных сведений о запуске приложения обычно включают `COREHOST_TRACE=1` и `COREHOST_TRACEFILE=host_trace.txt`, а затем запускают приложение.</span><span class="sxs-lookup"><span data-stu-id="f323c-365">The typical way to get detailed trace information about application startup is to set `COREHOST_TRACE=1` and `COREHOST_TRACEFILE=host_trace.txt` and then run the application.</span></span> <span data-ttu-id="f323c-366">В текущем каталоге будет создан новый файл `host_trace.txt` с подробными сведениями.</span><span class="sxs-lookup"><span data-stu-id="f323c-366">A new file `host_trace.txt` will be created in the current directory with the detailed information.</span></span>

## <a name="see-also"></a><span data-ttu-id="f323c-367">См. также</span><span class="sxs-lookup"><span data-stu-id="f323c-367">See also</span></span>

- [<span data-ttu-id="f323c-368">Файлы конфигурации среды выполнения</span><span class="sxs-lookup"><span data-stu-id="f323c-368">Runtime Configuration Files</span></span>](https://github.com/dotnet/sdk/blob/main/documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="f323c-369">Параметры конфигурации среды выполнения .NET</span><span class="sxs-lookup"><span data-stu-id="f323c-369">.NET run-time configuration settings</span></span>](../run-time-config/index.md)
