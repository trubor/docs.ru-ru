---
title: Команда dotnet test
description: Команда dotnet test служит для выполнения модульных тестов в проекте.
ms.date: 04/29/2020
ms.openlocfilehash: 4834da766bd052f44127a72635b65866eb7e3352
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189158"
---
# <a name="dotnet-test"></a><span data-ttu-id="f1f9d-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="f1f9d-103">dotnet test</span></span>

<span data-ttu-id="f1f9d-104">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="f1f9d-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f1f9d-105">name</span><span class="sxs-lookup"><span data-stu-id="f1f9d-105">Name</span></span>

<span data-ttu-id="f1f9d-106">`dotnet test` — драйвер тестов .NET, используемый для проведения модульных тестов.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f1f9d-107">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="f1f9d-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <ADAPTER_PATH>] [--blame] [--blame-crash]
    [--blame-crash-dump-type <DUMP_TYPE>] [--blame-crash-collect-always]
    [--blame-hang] [--blame-hang-dump-type <DUMP_TYPE>]
    [--blame-hang-timeout <TIMESPAN>]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_NAME>]
    [-d|--diag <LOG_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <RESULTS_DIR>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="f1f9d-108">Описание</span><span class="sxs-lookup"><span data-stu-id="f1f9d-108">Description</span></span>

<span data-ttu-id="f1f9d-109">Команда `dotnet test` служит для выполнения модульных тестов в решении.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="f1f9d-110">Команда `dotnet test` создает решение и запускает приложение тестового узла для каждого тестового проекта в решении.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="f1f9d-111">Тестовый узел выполняет тесты в заданном проекте с помощью платформы тестирования, например MSTest, NUnit или xUnit, и сообщает об успешном или неуспешном завершении каждого теста.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="f1f9d-112">Если все тесты выполнены успешно, средство выполнения тестов возвращает код 0. Если же любой тест завершается с ошибкой, средство выполнения возвращает 1.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="f1f9d-113">Для проектов с несколькими целевыми платформами тесты запускаются для каждой из них.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="f1f9d-114">Тестовый узел и платформа модульных тестов упаковываются в пакеты NuGet и восстанавливаются как обычные зависимости проекта.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="f1f9d-115">Тестовый проект указывает средство выполнения тестов с помощью обычного элемента `<PackageReference>`, как показано в следующем примере файла проекта:</span><span class="sxs-lookup"><span data-stu-id="f1f9d-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="f1f9d-116">Где `Microsoft.NET.Test.Sdk` — это тестовый узел, `xunit` — платформа тестирования.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="f1f9d-117">`xunit.runner.visualstudio` — это адаптер теста, позволяющий платформе xUnit работать с тестовым узлом.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="f1f9d-118">Неявное восстановление</span><span class="sxs-lookup"><span data-stu-id="f1f9d-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="f1f9d-119">Аргументы</span><span class="sxs-lookup"><span data-stu-id="f1f9d-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="f1f9d-120">Путь к тестовому проекту.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-120">Path to the test project.</span></span>
  - <span data-ttu-id="f1f9d-121">Путь к решению.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-121">Path to the solution.</span></span>
  - <span data-ttu-id="f1f9d-122">Путь к каталогу, содержащему проект или решение.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="f1f9d-123">Путь к *DLL-файлу* тестового проекта.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="f1f9d-124">Если он не указан, команда ищет проект или решение в текущем каталоге.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="f1f9d-125">Параметры</span><span class="sxs-lookup"><span data-stu-id="f1f9d-125">Options</span></span>

- **`-a|--test-adapter-path <ADAPTER_PATH>`**

  <span data-ttu-id="f1f9d-126">Путь к каталогу для поиска дополнительных адаптеров теста.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="f1f9d-127">Проверяются только *DLL*-файлы с суффиксом `.TestAdapter.dll`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="f1f9d-128">Если не указано, выполняется поиск по каталогу тестового *DLL*.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="f1f9d-129">Выполнение тестов в режиме обвинения.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="f1f9d-130">Этот параметр полезен при изоляции проблемных тестов, которые приводят к аварийному завершению хоста для тестов.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="f1f9d-131">При обнаружении сбоя он создает файл последовательности в `TestResults/<Guid>/<Guid>_Sequence.xml`, который фиксирует порядок тестов, выполненных до сбоя.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-131">When a crash is detected, it creates a sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- <span data-ttu-id="f1f9d-132">**`--blame-crash`** (Доступно, начиная с выпуска пакета SDK для NET 5.0 предварительной версии)</span><span class="sxs-lookup"><span data-stu-id="f1f9d-132">**`--blame-crash`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="f1f9d-133">Выполняет тесты в режиме обвинения и собирает аварийный дамп при непредвиденном завершении процесса хоста для тестов.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-133">Runs the tests in blame mode and collects a crash dump when the test host exits unexpectedly.</span></span> <span data-ttu-id="f1f9d-134">Этот параметр зависит от используемой версии .NET, типа ошибки и операционной системы.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-134">This option depends on the version of .NET used, the type of error, and the operating system.</span></span>
  
  <span data-ttu-id="f1f9d-135">Данные для дампа исключений в управляемом коде будут собираться в .NET 5.0 и более поздних версий автоматически.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-135">For exceptions in managed code, a dump will be automatically collected on .NET 5.0 and later versions.</span></span> <span data-ttu-id="f1f9d-136">Этот параметр создаст дамп для TestHost или любого дочернего процесса, который также выполнялся в .NET 5.0 и завершился сбоем.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-136">It will generate a dump for testhost or any child process that also ran on .NET 5.0 and crashed.</span></span> <span data-ttu-id="f1f9d-137">Аварийное завершение в машинном коде не приведет к созданию дампа.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-137">Crashes in native code will not generate a dump.</span></span> <span data-ttu-id="f1f9d-138">Этот параметр работает в Windows, macOS и Linux.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-138">This option works on Windows, macOS, and Linux.</span></span>
  
  <span data-ttu-id="f1f9d-139">Аварийные дампы в машинном коде или при использовании .NET Core 3.1 или более ранних версий можно собирать только в Windows с помощью Procdump.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-139">Crash dumps in native code, or when using .NET Core 3.1 or earlier versions, can only be collected on Windows, by using Procdump.</span></span> <span data-ttu-id="f1f9d-140">Каталог, содержащий файлы *procdump.exe* и *procdump64.exe*, должен быть включен в переменную среды PATH или PROCDUMP_PATH.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-140">A directory that contains *procdump.exe* and *procdump64.exe* must be in the PATH or PROCDUMP_PATH environment variable.</span></span> <span data-ttu-id="f1f9d-141">[Скачать средства.](/sysinternals/downloads/procdump)</span><span class="sxs-lookup"><span data-stu-id="f1f9d-141">[Download the tools](/sysinternals/downloads/procdump).</span></span> <span data-ttu-id="f1f9d-142">Подразумевает `--blame`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-142">Implies `--blame`.</span></span>
  
  <span data-ttu-id="f1f9d-143">Чтобы собрать аварийный дамп из собственного приложения, запущенного в NET 5.0 или более поздней версии, можно принудительно использовать Procdump, задав для переменной среды `VSTEST_DUMP_FORCEPROCDUMP` значение `1`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-143">To collect a crash dump from a native application running on .NET 5.0 or later, the usage of Procdump can be forced by setting the `VSTEST_DUMP_FORCEPROCDUMP` environment variable to `1`.</span></span>

- <span data-ttu-id="f1f9d-144">**`--blame-crash-dump-type <DUMP_TYPE>`** (Доступно, начиная с выпуска пакета SDK для NET 5.0 предварительной версии)</span><span class="sxs-lookup"><span data-stu-id="f1f9d-144">**`--blame-crash-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="f1f9d-145">Тип собираемого аварийного дампа.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-145">The type of crash dump to be collected.</span></span> <span data-ttu-id="f1f9d-146">Подразумевает `--blame-crash`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-146">Implies `--blame-crash`.</span></span>

- <span data-ttu-id="f1f9d-147">**`--blame-crash-collect-always`** (Доступно, начиная с выпуска пакета SDK для NET 5.0 предварительной версии)</span><span class="sxs-lookup"><span data-stu-id="f1f9d-147">**`--blame-crash-collect-always`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="f1f9d-148">Собирает аварийный дамп при ожидаемом и непредвиденном завершении процесса хоста для тестов.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-148">Collects a crash dump on expected as well as unexpected test host exit.</span></span>

- <span data-ttu-id="f1f9d-149">**`--blame-hang`** (Доступно, начиная с выпуска пакета SDK для NET 5.0 предварительной версии)</span><span class="sxs-lookup"><span data-stu-id="f1f9d-149">**`--blame-hang`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="f1f9d-150">Выполняет тесты в режиме обвинения и собирает дамп зависания при превышении тестом заданного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-150">Run the tests in blame mode and collects a hang dump when a test exceeds the given timeout.</span></span>

- <span data-ttu-id="f1f9d-151">**`--blame-hang-dump-type <DUMP_TYPE>`** (Доступно, начиная с выпуска пакета SDK для NET 5.0 предварительной версии)</span><span class="sxs-lookup"><span data-stu-id="f1f9d-151">**`--blame-hang-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="f1f9d-152">Тип собираемого аварийного дампа:</span><span class="sxs-lookup"><span data-stu-id="f1f9d-152">The type of crash dump to be collected.</span></span> <span data-ttu-id="f1f9d-153">`full`, `mini` или `none`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-153">It should be `full`, `mini`, or `none`.</span></span> <span data-ttu-id="f1f9d-154">Если указан тип `none`, процесс хоста для тестов завершается по истечении времени ожидания, но дамп не собирается.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-154">When `none` is specified, test host is terminated on timeout, but no dump is collected.</span></span> <span data-ttu-id="f1f9d-155">Подразумевает `--blame-hang`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-155">Implies `--blame-hang`.</span></span>

- <span data-ttu-id="f1f9d-156">**`--blame-hang-timeout <TIMESPAN>`** (Доступно, начиная с выпуска пакета SDK для NET 5.0 предварительной версии)</span><span class="sxs-lookup"><span data-stu-id="f1f9d-156">**`--blame-hang-timeout <TIMESPAN>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="f1f9d-157">Время ожидания каждого теста, после которого дамп зависания активируется, и тестирование хост-процесса и все его дочерние процессы создают дамп и завершаются.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-157">Per-test timeout, after which a hang dump is triggered and the test host process and all of its child processes are dumped and terminated.</span></span> <span data-ttu-id="f1f9d-158">Значение времени ожидания указывается в одном из следующих форматов:</span><span class="sxs-lookup"><span data-stu-id="f1f9d-158">The timeout value is specified in one of the following formats:</span></span>
  
  - <span data-ttu-id="f1f9d-159">1,5 ч, 1,5 часа</span><span class="sxs-lookup"><span data-stu-id="f1f9d-159">1.5h, 1.5hour, 1.5hours</span></span>
  - <span data-ttu-id="f1f9d-160">90 м, 90 мин, 90 минут</span><span class="sxs-lookup"><span data-stu-id="f1f9d-160">90m, 90min, 90minute, 90minutes</span></span>
  - <span data-ttu-id="f1f9d-161">5400 с, 5400 сек, 5400 секунд</span><span class="sxs-lookup"><span data-stu-id="f1f9d-161">5400s, 5400sec, 5400second, 5400seconds</span></span>
  - <span data-ttu-id="f1f9d-162">5 400 000 мс, 5 400 000 мсек, 5 400 000 миллисекунд</span><span class="sxs-lookup"><span data-stu-id="f1f9d-162">5400000ms, 5400000mil, 5400000millisecond, 5400000milliseconds</span></span>

  <span data-ttu-id="f1f9d-163">Если единица измерения не указана (например, 5 400 000), предполагается, что значение указано в миллисекундах.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-163">When no unit is used (for example, 5400000), the value is assumed to be in milliseconds.</span></span> <span data-ttu-id="f1f9d-164">При использовании вместе с тестами, управляемыми данными, поведение времени ожидания зависит от используемого адаптера теста.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-164">When used together with data driven tests, the timeout behavior depends on the test adapter used.</span></span> <span data-ttu-id="f1f9d-165">Для xUnit и NUnit время ожидания обновляется после каждого тестового случая.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-165">For xUnit and NUnit the timeout is renewed after every test case.</span></span> <span data-ttu-id="f1f9d-166">Для MSTest время ожидания используется для всех тестовых случаев.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-166">For MSTest, the timeout is used for all test cases.</span></span> <span data-ttu-id="f1f9d-167">Эта возможность поддерживается в Windows с netcoreapp 2.1 и более поздних версий, в Linux с netcoreapp 3.1 и более поздних версий, а также в macOS с NET 5.0 или более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-167">This option is supported on Windows with netcoreapp2.1 and later, on Linux with netcoreapp3.1 and later, and on macOS with net5.0 or later.</span></span> <span data-ttu-id="f1f9d-168">Подразумевает `--blame` и `--blame-hang`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-168">Implies `--blame` and `--blame-hang`.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="f1f9d-169">Определяет конфигурацию сборки.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-169">Defines the build configuration.</span></span> <span data-ttu-id="f1f9d-170">Значение по умолчанию — `Debug`, но конфигурация проекта может переопределить этот параметр SDK по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-170">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_NAME>`**

  <span data-ttu-id="f1f9d-171">Включает сборщик данных для тестового запуска.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-171">Enables data collector for the test run.</span></span> <span data-ttu-id="f1f9d-172">Дополнительные сведения см. в разделе [Мониторинг и анализ тестового запуска](https://aka.ms/vstest-collect).</span><span class="sxs-lookup"><span data-stu-id="f1f9d-172">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>
  
  <span data-ttu-id="f1f9d-173">Чтобы получить объем протестированного кода на любой платформе, поддерживаемой .NET Core, установите [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) и используйте параметр `--collect:"XPlat Code Coverage"`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-173">To collect code coverage on any platform that is supported by .NET Core, install [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) and use the `--collect:"XPlat Code Coverage"` option.</span></span>

  <span data-ttu-id="f1f9d-174">В Windows объем протестированного кода можно получить с помощью параметра `--collect "Code Coverage"`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-174">On Windows, you can collect code coverage by using the `--collect "Code Coverage"` option.</span></span> <span data-ttu-id="f1f9d-175">Этот параметр создает файл *COVERAGE*, который можно открыть в Visual Studio 2019 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-175">This option generates a *.coverage* file, which can be opened in Visual Studio 2019 Enterprise.</span></span> <span data-ttu-id="f1f9d-176">Дополнительные сведения см. в статьях [Использование объема протестированного кода](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) и [Настройка анализа объема протестированного кода](/visualstudio/test/customizing-code-coverage-analysis).</span><span class="sxs-lookup"><span data-stu-id="f1f9d-176">For more information, see [Use code coverage](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) and [Customize code coverage analysis](/visualstudio/test/customizing-code-coverage-analysis).</span></span>

- **`-d|--diag <LOG_FILE>`**

  <span data-ttu-id="f1f9d-177">Включает режим диагностики для платформы тестирования и записывает диагностические сообщения в указанный файл и в файлы рядом с ним.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-177">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="f1f9d-178">Процесс, который заносит сообщения в журнал, определяет, какие файлы создаются, например `*.host_<date>.txt` для журнала тестового узла и `*.datacollector_<date>.txt` для журнала сборщика данных.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-178">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="f1f9d-179">Определяет принудительное использование `dotnet` или тестового узла .NET Framework для двоичных файлов теста.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-179">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="f1f9d-180">Этот параметр определяет только используемый тип узла.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-180">This option only determines which type of host to use.</span></span> <span data-ttu-id="f1f9d-181">Реальная используемая версия платформы определяется в файле *runtimeconfig.json* тестового проекта.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-181">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="f1f9d-182">Если этот параметр не указан, для определения типа узла используется [атрибут сборки TargetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute).</span><span class="sxs-lookup"><span data-stu-id="f1f9d-182">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="f1f9d-183">Если этот атрибут удален из *DLL*, используется узел .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-183">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="f1f9d-184">Фильтрует тесты в текущем проекте с помощью заданного выражения.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-184">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="f1f9d-185">Дополнительные сведения см. в разделе [Сведения о параметре "Фильтр"](#filter-option-details).</span><span class="sxs-lookup"><span data-stu-id="f1f9d-185">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="f1f9d-186">Дополнительные сведения и примеры использования фильтрации при выборочном модульном тестировании см. в статье [Выполнение выборочных модульных тестов](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f1f9d-186">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="f1f9d-187">Выводит краткую справку по команде.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-187">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="f1f9d-188">Позволяет команде остановиться и дождаться, пока пользователь выполнит действие или введет данные.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-188">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="f1f9d-189">Например, чтобы завершить проверку подлинности.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-189">For example, to complete authentication.</span></span> <span data-ttu-id="f1f9d-190">Доступно, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-190">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER>`**

  <span data-ttu-id="f1f9d-191">Указывает средство ведения журнала для результатов тестирования.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-191">Specifies a logger for test results.</span></span> <span data-ttu-id="f1f9d-192">В отличие от MSBuild, dotnet test не принимает аббревиатуры: вместо `-l "console;v=d"` используйте `-l "console;verbosity=detailed"`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-192">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span> <span data-ttu-id="f1f9d-193">Укажите параметр несколько раз, чтобы включить несколько средств ведения журнала.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-193">Specify the parameter multiple times to enable multiple loggers.</span></span>

- **`--no-build`**

  <span data-ttu-id="f1f9d-194">Не выполняет сборку тестового проекта перед запуском.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-194">Doesn't build the test project before running it.</span></span> <span data-ttu-id="f1f9d-195">Он также неявно задает флаг `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-195">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="f1f9d-196">Запуск тестов без отображения баннера TestPlatform Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-196">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="f1f9d-197">Доступно, начиная с пакета SDK для .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-197">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="f1f9d-198">Не выполняет неявное восстановление при выполнении команды.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-198">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="f1f9d-199">Каталог, в котором выполняется поиск двоичных файлов для выполнения.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-199">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="f1f9d-200">Если значение не указано, путь по умолчанию — `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-200">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="f1f9d-201">Для проектов с несколькими целевыми платформами (с помощью свойства `TargetFrameworks`) необходимо также определить `--framework` при указании этого параметра.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-201">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="f1f9d-202">`dotnet test` всегда запускает тесты из выходного каталога.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-202">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="f1f9d-203">Для использования ресурсов тестирования в выходном каталоге можно использовать <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-203">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <RESULTS_DIR>`**

  <span data-ttu-id="f1f9d-204">Каталог для сохранения результатов тестов.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-204">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="f1f9d-205">Если указанный каталог не существует, он создается.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-205">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="f1f9d-206">По умолчанию используется `TestResults` в каталоге, содержащем файл проекта.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-206">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="f1f9d-207">Целевая среда выполнения для тестирования.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-207">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="f1f9d-208">Файл `.runsettings`, который необходимо использовать для проведения тестов.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-208">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="f1f9d-209">Элемент `TargetPlatform` (x86|x64) не влияет на `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-209">The `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="f1f9d-210">Чтобы запускать тесты для x86, установите версию .NET Core x86.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-210">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="f1f9d-211">Разрядность *dotnet.exe* в пути будет использоваться для выполнения тестов.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-211">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="f1f9d-212">Дополнительные сведения см. в следующих ресурсах:</span><span class="sxs-lookup"><span data-stu-id="f1f9d-212">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="f1f9d-213">Настройка модульных тестов с помощью файла `.runsettings`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-213">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="f1f9d-214">Настройка тестового запуска</span><span class="sxs-lookup"><span data-stu-id="f1f9d-214">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="f1f9d-215">Вывод списка обнаруженных тестов вместо выполнения тестов.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-215">List the discovered tests instead of running the tests.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f1f9d-216">Задает уровень детализации команды.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-216">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f1f9d-217">Допустимые значения: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` и `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-217">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f1f9d-218">Значение по умолчанию — `minimal`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-218">The default is `minimal`.</span></span> <span data-ttu-id="f1f9d-219">Для получения дополнительной информации см. <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-219">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="f1f9d-220">Аргументы **`RunSettings`**</span><span class="sxs-lookup"><span data-stu-id="f1f9d-220">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="f1f9d-221">Встроенные `RunSettings` передаются как последние аргументы в командной строке после "-- " (обратите внимание на пробел после "--").</span><span class="sxs-lookup"><span data-stu-id="f1f9d-221">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="f1f9d-222">Встроенные `RunSettings` указываются как пары `[name]=[value]`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-222">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="f1f9d-223">Несколько пар `[name]=[value]` разделяются пробелами.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-223">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="f1f9d-224">Пример: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="f1f9d-224">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="f1f9d-225">Дополнительные сведения см. в статье о [передаче аргументов RunSettings с помощью командной строки](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span><span class="sxs-lookup"><span data-stu-id="f1f9d-225">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="f1f9d-226">Примеры</span><span class="sxs-lookup"><span data-stu-id="f1f9d-226">Examples</span></span>

- <span data-ttu-id="f1f9d-227">Выполнение тестов в проекте в текущем каталоге:</span><span class="sxs-lookup"><span data-stu-id="f1f9d-227">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="f1f9d-228">Выполнение тестов в проекте `test1`:</span><span class="sxs-lookup"><span data-stu-id="f1f9d-228">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="f1f9d-229">Выполнение тестов в проекте в текущем каталоге и создание файла результатов теста в формате TRX:</span><span class="sxs-lookup"><span data-stu-id="f1f9d-229">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="f1f9d-230">Выполнение тестов в проекте в текущем каталоге и создание файла с объемом протестированного кода (после установки интеграции сборщиков [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md)):</span><span class="sxs-lookup"><span data-stu-id="f1f9d-230">Run the tests in the project in the current directory, and generate a code coverage file (after installing [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) collectors integration):</span></span>

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- <span data-ttu-id="f1f9d-231">Выполнение тестов в проекте в текущем каталоге и создание файла с объемом протестированного кода (только Windows):</span><span class="sxs-lookup"><span data-stu-id="f1f9d-231">Run the tests in the project in the current directory, and generate a code coverage file (Windows only):</span></span>

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- <span data-ttu-id="f1f9d-232">Выполнение тестов в проекте в текущем каталоге и вывод журнала с подробными сведениями в консоль:</span><span class="sxs-lookup"><span data-stu-id="f1f9d-232">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

- <span data-ttu-id="f1f9d-233">Выполнение тестов в проекте в текущем каталоге и тестов отчетов, которые выполнялись при сбое узла тестирования:</span><span class="sxs-lookup"><span data-stu-id="f1f9d-233">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="f1f9d-234">Сведения о параметре "Фильтр"</span><span class="sxs-lookup"><span data-stu-id="f1f9d-234">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="f1f9d-235">Параметр `<Expression>` имеет следующий формат: `<property><operator><value>[|&<Expression>]`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-235">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="f1f9d-236">`<property>` — это атрибут `Test Case`.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-236">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="f1f9d-237">Ниже приведены свойства, поддерживаемые популярными платформами модульных тестов.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-237">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="f1f9d-238">Тестовая платформа</span><span class="sxs-lookup"><span data-stu-id="f1f9d-238">Test Framework</span></span> | <span data-ttu-id="f1f9d-239">Поддерживаемые свойства</span><span class="sxs-lookup"><span data-stu-id="f1f9d-239">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="f1f9d-240">MSTest</span><span class="sxs-lookup"><span data-stu-id="f1f9d-240">MSTest</span></span>         | <ul><li><span data-ttu-id="f1f9d-241">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f1f9d-241">FullyQualifiedName</span></span></li><li><span data-ttu-id="f1f9d-242">name</span><span class="sxs-lookup"><span data-stu-id="f1f9d-242">Name</span></span></li><li><span data-ttu-id="f1f9d-243">ClassName</span><span class="sxs-lookup"><span data-stu-id="f1f9d-243">ClassName</span></span></li><li><span data-ttu-id="f1f9d-244">Priority</span><span class="sxs-lookup"><span data-stu-id="f1f9d-244">Priority</span></span></li><li><span data-ttu-id="f1f9d-245">TestCategory</span><span class="sxs-lookup"><span data-stu-id="f1f9d-245">TestCategory</span></span></li></ul> |
| <span data-ttu-id="f1f9d-246">xUnit</span><span class="sxs-lookup"><span data-stu-id="f1f9d-246">xUnit</span></span>          | <ul><li><span data-ttu-id="f1f9d-247">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f1f9d-247">FullyQualifiedName</span></span></li><li><span data-ttu-id="f1f9d-248">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f1f9d-248">DisplayName</span></span></li><li><span data-ttu-id="f1f9d-249">Признаки</span><span class="sxs-lookup"><span data-stu-id="f1f9d-249">Traits</span></span></li></ul>                                   |
| <span data-ttu-id="f1f9d-250">NUnit</span><span class="sxs-lookup"><span data-stu-id="f1f9d-250">NUnit</span></span>          | <ul><li><span data-ttu-id="f1f9d-251">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="f1f9d-251">FullyQualifiedName</span></span></li><li><span data-ttu-id="f1f9d-252">name</span><span class="sxs-lookup"><span data-stu-id="f1f9d-252">Name</span></span></li><li><span data-ttu-id="f1f9d-253">TestCategory</span><span class="sxs-lookup"><span data-stu-id="f1f9d-253">TestCategory</span></span></li><li><span data-ttu-id="f1f9d-254">Priority</span><span class="sxs-lookup"><span data-stu-id="f1f9d-254">Priority</span></span></li></ul>                                   |

<span data-ttu-id="f1f9d-255">`<operator>` описывает связь между свойством и значением:</span><span class="sxs-lookup"><span data-stu-id="f1f9d-255">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="f1f9d-256">Оператор</span><span class="sxs-lookup"><span data-stu-id="f1f9d-256">Operator</span></span> | <span data-ttu-id="f1f9d-257">Функция</span><span class="sxs-lookup"><span data-stu-id="f1f9d-257">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="f1f9d-258">Точное соответствие</span><span class="sxs-lookup"><span data-stu-id="f1f9d-258">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="f1f9d-259">Неточное соответствие</span><span class="sxs-lookup"><span data-stu-id="f1f9d-259">Not exact match</span></span> |
| `~`      | <span data-ttu-id="f1f9d-260">Содержит</span><span class="sxs-lookup"><span data-stu-id="f1f9d-260">Contains</span></span>        |
| `!~`     | <span data-ttu-id="f1f9d-261">Не содержит</span><span class="sxs-lookup"><span data-stu-id="f1f9d-261">Not contains</span></span>    |

<span data-ttu-id="f1f9d-262">`<value>` — это строка.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-262">`<value>` is a string.</span></span> <span data-ttu-id="f1f9d-263">Поиск выполняется без учета регистра.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-263">All the lookups are case insensitive.</span></span>

<span data-ttu-id="f1f9d-264">Выражение без `<operator>` автоматически считается функцией `contains` для свойства `FullyQualifiedName` (например, `dotnet test --filter xyz` совпадает с `dotnet test --filter FullyQualifiedName~xyz`).</span><span class="sxs-lookup"><span data-stu-id="f1f9d-264">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="f1f9d-265">Выражения можно объединять с условными операторами.</span><span class="sxs-lookup"><span data-stu-id="f1f9d-265">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="f1f9d-266">Оператор</span><span class="sxs-lookup"><span data-stu-id="f1f9d-266">Operator</span></span>            | <span data-ttu-id="f1f9d-267">Функция</span><span class="sxs-lookup"><span data-stu-id="f1f9d-267">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="f1f9d-268">OR</span><span class="sxs-lookup"><span data-stu-id="f1f9d-268">OR</span></span>       |
| `&`                 | <span data-ttu-id="f1f9d-269">AND</span><span class="sxs-lookup"><span data-stu-id="f1f9d-269">AND</span></span>      |

<span data-ttu-id="f1f9d-270">При использовании условных операторов выражения можно заключать в скобки (например, `(Name~TestMethod1) | (Name~TestMethod2)`).</span><span class="sxs-lookup"><span data-stu-id="f1f9d-270">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="f1f9d-271">Дополнительные сведения и примеры использования фильтрации при выборочном модульном тестировании см. в статье [Выполнение выборочных модульных тестов](../testing/selective-unit-tests.md).</span><span class="sxs-lookup"><span data-stu-id="f1f9d-271">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f1f9d-272">См. также</span><span class="sxs-lookup"><span data-stu-id="f1f9d-272">See also</span></span>

- [<span data-ttu-id="f1f9d-273">Платформы и целевые объекты</span><span class="sxs-lookup"><span data-stu-id="f1f9d-273">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="f1f9d-274">Каталог идентификаторов сред выполнения (RID) .NET</span><span class="sxs-lookup"><span data-stu-id="f1f9d-274">.NET Runtime Identifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="f1f9d-275">Передача аргументов runsettings через командную строку</span><span class="sxs-lookup"><span data-stu-id="f1f9d-275">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
