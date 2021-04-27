---
title: Средство диагностики dotnet-dump — .NET CLI
description: Узнайте, как установить и использовать средство CLI dotnet-dump для накопления и анализа дампов Windows и Linux без использования отладчика машинного кода.
ms.date: 11/17/2020
ms.topic: reference
ms.openlocfilehash: 57149c9330d6057ea57a32bfa6582a73ed6b6dee
ms.sourcegitcommit: 8f71a6c655a9c39d5223401aed76c02ba00e03ee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2021
ms.locfileid: "107740609"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="5ac61-103">Программа для сбора и анализа дампов (dotnet-dump)</span><span class="sxs-lookup"><span data-stu-id="5ac61-103">Dump collection and analysis utility (dotnet-dump)</span></span>

<span data-ttu-id="5ac61-104">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 3.0 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="5ac61-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="5ac61-105">`dotnet-dump` для macOS поддерживается только в .NET 5.0 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="5ac61-105">`dotnet-dump` for macOS is only supported with .NET 5.0 and later versions.</span></span>

## <a name="install"></a><span data-ttu-id="5ac61-106">Установка</span><span class="sxs-lookup"><span data-stu-id="5ac61-106">Install</span></span>

<span data-ttu-id="5ac61-107">Есть два способа загрузки и установки `dotnet-dump`:</span><span class="sxs-lookup"><span data-stu-id="5ac61-107">There are two ways to download and install `dotnet-dump`:</span></span>

- <span data-ttu-id="5ac61-108">**Средство dotnet global:**</span><span class="sxs-lookup"><span data-stu-id="5ac61-108">**dotnet global tool:**</span></span>

  <span data-ttu-id="5ac61-109">Чтобы установить последнюю версию [пакета NuGet](https://www.nuget.org/packages/dotnet-dump) `dotnet-dump`, используйте команду [dotnet tool install](../tools/dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="5ac61-109">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-dump
  ```

- <span data-ttu-id="5ac61-110">**Прямое скачивание:**</span><span class="sxs-lookup"><span data-stu-id="5ac61-110">**Direct download:**</span></span>

  <span data-ttu-id="5ac61-111">скачайте исполняемый файл средства, соответствующий вашей платформе:</span><span class="sxs-lookup"><span data-stu-id="5ac61-111">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="5ac61-112">OS</span><span class="sxs-lookup"><span data-stu-id="5ac61-112">OS</span></span>  | <span data-ttu-id="5ac61-113">Платформа</span><span class="sxs-lookup"><span data-stu-id="5ac61-113">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="5ac61-114">Windows</span><span class="sxs-lookup"><span data-stu-id="5ac61-114">Windows</span></span> | <span data-ttu-id="5ac61-115">[x86](https://aka.ms/dotnet-dump/win-x86) \| [x64](https://aka.ms/dotnet-dump/win-x64) \| [arm](https://aka.ms/dotnet-dump/win-arm) \| [arm-x64](https://aka.ms/dotnet-dump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="5ac61-115">[x86](https://aka.ms/dotnet-dump/win-x86) \| [x64](https://aka.ms/dotnet-dump/win-x64) \| [arm](https://aka.ms/dotnet-dump/win-arm) \| [arm-x64](https://aka.ms/dotnet-dump/win-arm64)</span></span> |
  | <span data-ttu-id="5ac61-116">macOS</span><span class="sxs-lookup"><span data-stu-id="5ac61-116">macOS</span></span>   | [<span data-ttu-id="5ac61-117">x64</span><span class="sxs-lookup"><span data-stu-id="5ac61-117">x64</span></span>](https://aka.ms/dotnet-dump/osx-x64) |
  | <span data-ttu-id="5ac61-118">Linux</span><span class="sxs-lookup"><span data-stu-id="5ac61-118">Linux</span></span>   | <span data-ttu-id="5ac61-119">[x64](https://aka.ms/dotnet-dump/linux-x64) \| [arm](https://aka.ms/dotnet-dump/linux-arm) \| [arm64](https://aka.ms/dotnet-dump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-dump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-dump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="5ac61-119">[x64](https://aka.ms/dotnet-dump/linux-x64) \| [arm](https://aka.ms/dotnet-dump/linux-arm) \| [arm64](https://aka.ms/dotnet-dump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-dump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-dump/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="5ac61-120">Для использования `dotnet-dump` в приложении x86 необходима соответствующая версия средства для архитектуры x86.</span><span class="sxs-lookup"><span data-stu-id="5ac61-120">To use `dotnet-dump` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5ac61-121">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="5ac61-121">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="5ac61-122">Описание</span><span class="sxs-lookup"><span data-stu-id="5ac61-122">Description</span></span>

<span data-ttu-id="5ac61-123">`dotnet-dump` — это средство сбора и анализа дампов в Windows и Linux, которое не задействует собственный отладчик системы (как, например, `lldb` в Linux).</span><span class="sxs-lookup"><span data-stu-id="5ac61-123">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="5ac61-124">Это средство имеет важное значение на таких платформах, как Alpine Linux, где отсутствует полноценно работающее средство `lldb`.</span><span class="sxs-lookup"><span data-stu-id="5ac61-124">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="5ac61-125">Средство `dotnet-dump` позволяет выполнять команды SOS для анализа сбоев и сборщика мусора (GC), но не поддерживает некоторые функции, как, например, отображение собственных кадров стека, потому что не является встроенным отладчиком.</span><span class="sxs-lookup"><span data-stu-id="5ac61-125">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="5ac61-126">Параметры</span><span class="sxs-lookup"><span data-stu-id="5ac61-126">Options</span></span>

- **`--version`**

  <span data-ttu-id="5ac61-127">Отображение версии служебной программы dotnet-dump.</span><span class="sxs-lookup"><span data-stu-id="5ac61-127">Displays the version of the dotnet-dump utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5ac61-128">Отображение справки в командной строке.</span><span class="sxs-lookup"><span data-stu-id="5ac61-128">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="5ac61-129">Команды</span><span class="sxs-lookup"><span data-stu-id="5ac61-129">Commands</span></span>

| <span data-ttu-id="5ac61-130">Команда</span><span class="sxs-lookup"><span data-stu-id="5ac61-130">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="5ac61-131">dotnet-dump collect</span><span class="sxs-lookup"><span data-stu-id="5ac61-131">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="5ac61-132">dotnet-dump analyze</span><span class="sxs-lookup"><span data-stu-id="5ac61-132">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="5ac61-133">dotnet-dump collect</span><span class="sxs-lookup"><span data-stu-id="5ac61-133">dotnet-dump collect</span></span>

<span data-ttu-id="5ac61-134">Записывает дамп из процесса.</span><span class="sxs-lookup"><span data-stu-id="5ac61-134">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="5ac61-135">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="5ac61-135">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [-n|--name] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="5ac61-136">Параметры</span><span class="sxs-lookup"><span data-stu-id="5ac61-136">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="5ac61-137">Отображение справки в командной строке.</span><span class="sxs-lookup"><span data-stu-id="5ac61-137">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="5ac61-138">Указывает идентификатор процесса, из которого нужно собрать дамп.</span><span class="sxs-lookup"><span data-stu-id="5ac61-138">Specifies the process ID number to collect a dump from.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="5ac61-139">Имя процесса, из которого нужно получить дамп.</span><span class="sxs-lookup"><span data-stu-id="5ac61-139">Specifies the name of the process to collect a dump from.</span></span>

- **`--type <Full|Heap|Mini>`**

  <span data-ttu-id="5ac61-140">Указывает тип дампа, который определяет типы собираемых из процесса данных.</span><span class="sxs-lookup"><span data-stu-id="5ac61-140">Specifies the dump type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="5ac61-141">Здесь возможны три варианта:</span><span class="sxs-lookup"><span data-stu-id="5ac61-141">There are three types:</span></span>

  - <span data-ttu-id="5ac61-142">`Full` — самый крупный дамп, содержащий всю память, включая образы модулей.</span><span class="sxs-lookup"><span data-stu-id="5ac61-142">`Full` - The largest dump containing all memory including the module images.</span></span>
  - <span data-ttu-id="5ac61-143">`Heap` — большой и сравнительно подробный дамп, который содержит списки модулей, списки потоков, все стеки, сведения об исключениях, сведения об обработке и всю память, за исключением сопоставленных образов.</span><span class="sxs-lookup"><span data-stu-id="5ac61-143">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="5ac61-144">`Mini` — небольшой дамп, который содержит списки модулей, списки потоков, сведения об исключениях и все стеки.</span><span class="sxs-lookup"><span data-stu-id="5ac61-144">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="5ac61-145">Если тип не указан, по умолчанию используется вариант `Full`.</span><span class="sxs-lookup"><span data-stu-id="5ac61-145">If not specified, `Full` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="5ac61-146">Полный путь и имя файла, в который будет записан собранный дамп.</span><span class="sxs-lookup"><span data-stu-id="5ac61-146">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="5ac61-147">Если значение не указано, используются следующие:</span><span class="sxs-lookup"><span data-stu-id="5ac61-147">If not specified:</span></span>

  - <span data-ttu-id="5ac61-148">*.\dump_YYYYMMDD_HHMMSS.dmp* в ОС Windows;</span><span class="sxs-lookup"><span data-stu-id="5ac61-148">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="5ac61-149">*./core_YYYYMMDD_HHMMSS* в ОС Linux.</span><span class="sxs-lookup"><span data-stu-id="5ac61-149">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="5ac61-150">YYYYMMDD обозначает формат "год/месяц/день", а HHMMSS — формат "час/минута/секунда".</span><span class="sxs-lookup"><span data-stu-id="5ac61-150">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="5ac61-151">Включает ведение журнала диагностики для сбора дампов.</span><span class="sxs-lookup"><span data-stu-id="5ac61-151">Enables dump collection diagnostic logging.</span></span>

> [!NOTE]
> <span data-ttu-id="5ac61-152">В Linux и macOS эта команда ожидает, что целевое приложение и `dotnet-dump` будут совместно использовать одну и ту же переменную среды `TMPDIR`.</span><span class="sxs-lookup"><span data-stu-id="5ac61-152">On Linux and macOS, this command expects the target application and `dotnet-dump` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="5ac61-153">В противном случае время ожидания команды истечет.</span><span class="sxs-lookup"><span data-stu-id="5ac61-153">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="5ac61-154">Чтобы собрать дамп с помощью `dotnet-dump`, ее необходимо запустить от имени пользователя, запустившего целевой процесс, или от имени привилегированного пользователя.</span><span class="sxs-lookup"><span data-stu-id="5ac61-154">To collect a dump using `dotnet-dump`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="5ac61-155">В противном случае средство не сможет установить соединение с целевым процессом.</span><span class="sxs-lookup"><span data-stu-id="5ac61-155">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="5ac61-156">dotnet-dump analyze</span><span class="sxs-lookup"><span data-stu-id="5ac61-156">dotnet-dump analyze</span></span>

<span data-ttu-id="5ac61-157">Запускает интерактивную оболочку для просмотра дампа.</span><span class="sxs-lookup"><span data-stu-id="5ac61-157">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="5ac61-158">Эта оболочка принимает различные [команды SOS](#analyze-sos-commands).</span><span class="sxs-lookup"><span data-stu-id="5ac61-158">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="5ac61-159">Краткий обзор</span><span class="sxs-lookup"><span data-stu-id="5ac61-159">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="5ac61-160">Аргументы</span><span class="sxs-lookup"><span data-stu-id="5ac61-160">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="5ac61-161">Указывает путь к анализируемому файлу дампа.</span><span class="sxs-lookup"><span data-stu-id="5ac61-161">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="5ac61-162">Параметры</span><span class="sxs-lookup"><span data-stu-id="5ac61-162">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="5ac61-163">Указывает [команду](#analyze-sos-commands), которую нужно выполнить при запуске оболочки.</span><span class="sxs-lookup"><span data-stu-id="5ac61-163">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="5ac61-164">Анализ команд SOS</span><span class="sxs-lookup"><span data-stu-id="5ac61-164">Analyze SOS commands</span></span>

| <span data-ttu-id="5ac61-165">Команда</span><span class="sxs-lookup"><span data-stu-id="5ac61-165">Command</span></span>                             | <span data-ttu-id="5ac61-166">Функция</span><span class="sxs-lookup"><span data-stu-id="5ac61-166">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="5ac61-167">Отображение всех доступных команд.</span><span class="sxs-lookup"><span data-stu-id="5ac61-167">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="5ac61-168">Отображение сведений об указанной команде.</span><span class="sxs-lookup"><span data-stu-id="5ac61-168">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="5ac61-169">Выход из интерактивного режима.</span><span class="sxs-lookup"><span data-stu-id="5ac61-169">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="5ac61-170">Обеспечивает трассировку стека только для управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="5ac61-170">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="5ac61-171">Перечисление всех выполняемых управляемых потоков.</span><span class="sxs-lookup"><span data-stu-id="5ac61-171">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="5ac61-172">Отображение информации о машинах асинхронной обработки для кучи со сборкой мусора.</span><span class="sxs-lookup"><span data-stu-id="5ac61-172">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="5ac61-173">Отображение сведений о сборке, находящейся по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="5ac61-173">Displays details about the assembly at the specified address.</span></span>                                 |
| `dumpclass <arguments>`             | <span data-ttu-id="5ac61-174">Отображение сведений о структуре `EEClass`, находящейся по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="5ac61-174">Displays information about the `EEClass` structure at the specified address.</span></span>                  |
| `dumpdelegate <arguments>`          | <span data-ttu-id="5ac61-175">Отображение сведений о делегате, находящемся по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="5ac61-175">Displays information about the delegate at the specified address.</span></span>                             |
| `dumpdomain <arguments>`            | <span data-ttu-id="5ac61-176">Отображение сведений обо всех доменах приложений и всех сборках в указанных доменах.</span><span class="sxs-lookup"><span data-stu-id="5ac61-176">Displays information all the AppDomains and all assemblies within the specified domain.</span></span>       |
| `dumpheap <arguments>`              | <span data-ttu-id="5ac61-177">Отображение сведений о куче со сборкой мусора и статистики сборки мусора по объектам.</span><span class="sxs-lookup"><span data-stu-id="5ac61-177">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="5ac61-178">Отображает язык CIL, связанный с управляемым методом.</span><span class="sxs-lookup"><span data-stu-id="5ac61-178">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="5ac61-179">Записывает в указанный файл содержимое журнала нагрузок, хранящегося в памяти.</span><span class="sxs-lookup"><span data-stu-id="5ac61-179">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="5ac61-180">Отображение сведений о структуре `MethodDesc`, находящейся по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="5ac61-180">Displays information about the `MethodDesc` structure at the specified address.</span></span>               |
| `dumpmodule <arguments>`            | <span data-ttu-id="5ac61-181">Отображение сведений о модуле, находящемся по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="5ac61-181">Displays information about the module at the specified address.</span></span>                               |
| `dumpmt <arguments>`                | <span data-ttu-id="5ac61-182">Отображение сведений об объекте `MethodTable`, находящемся по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="5ac61-182">Displays information about the `MethodTable` at the specified address.</span></span>                        |
| `dumpobj <arguments>`               | <span data-ttu-id="5ac61-183">Отображение сведений об объекте, находящемся по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="5ac61-183">Displays info about the object at the specified address.</span></span>                                      |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="5ac61-184">Отображает все управляемые объекты, обнаруженные в пределах границ текущего стека.</span><span class="sxs-lookup"><span data-stu-id="5ac61-184">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="5ac61-185">Отображение сведений о памяти процессов, занятой внутренними структурами данных среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="5ac61-185">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="5ac61-186">Отображает все объекты, зарегистрированные для заключительной обработки.</span><span class="sxs-lookup"><span data-stu-id="5ac61-186">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="5ac61-187">Отображение сведений о ссылках (или корневых элементах) объекта, который расположен по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="5ac61-187">Displays info about references (or roots) to the object at the specified address.</span></span>             |
| `gcwhere <arguments>`               | <span data-ttu-id="5ac61-188">Отображение расположения переданного аргумента в куче со сборкой мусора.</span><span class="sxs-lookup"><span data-stu-id="5ac61-188">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="5ac61-189">Отображение структуры `MethodDesc`, которая расположена по указанному адресу в JIT-коде.</span><span class="sxs-lookup"><span data-stu-id="5ac61-189">Displays the `MethodDesc` structure at the specified address in JIT code.</span></span>                     |
| `histclear <arguments>`             | <span data-ttu-id="5ac61-190">Освобождает все ресурсы, используемые семейством команд `hist*`.</span><span class="sxs-lookup"><span data-stu-id="5ac61-190">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="5ac61-191">Инициализирует структуры SOS из журнала нагрузки, сохраненного в отлаживаемом объекте.</span><span class="sxs-lookup"><span data-stu-id="5ac61-191">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="5ac61-192">Отображение перераспределений журнала нагрузок для сборки мусора, связанных с `<arguments>`.</span><span class="sxs-lookup"><span data-stu-id="5ac61-192">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="5ac61-193">Отображение всех записей журнала, ссылающихся на объект по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="5ac61-193">Displays all the log entries that reference the object at the specified address.</span></span>              |
| `histroot <arguments>`              | <span data-ttu-id="5ac61-194">Отображает сведения о повышениях и перемещениях указанного корневого элемента.</span><span class="sxs-lookup"><span data-stu-id="5ac61-194">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="5ac61-195">Отображение выполняемых собственных модулей.</span><span class="sxs-lookup"><span data-stu-id="5ac61-195">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="5ac61-196">Отображение структур `MethodTable` и `EEClass` для `<argument>`.</span><span class="sxs-lookup"><span data-stu-id="5ac61-196">Displays the `MethodTable` and `EEClass` structures for the `<argument>`.</span></span>                     |
| `pe|printexception <arguments>`     | <span data-ttu-id="5ac61-197">Отображение любого производного от класса <xref:System.Exception> объекта для `<argument>`.</span><span class="sxs-lookup"><span data-stu-id="5ac61-197">Displays any object derived from the <xref:System.Exception> class for the `<argument>`.</span></span>      |
| `setsymbolserver <arguments>`       | <span data-ttu-id="5ac61-198">Включение поддержки сервера символов</span><span class="sxs-lookup"><span data-stu-id="5ac61-198">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="5ac61-199">Отображение сведений о заполнителе SyncBlock.</span><span class="sxs-lookup"><span data-stu-id="5ac61-199">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="5ac61-200">Отображение или изменение идентификатора текущего потока для команд SOS.</span><span class="sxs-lookup"><span data-stu-id="5ac61-200">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

> [!NOTE]
> <span data-ttu-id="5ac61-201">Дополнительные сведения см. в разделе [Расширение отладки SOS для .NET](sos-debugging-extension.md).</span><span class="sxs-lookup"><span data-stu-id="5ac61-201">Additional details can be found in [SOS Debugging Extension for .NET](sos-debugging-extension.md).</span></span>

## <a name="using-dotnet-dump"></a><span data-ttu-id="5ac61-202">Использование `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="5ac61-202">Using `dotnet-dump`</span></span>

<span data-ttu-id="5ac61-203">Первым шагом является сборка дампа.</span><span class="sxs-lookup"><span data-stu-id="5ac61-203">The first step is to collect a dump.</span></span> <span data-ttu-id="5ac61-204">Этот шаг можно пропустить, если уже создан основной дамп.</span><span class="sxs-lookup"><span data-stu-id="5ac61-204">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="5ac61-205">Основные дампы могут создавать как операционная система, так и встроенная в среду выполнения .NET Core [функция создания дампа](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/botr/xplat-minidump-generation.md).</span><span class="sxs-lookup"><span data-stu-id="5ac61-205">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/runtime/blob/main/docs/design/coreclr/botr/xplat-minidump-generation.md) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="5ac61-206">Теперь запустите анализ основного дампа с помощью команды `analyze`:</span><span class="sxs-lookup"><span data-stu-id="5ac61-206">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="5ac61-207">Это действие открывает интерактивный сеанс, который принимает команды следующего вида:</span><span class="sxs-lookup"><span data-stu-id="5ac61-207">This action brings up an interactive session that accepts commands like:</span></span>

```console
> clrstack
OS Thread Id: 0x573d (0)
    Child SP               IP Call Site
00007FFD28B42C58 00007fb22c1a8ed9 [HelperMethodFrame_PROTECTOBJ: 00007ffd28b42c58] System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo) [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.Program.Foo4(System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.Program.Foo2(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.Program.Foo1(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.Program.Main(System.String[]) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]
00007FFD28B43210 00007fb22aa9cedf [GCFrame: 00007ffd28b43210]
00007FFD28B43610 00007fb22aa9cedf [GCFrame: 00007ffd28b43610]
```

<span data-ttu-id="5ac61-208">Чтобы получить сведения о необработанном исключении, которое привело к сбою приложения, выполните:</span><span class="sxs-lookup"><span data-stu-id="5ac61-208">To see an unhandled exception that killed your app:</span></span>

```console
> pe -lines
Exception object: 00007fb18c038590
Exception type:   System.Reflection.TargetInvocationException
Message:          Exception has been thrown by the target of an invocation.
InnerException:   System.Exception, Use !PrintException 00007FB18C038368 to see more.
StackTrace (generated):
SP               IP               Function
00007FFD28B42DD0 0000000000000000 System.Private.CoreLib.dll!System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Private.CoreLib.dll!System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo)+0xa7 [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.dll!SymbolTestApp.Program.Foo4(System.String)+0x15d [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.dll!SymbolTestApp.Program.Foo2(Int32, System.String)+0x34 [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.dll!SymbolTestApp.Program.Foo1(Int32, System.String)+0x3a [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.dll!SymbolTestApp.Program.Main(System.String[])+0x6e [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]

StackTraceString: <none>
HResult: 80131604
```

## <a name="special-instructions-for-docker"></a><span data-ttu-id="5ac61-209">Особые инструкции для Docker</span><span class="sxs-lookup"><span data-stu-id="5ac61-209">Special instructions for Docker</span></span>

<span data-ttu-id="5ac61-210">Если вы используете Docker, для сбора дампа требуются возможности `SYS_PTRACE` (`--cap-add=SYS_PTRACE` или `--privileged`).</span><span class="sxs-lookup"><span data-stu-id="5ac61-210">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="5ac61-211">В образах Docker с Linux и пакетом SDK для Microsoft .NET Core некоторые команды `dotnet-dump` могут вызвать следующее исключение:</span><span class="sxs-lookup"><span data-stu-id="5ac61-211">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="5ac61-212">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception. (Необработанное исключение: System.DllNotFoundException: Не удалось загрузить общую библиотеку libdl.so или одну из ее зависимостей.)</span><span class="sxs-lookup"><span data-stu-id="5ac61-212">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="5ac61-213">Чтобы обойти эту проблему, установите пакет libc6-dev.</span><span class="sxs-lookup"><span data-stu-id="5ac61-213">To work around this problem, install the "libc6-dev" package.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ac61-214">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5ac61-214">See also</span></span>

- [<span data-ttu-id="5ac61-215">Сбор и анализ блога дампов памяти</span><span class="sxs-lookup"><span data-stu-id="5ac61-215">Collecting and analyzing memory dumps blog</span></span>](https://devblogs.microsoft.com/dotnet/collecting-and-analyzing-memory-dumps/)
- [<span data-ttu-id="5ac61-216">Средство анализа кучи (dotnet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="5ac61-216">Heap analysis tool (dotnet-gcdump)</span></span>](dotnet-gcdump.md)
