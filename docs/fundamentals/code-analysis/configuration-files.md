---
title: Файлы конфигурации для правил анализа кода
description: Сведения о различных файлах конфигурации для настройки правил анализа кода.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 0d64df42ffb1763afed3e883c4f043755e158489
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633992"
---
# <a name="configuration-files-for-code-analysis-rules"></a><span data-ttu-id="ba97d-103">Файлы конфигурации для правил анализа кода</span><span class="sxs-lookup"><span data-stu-id="ba97d-103">Configuration files for code analysis rules</span></span>

<span data-ttu-id="ba97d-104">Правила анализа кода имеют различные [Параметры конфигурации](configuration-options.md).</span><span class="sxs-lookup"><span data-stu-id="ba97d-104">Code analysis rules have various [configuration options](configuration-options.md).</span></span> <span data-ttu-id="ba97d-105">Эти параметры указываются в виде пар "ключ-значение" в одном из следующих файлов конфигурации анализатора:</span><span class="sxs-lookup"><span data-stu-id="ba97d-105">You specify these options as key-value pairs in one of the following analyzer configuration files:</span></span>

- <span data-ttu-id="ba97d-106">[EditorConfig](#editorconfig) файл: параметры конфигурации на основе файлов или папок.</span><span class="sxs-lookup"><span data-stu-id="ba97d-106">[EditorConfig](#editorconfig) file: File-based or folder-based configuration options.</span></span>
- <span data-ttu-id="ba97d-107">[Глобальный файл анализерконфиг](#global-analyzerconfig) : параметры конфигурации на уровне проекта.</span><span class="sxs-lookup"><span data-stu-id="ba97d-107">[Global AnalyzerConfig](#global-analyzerconfig) file: Project-level configuration options.</span></span>

## EditorConfig

<span data-ttu-id="ba97d-108">[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) файлы используются для предоставления **параметров, которые применяются к конкретным исходным файлам или папкам**.</span><span class="sxs-lookup"><span data-stu-id="ba97d-108">[EditorConfig](/visualstudio/ide/create-portable-custom-editor-options) files are used to provide **options that apply to specific source files or folders**.</span></span> <span data-ttu-id="ba97d-109">Параметры размещаются в разделе Заголовки разделов, чтобы найти соответствующие файлы и папки.</span><span class="sxs-lookup"><span data-stu-id="ba97d-109">Options are placed under section headers to identify the applicable files and folders.</span></span> <span data-ttu-id="ba97d-110">Добавьте запись для каждого правила, которое необходимо настроить, и разместите его в соответствующем разделе расширения файла, например `[*.cs]` .</span><span class="sxs-lookup"><span data-stu-id="ba97d-110">Add an entry for each rule you want to configure, and place it under the corresponding file extension section, for example, `[*.cs]`.</span></span>

```ini
[*.cs]
<option_name> = <option_value>
```

<span data-ttu-id="ba97d-111">В приведенном выше примере `[*.cs]` — это заголовок раздела editorconfig для выбора всех файлов C# с `.cs` расширением файла в текущей папке, включая вложенные папки.</span><span class="sxs-lookup"><span data-stu-id="ba97d-111">In the above example, `[*.cs]` is an editorconfig section header to select all C# files with `.cs` file extension within the current folder, including subfolders.</span></span> <span data-ttu-id="ba97d-112">Последующая запись `<option_name> = <option_value>` — это параметр анализатора, который будет применяться ко всем файлам C#.</span><span class="sxs-lookup"><span data-stu-id="ba97d-112">The subsequent entry, `<option_name> = <option_value>`, is an analyzer option that will be applied to all the C# files.</span></span>

<span data-ttu-id="ba97d-113">EditorConfigСоглашения о файлах можно применить к папке, проекту или всему репозиторию, поместив файл в соответствующий каталог.</span><span class="sxs-lookup"><span data-stu-id="ba97d-113">You can apply EditorConfig file conventions to a folder, a project, or an entire repo by placing the file in the corresponding directory.</span></span> <span data-ttu-id="ba97d-114">Эти параметры применяются при выполнении анализа во время сборки, а также при редактировании кода в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ba97d-114">These options are applied when executing the analysis at build time and while you edit code in Visual Studio.</span></span>

<span data-ttu-id="ba97d-115">Если у вас есть файл *. editorconfig* для параметров редактора, таких как размер отступа или необходимость обрезать пробелы в конце, можно поместить параметры конфигурации анализа кода в тот же файл.</span><span class="sxs-lookup"><span data-stu-id="ba97d-115">If you have an existing *.editorconfig* file for editor settings such as indent size or whether to trim trailing whitespace, you can place your code analysis configuration options in the same file.</span></span>

> [!TIP]
> <span data-ttu-id="ba97d-116">Visual Studio предоставляет шаблон элемента *. editorconfig* , который упрощает добавление одного из этих файлов в проект.</span><span class="sxs-lookup"><span data-stu-id="ba97d-116">Visual Studio provides an *.editorconfig* item template that makes is easy to add one of these files to your project.</span></span> <span data-ttu-id="ba97d-117">Дополнительные сведения см. [в разделе Добавление EditorConfig файла в проект](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).</span><span class="sxs-lookup"><span data-stu-id="ba97d-117">For more information, see [Add an EditorConfig file to a project](/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).</span></span>

### <a name="example"></a><span data-ttu-id="ba97d-118">Пример</span><span class="sxs-lookup"><span data-stu-id="ba97d-118">Example</span></span>

<span data-ttu-id="ba97d-119">Ниже приведен пример EditorConfig файла для настройки параметров и серьезности правила.</span><span class="sxs-lookup"><span data-stu-id="ba97d-119">Following is an example EditorConfig file to configure options and rule severity:</span></span>

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="global-analyzerconfig"></a><span data-ttu-id="ba97d-120">Глобальная Анализерконфиг</span><span class="sxs-lookup"><span data-stu-id="ba97d-120">Global AnalyzerConfig</span></span>

<span data-ttu-id="ba97d-121">Начиная с пакета SDK для .NET 5 (который поддерживается в Visual Studio 2019 версии 16,8 и более поздних версиях), можно также настроить параметры анализатора с помощью глобальных файлов _анализерконфиг_ .</span><span class="sxs-lookup"><span data-stu-id="ba97d-121">Starting with the .NET 5 SDK (which is supported in Visual Studio 2019 version 16.8 and later versions), you can also configure analyzer options with global _AnalyzerConfig_ files.</span></span> <span data-ttu-id="ba97d-122">Эти файлы используются для предоставления **параметров, которые применяются ко всем исходным файлам в проекте**, независимо от их имен или путей к файлам.</span><span class="sxs-lookup"><span data-stu-id="ba97d-122">These files are used to provide **options that apply to all the source files in a project**, regardless of their file names or file paths.</span></span>

<span data-ttu-id="ba97d-123">В отличие от [EditorConfig](#editorconfig) файлов глобальные файлы конфигурации нельзя использовать для настройки параметров стиля редактора для IDE, таких как размер отступа или необходимость обрезки конечных пробелов.</span><span class="sxs-lookup"><span data-stu-id="ba97d-123">Unlike [EditorConfig](#editorconfig) files, global config files can't be used to configure editor style settings for IDEs, such as indent size or whether to trim trailing whitespace.</span></span> <span data-ttu-id="ba97d-124">Вместо этого они предназначены исключительно для указания параметров конфигурации анализатора уровня проекта.</span><span class="sxs-lookup"><span data-stu-id="ba97d-124">Instead, they are designed purely for specifying project-level analyzer configuration options.</span></span>

### <a name="format"></a><span data-ttu-id="ba97d-125">Формат</span><span class="sxs-lookup"><span data-stu-id="ba97d-125">Format</span></span>

<span data-ttu-id="ba97d-126">В отличие от EditorConfig файлов, которые должны иметь заголовки разделов, например `[*.cs]` , для обнаружения подходящих файлов и папок, глобальные файлы анализерконфиг не имеют заголовков разделов.</span><span class="sxs-lookup"><span data-stu-id="ba97d-126">Unlike EditorConfig files, which must have section headers, such as `[*.cs]`, to identify the applicable files and folders, global AnalyzerConfig files don't have section headers.</span></span> <span data-ttu-id="ba97d-127">Вместо этого им требуется запись верхнего уровня формы, `is_global = true` чтобы отличать их от обычных EditorConfig файлов.</span><span class="sxs-lookup"><span data-stu-id="ba97d-127">Instead, they require a top level entry of the form `is_global = true` to differentiate them from regular EditorConfig files.</span></span> <span data-ttu-id="ba97d-128">Это означает, что все параметры в файле применяются ко всему проекту.</span><span class="sxs-lookup"><span data-stu-id="ba97d-128">This indicates that all the options in the file apply to the entire project.</span></span> <span data-ttu-id="ba97d-129">Пример:</span><span class="sxs-lookup"><span data-stu-id="ba97d-129">For example:</span></span>

```ini
is_global = true
<option_name> = <option_value>
```

### <a name="naming"></a><span data-ttu-id="ba97d-130">Именование</span><span class="sxs-lookup"><span data-stu-id="ba97d-130">Naming</span></span>

<span data-ttu-id="ba97d-131">В отличие от EditorConfig файлов, которые должны называться `.editorconfig` , глобальные файлы конфигурации не обязательно должны иметь определенное имя или расширение.</span><span class="sxs-lookup"><span data-stu-id="ba97d-131">Unlike EditorConfig files, which must be named `.editorconfig`, global config files do not need to have a specific name or extension.</span></span> <span data-ttu-id="ba97d-132">Однако если вы назначите эти файлы как, `.globalconfig` они будут неявно применены ко всем проектам C# и Visual Basic в текущей папке, включая вложенные папки.</span><span class="sxs-lookup"><span data-stu-id="ba97d-132">However, if you name these files as `.globalconfig` then they will be implicitly applied to all the C# and Visual Basic projects within the current folder, including subfolders.</span></span> <span data-ttu-id="ba97d-133">В противном случае необходимо явно добавить `GlobalAnalyzerConfigFiles` элемент в файл проекта MSBuild:</span><span class="sxs-lookup"><span data-stu-id="ba97d-133">Otherwise, you must explicitly add the `GlobalAnalyzerConfigFiles` item to your MSBuild project file:</span></span>

```xml
<ItemGroup>
  <GlobalAnalyzerConfigFiles Include="<path_to_global_analyzer_config>" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="ba97d-134">Запись верхнего уровня требуется, `is_global = true` даже если файл называется `.globalconfig` .</span><span class="sxs-lookup"><span data-stu-id="ba97d-134">The top-level entry `is_global = true` is required even when the file is named `.globalconfig`.</span></span>

### <a name="example"></a><span data-ttu-id="ba97d-135">Пример</span><span class="sxs-lookup"><span data-stu-id="ba97d-135">Example</span></span>

<span data-ttu-id="ba97d-136">Ниже приведен пример глобального файла Анализерконфиг для настройки параметров и серьезности правил на уровне проекта.</span><span class="sxs-lookup"><span data-stu-id="ba97d-136">Following is an example global AnalyzerConfig file to configure options and rule severity at the project level:</span></span>

```ini
# Top level entry required to mark this as a global AnalyzerConfig file
is_global = true

# NOTE: No section headers for configuration entries

#### .NET Coding Conventions ####

# this. and Me. preferences
dotnet_style_qualification_for_method = true:warning

#### Diagnostic configuration ####

# CA1000: Do not declare static members on generic types
dotnet_diagnostic.CA1000.severity = warning
```

## <a name="precedence"></a><span data-ttu-id="ba97d-137">Приоритет</span><span class="sxs-lookup"><span data-stu-id="ba97d-137">Precedence</span></span>

<span data-ttu-id="ba97d-138">Оба EditorConfig файла и глобальные файлы анализерконфиг задают пару "ключ-значение" для каждого параметра.</span><span class="sxs-lookup"><span data-stu-id="ba97d-138">Both EditorConfig files and global AnalyzerConfig files specify a key-value pair for each option.</span></span> <span data-ttu-id="ba97d-139">Конфликты возникают, когда имеется несколько записей с одинаковым ключом, но разными значениями.</span><span class="sxs-lookup"><span data-stu-id="ba97d-139">Conflicts arise when there are multiple entries with the same key but different values.</span></span>

### <a name="general-options"></a><span data-ttu-id="ba97d-140">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="ba97d-140">General options</span></span>

<span data-ttu-id="ba97d-141">При возникновении конфликтов между параметрами для разрешения конфликтов используются следующие правила приоритета.</span><span class="sxs-lookup"><span data-stu-id="ba97d-141">When conflicts arise between options, the following precedence rules are used to resolve the conflicts:</span></span>

- <span data-ttu-id="ba97d-142">Конфликтующие записи в одном файле конфигурации: запись, которая появляется позже в файле WINS.</span><span class="sxs-lookup"><span data-stu-id="ba97d-142">Conflicting entries in the same configuration file: The entry that appears later in the file wins.</span></span> <span data-ttu-id="ba97d-143">Это справедливо для конфликтующих записей в одном EditorConfig файле, а также в одном глобальном файле анализерконфиг.</span><span class="sxs-lookup"><span data-stu-id="ba97d-143">This is true for conflicting entries within a single EditorConfig file and also within a single global AnalyzerConfig file.</span></span>

- <span data-ttu-id="ba97d-144">Конфликтующие записи в двух EditorConfig файлах: запись в EditorConfig файле, которая находится глубже в файловой системе и, следовательно, имеет более длинный путь к файлу, WINS.</span><span class="sxs-lookup"><span data-stu-id="ba97d-144">Conflicting entries in two EditorConfig files: The entry in the EditorConfig file that's deeper in the file system, and hence has a longer file path, wins.</span></span>

- <span data-ttu-id="ba97d-145">Конфликтующие записи в двух глобальных файлах Анализерконфиг: выводится предупреждение компилятора, и обе записи игнорируются.</span><span class="sxs-lookup"><span data-stu-id="ba97d-145">Conflicting entries in two global AnalyzerConfig files: A compiler warning is reported and both entries are ignored.</span></span>

- <span data-ttu-id="ba97d-146">Конфликтующие записи в EditorConfig файле и глобальном файле анализерконфиг: запись в EditorConfig файле WINS.</span><span class="sxs-lookup"><span data-stu-id="ba97d-146">Conflicting entries in an EditorConfig file and a Global AnalyzerConfig file: The entry in the EditorConfig file wins.</span></span>

### <a name="severity-options"></a><span data-ttu-id="ba97d-147">Параметры серьезности</span><span class="sxs-lookup"><span data-stu-id="ba97d-147">Severity options</span></span>

<span data-ttu-id="ba97d-148">Предыдущие [Общие правила приоритета](#general-options) применяются ко всем параметрам, указанным в файлах конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ba97d-148">The previous [general precedence rules](#general-options) apply for all options specified in configuration files.</span></span> <span data-ttu-id="ba97d-149">Для параметров [конфигурации с уровнем серьезности](configuration-options.md#severity-level) применяются следующие дополнительные правила приоритета.</span><span class="sxs-lookup"><span data-stu-id="ba97d-149">For [severity configuration](configuration-options.md#severity-level) options, the following additional precedence rules apply:</span></span>

- <span data-ttu-id="ba97d-150">Параметры серьезности, указанные в командной строке как параметры компилятора ( `/nowarn` или `/warnaserror` ), всегда переопределяют параметры [конфигурации серьезности](configuration-options.md#severity-level) , указанные в EditorConfig и глобальные файлы анализерконфиг.</span><span class="sxs-lookup"><span data-stu-id="ba97d-150">Severity options specified at the command line as compiler options (`/nowarn` or `/warnaserror`) always override [severity configuration](configuration-options.md#severity-level) options specified in EditorConfig and global AnalyzerConfig files.</span></span>

- <span data-ttu-id="ba97d-151">Параметры серьезности также можно указать с помощью [RuleSet](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) -файла.</span><span class="sxs-lookup"><span data-stu-id="ba97d-151">Severity options can also be specified with a [Ruleset](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) file.</span></span> <span data-ttu-id="ba97d-152">Однако файлы набора правил не рекомендуются в пользу EditorConfig глобальных файлов анализерконфиг.</span><span class="sxs-lookup"><span data-stu-id="ba97d-152">However, rulesets files are deprecated in favor of EditorConfig and global AnalyzerConfig files.</span></span> <span data-ttu-id="ba97d-153">Рекомендуется [преобразовать RuleSet Files в эквивалентный EditorConfig файл](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file).</span><span class="sxs-lookup"><span data-stu-id="ba97d-153">It's recommended that you [convert ruleset files to an equivalent EditorConfig file](/visualstudio/code-quality/use-roslyn-analyzers#convert-an-existing-ruleset-file-to-editorconfig-file).</span></span> <span data-ttu-id="ba97d-154">Приоритет для конфликтующих записей серьезности из файла набора правил и EditorConfig глобальных файлов анализерконфиг не _определен_.</span><span class="sxs-lookup"><span data-stu-id="ba97d-154">Precedence for conflicting severity entries from a ruleset file and EditorConfig or global AnalyzerConfig files is _undefined_.</span></span>

- <span data-ttu-id="ba97d-155">Сведения о правилах приоритета для связанных параметров серьезности с различными ключами, например при указании различных уровней серьезности для одного правила и категории, к которой относится правило, см. в разделе [Параметры конфигурации для анализа кода](configuration-options.md#precedence).</span><span class="sxs-lookup"><span data-stu-id="ba97d-155">For information about precedence rules for related severity options with different keys, for example, when different severities are specified for a single rule and for the category that rule falls under, see [Configuration options for code analysis](configuration-options.md#precedence).</span></span>

## <a name="see-also"></a><span data-ttu-id="ba97d-156">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ba97d-156">See also</span></span>

- [<span data-ttu-id="ba97d-157">EditorConfig Общая ошибка проектирования VS Анализерконфиг</span><span class="sxs-lookup"><span data-stu-id="ba97d-157">EditorConfig vs global AnalyzerConfig design issue</span></span>](https://github.com/dotnet/roslyn/issues/47707)
