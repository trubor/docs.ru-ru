---
title: Настройка правил анализа кода
description: Сведения о том, как настроить правила анализа кода в файле конфигурации анализатора.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: c1992b32e5159e9bf7ae4d00b92a5baa7f7c1b8c
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876621"
---
# <a name="configuration-options-for-code-analysis"></a><span data-ttu-id="edb80-103">Параметры конфигурации для анализа кода</span><span class="sxs-lookup"><span data-stu-id="edb80-103">Configuration options for code analysis</span></span>

<span data-ttu-id="edb80-104">Для правил анализа кода доступно несколько параметров конфигурации.</span><span class="sxs-lookup"><span data-stu-id="edb80-104">Code analysis rules have various configuration options.</span></span> <span data-ttu-id="edb80-105">Эти параметры указываются в [файле конфигурации анализатора](configuration-files.md) в формате пар "ключ — значение" с использованием синтаксиса `<option key> = <option value>`.</span><span class="sxs-lookup"><span data-stu-id="edb80-105">These options are specified as key-value pairs in an [analyzer configuration file](configuration-files.md) using the syntax `<option key> = <option value>`.</span></span>

<span data-ttu-id="edb80-106">Чаще всего вам придется настраивать такой параметр, как [серьезность правила](#severity-level).</span><span class="sxs-lookup"><span data-stu-id="edb80-106">The most common option you'll configure is a [rule's severity](#severity-level).</span></span> <span data-ttu-id="edb80-107">Уровень серьезности можно настроить отдельно для всех правил анализатора, включая [правила качества кода](quality-rules/index.md) и [правила стиля кода](style-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="edb80-107">You can configure severity level for all analyzer rules, including [code quality rules](quality-rules/index.md) and [code style rules](style-rules/index.md).</span></span> <span data-ttu-id="edb80-108">Например, чтобы использовать правило как предупреждение, добавьте в файл EditorConfig следующую пару "ключ — значение".</span><span class="sxs-lookup"><span data-stu-id="edb80-108">For example, to enable a rule as a warning, you can add the following key-value pair to an EditorConfig file.</span></span>

`dotnet_diagnostic.<rule ID>.severity = warning`

<span data-ttu-id="edb80-109">Кроме того, можно настроить поведение правила с помощью дополнительных параметров:</span><span class="sxs-lookup"><span data-stu-id="edb80-109">You can also configure additional options to customize rule behavior:</span></span>

- <span data-ttu-id="edb80-110">Правила качества кода имеют [дополнительные параметры](code-quality-rule-options.md) для настройки поведения, например имен методов, к которым будет применяться правило.</span><span class="sxs-lookup"><span data-stu-id="edb80-110">Code quality rules have [additional options](code-quality-rule-options.md) to configure behavior, such as which method names a rule should apply to.</span></span>
- <span data-ttu-id="edb80-111">Правила стиля кода имеют [пользовательские параметры стиля кода](code-style-rule-options.md).</span><span class="sxs-lookup"><span data-stu-id="edb80-111">Code style rules have [custom code style options](code-style-rule-options.md).</span></span>
- <span data-ttu-id="edb80-112">Правила анализатора от сторонних поставщиков могут включать определения собственных параметров конфигурации с произвольными именами ключей и форматами значений.</span><span class="sxs-lookup"><span data-stu-id="edb80-112">Third party analyzer rules can define their own configuration options, with custom key names and value formats.</span></span>

<span data-ttu-id="edb80-113">Ниже приведен пример синтаксиса для настройки серьезности конкретного правила в [файле конфигурации анализатора](configuration-files.md):</span><span class="sxs-lookup"><span data-stu-id="edb80-113">The syntax for configuring a specific rule's severity in an [analyzer configuration file](configuration-files.md) is as follows:</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a><span data-ttu-id="edb80-114">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="edb80-114">General options</span></span>

<span data-ttu-id="edb80-115">Эти параметры применяются к анализу кода в целом.</span><span class="sxs-lookup"><span data-stu-id="edb80-115">These options apply to code analysis as a whole.</span></span> <span data-ttu-id="edb80-116">Вы не можете применять их только к одному правилу или набору правил.</span><span class="sxs-lookup"><span data-stu-id="edb80-116">They cannot be applied only to a single rule or set of rules.</span></span>

### <a name="exclude-generated-code"></a><span data-ttu-id="edb80-117">Исключение созданного кода</span><span class="sxs-lookup"><span data-stu-id="edb80-117">Exclude generated code</span></span>

<span data-ttu-id="edb80-118">Вы можете указать дополнительные файлы и папки, которые следует считать предназначенными для созданного кода, добавив запись `generated_code = true | false` в [файл конфигурации](configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="edb80-118">You can configure additional files and folders to be treated as generated code by adding a `generated_code = true | false` entry to your [configuration file](configuration-files.md).</span></span> <span data-ttu-id="edb80-119">Предупреждения анализатора кода .NET бесполезны для файлов созданного кода, например создаваемых конструктором файлов, так как пользователи не смогут изменить их для устранения обнаруженных нарушений.</span><span class="sxs-lookup"><span data-stu-id="edb80-119">.NET code analyzer warnings aren't useful on generated code files, such as designer-generated files, which users can't edit to fix any violations.</span></span> <span data-ttu-id="edb80-120">В большинстве случаев анализаторы кода пропускают файлы созданного кода и не сообщают о нарушениях в них.</span><span class="sxs-lookup"><span data-stu-id="edb80-120">In most cases, code analyzers skip generated code files and don't report violations on these files.</span></span>

<span data-ttu-id="edb80-121">По умолчанию файлы с определенными расширениями или автоматически создаваемыми заголовками обрабатываются как файлы созданного кода.</span><span class="sxs-lookup"><span data-stu-id="edb80-121">By default, files with certain file extensions or auto-generated file headers are treated as generated code files.</span></span> <span data-ttu-id="edb80-122">Например, файл с постфиксом `.designer.cs` или `.generated.cs` считается содержащим созданный код.</span><span class="sxs-lookup"><span data-stu-id="edb80-122">For example, a file name ending with `.designer.cs` or `.generated.cs` is considered generated code.</span></span> <span data-ttu-id="edb80-123">Этот параметр конфигурации позволяет указать дополнительные шаблоны именования.</span><span class="sxs-lookup"><span data-stu-id="edb80-123">This configuration option lets you specify additional naming patterns.</span></span>

<span data-ttu-id="edb80-124">Например, чтобы считать все файлы, имена которых оканчиваются на `.MyGenerated.cs`, содержащими созданный код, добавьте следующую запись:</span><span class="sxs-lookup"><span data-stu-id="edb80-124">For example, to treat all files whose name ends with `.MyGenerated.cs` as generated code, add the following entry:</span></span>

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a><span data-ttu-id="edb80-125">Параметры для конкретных правил</span><span class="sxs-lookup"><span data-stu-id="edb80-125">Rule-specific options</span></span>

<span data-ttu-id="edb80-126">Параметры для конкретных правил могут применяться к одному правилу, к набору правил или ко всем правилам.</span><span class="sxs-lookup"><span data-stu-id="edb80-126">Rule-specific options can be applied to a single rule, a set of rules, or all rules.</span></span> <span data-ttu-id="edb80-127">Доступны следующие параметры для конкретных правил:</span><span class="sxs-lookup"><span data-stu-id="edb80-127">The rule-specific options include:</span></span>

- [<span data-ttu-id="edb80-128">Уровень серьезности правила.</span><span class="sxs-lookup"><span data-stu-id="edb80-128">Rule severity level</span></span>](#severity-level)
- [<span data-ttu-id="edb80-129">Параметры для правил *качества кода*.</span><span class="sxs-lookup"><span data-stu-id="edb80-129">Options specific to *code-quality* rules</span></span>](code-quality-rule-options.md)

### <a name="severity-level"></a><span data-ttu-id="edb80-130">Степень серьезности</span><span class="sxs-lookup"><span data-stu-id="edb80-130">Severity level</span></span>

<span data-ttu-id="edb80-131">В следующей таблице представлены разные уровни серьезности правил, которые можно настроить для всех правил анализатора, включая правила [качества кода](quality-rules/index.md) и [стиля кода](style-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="edb80-131">The following table shows the different rule severities that you can configure for all analyzer rules, including [code quality](quality-rules/index.md) and [code style](style-rules/index.md) rules.</span></span>

| <span data-ttu-id="edb80-132">Значение конфигурации серьезности</span><span class="sxs-lookup"><span data-stu-id="edb80-132">Severity configuration value</span></span> | <span data-ttu-id="edb80-133">Реакция на событие во время сборки</span><span class="sxs-lookup"><span data-stu-id="edb80-133">Build-time behavior</span></span> |
|-|-|
| `error` | <span data-ttu-id="edb80-134">Нарушения отображаются как *ошибки* при сборке, которые аварийно завершают ее.</span><span class="sxs-lookup"><span data-stu-id="edb80-134">Violations appear as build *errors* and cause builds to fail.</span></span>|
| `warning` | <span data-ttu-id="edb80-135">Нарушения отображаются как *предупреждения* сборки, но не приводят к аварийному завершению, если вы не настроили параметр, требующий обрабатывать предупреждения как ошибки.</span><span class="sxs-lookup"><span data-stu-id="edb80-135">Violations appear as build *warnings* but do not cause builds to fail (unless you have an option set to treat warnings as errors).</span></span> |
| `suggestion` | <span data-ttu-id="edb80-136">Нарушения отображаются как *сообщения* сборки и предложения в интегрированной среде разработки Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="edb80-136">Violations appear as build *messages* and as suggestions in the Visual Studio IDE.</span></span> |
| `silent` | <span data-ttu-id="edb80-137">Нарушения не видны пользователю.</span><span class="sxs-lookup"><span data-stu-id="edb80-137">Violations aren't visible to the user.</span></span> |
| `none` | <span data-ttu-id="edb80-138">Правило подавляется полностью.</span><span class="sxs-lookup"><span data-stu-id="edb80-138">Rule is suppressed completely.</span></span> |
| `default` | <span data-ttu-id="edb80-139">Используется серьезность правила по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="edb80-139">The default severity of the rule is used.</span></span> <span data-ttu-id="edb80-140">Уровни серьезности по умолчанию для каждого выпуска .NET приведены в [репозитории roslyn-analyzers](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span><span class="sxs-lookup"><span data-stu-id="edb80-140">The default severities for each .NET release are listed in the [roslyn-analyzers repo](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span></span> <span data-ttu-id="edb80-141">В этой таблице "Disabled" соответствует `none`, "Hidden" соответствует `silent`, а "info" соответствует `suggestion`.</span><span class="sxs-lookup"><span data-stu-id="edb80-141">In that table, "Disabled" corresponds to `none`, "Hidden" corresponds to `silent`, and "Info" corresponds to `suggestion`.</span></span> |

> [!TIP]
> <span data-ttu-id="edb80-142">Сведения о том, как проявляются уровни серьезности правил в Visual Studio, см. в разделе об [уровнях серьезности](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span><span class="sxs-lookup"><span data-stu-id="edb80-142">For information about how rule severities surface in Visual Studio, see [Severity levels](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span></span>

#### <a name="scope"></a><span data-ttu-id="edb80-143">Область</span><span class="sxs-lookup"><span data-stu-id="edb80-143">Scope</span></span>

<span data-ttu-id="edb80-144">Чтобы задать серьезность правила для одного правила, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="edb80-144">To set the rule severity for a single rule, use the following syntax.</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

<span data-ttu-id="edb80-145">Чтобы задать серьезность по умолчанию для [категории правил](categories.md), используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="edb80-145">To set the default rule severity for a [category of rules](categories.md), use the following syntax.</span></span> <span data-ttu-id="edb80-146">Категория для каждого правила указана на странице справки соответствующего правила, например [CA1000](quality-rules/ca1000.md).</span><span class="sxs-lookup"><span data-stu-id="edb80-146">The category for each rule is provided in the individual rule reference pages, for example, [CA1000](quality-rules/ca1000.md).</span></span>

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

<span data-ttu-id="edb80-147">Чтобы задать серьезность правила по умолчанию для всех правил анализатора, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="edb80-147">To set the default rule severity for all analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

> [!IMPORTANT]
> <span data-ttu-id="edb80-148">Если вы задаете уровень серьезности одной записью для нескольких правил, то есть для *категории* правил или для *всех* правил, этот уровень серьезности применяется только к тем правилам, которые [включены по умолчанию](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span><span class="sxs-lookup"><span data-stu-id="edb80-148">When you configure the severity level for multiple rules with a single entry, either for a *category* of rules or for *all* rules, the severity only applies to rules that are [enabled by default](https://github.com/dotnet/roslyn-analyzers/blob/main/src/NetAnalyzers/Core/AnalyzerReleases.Shipped.md).</span></span> <span data-ttu-id="edb80-149">Чтобы применить его к правилам, отключенным по умолчанию, нужно выполнить одно из следующих действий:</span><span class="sxs-lookup"><span data-stu-id="edb80-149">To enable rules that are disabled by default, you must either:</span></span>
>
> - <span data-ttu-id="edb80-150">Добавьте явную запись конфигурации `dotnet_diagnostic.<rule ID>.severity = <severity>` для каждого правила.</span><span class="sxs-lookup"><span data-stu-id="edb80-150">Add an explicit `dotnet_diagnostic.<rule ID>.severity = <severity>` configuration entry for each rule.</span></span>
> - <span data-ttu-id="edb80-151">Включите *все* правила, задав для [\<AnalysisMode>](../../core/project-sdk/msbuild-props.md#analysismode) значение `AllEnabledByDefault`.</span><span class="sxs-lookup"><span data-stu-id="edb80-151">Enable *all* rules by setting [\<AnalysisMode>](../../core/project-sdk/msbuild-props.md#analysismode) to `AllEnabledByDefault`.</span></span>

#### <a name="precedence"></a><span data-ttu-id="edb80-152">Приоритет</span><span class="sxs-lookup"><span data-stu-id="edb80-152">Precedence</span></span>

<span data-ttu-id="edb80-153">Если к одному идентификатору правила могут применяться несколько записей конфигурации серьезности, приоритет определяется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="edb80-153">If you have multiple severity configuration entries that can be applied to the same rule ID, precedence is chosen in the following order:</span></span>

- <span data-ttu-id="edb80-154">Запись для конкретного идентификатора правила имеет приоритет над записью для категории.</span><span class="sxs-lookup"><span data-stu-id="edb80-154">An entry for an individual rule by ID takes precedence over an entry for a category.</span></span>
- <span data-ttu-id="edb80-155">Запись для категории имеет приоритет над записью для всех правил анализатора.</span><span class="sxs-lookup"><span data-stu-id="edb80-155">An entry for a category takes precedence over an entry for all analyzer rules.</span></span>

<span data-ttu-id="edb80-156">Рассмотрим следующий пример с правилом [CA1822](/visualstudio/code-quality/ca1822), которое имеет категорию Performance (Производительность):</span><span class="sxs-lookup"><span data-stu-id="edb80-156">Consider the following example, where [CA1822](/visualstudio/code-quality/ca1822) has the category "Performance":</span></span>

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

<span data-ttu-id="edb80-157">В примере выше к правилу CA1822 применимы все три записи серьезности.</span><span class="sxs-lookup"><span data-stu-id="edb80-157">In the preceding example, all three severity entries are applicable to CA1822.</span></span> <span data-ttu-id="edb80-158">Но применение указанных правил приоритета приводит к тому, что первая запись с идентификатором правила "опережает" все остальные записи.</span><span class="sxs-lookup"><span data-stu-id="edb80-158">However, using the specified precedence rules, the first rule ID-based entry wins over the next entries.</span></span> <span data-ttu-id="edb80-159">Следовательно, в этом примере для CA1822 будет применяться уровень серьезности `error`.</span><span class="sxs-lookup"><span data-stu-id="edb80-159">In this example, CA1822 will have an effective severity of `error`.</span></span> <span data-ttu-id="edb80-160">Все остальные правила в категории Performance (Производительность) будут иметь серьезность `warning`.</span><span class="sxs-lookup"><span data-stu-id="edb80-160">All other rules within the "Performance" category will have a severity of `warning`.</span></span>

<span data-ttu-id="edb80-161">Сведения о распределении приоритетов между файлами см. в [разделе "Приоритет" статьи о файлах конфигурации](configuration-files.md#precedence).</span><span class="sxs-lookup"><span data-stu-id="edb80-161">For information about how inter-file precedence is decided, see the [Precedence section of the Configuration files article](configuration-files.md#precedence).</span></span>
