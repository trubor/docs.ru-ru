---
title: Настройка правил анализа кода
description: Узнайте, как настроить правила анализа кода в файле конфигурации анализатора.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 8f76c9c86c202ef1bad23bffe8379b0b93a53f17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787725"
---
# <a name="configuration-options-for-code-analysis"></a><span data-ttu-id="b99e2-103">Параметры конфигурации для анализа кода</span><span class="sxs-lookup"><span data-stu-id="b99e2-103">Configuration options for code analysis</span></span>

<span data-ttu-id="b99e2-104">Правила анализа кода имеют различные параметры конфигурации.</span><span class="sxs-lookup"><span data-stu-id="b99e2-104">Code analysis rules have various configuration options.</span></span> <span data-ttu-id="b99e2-105">Эти параметры указываются в виде пар "ключ-значение" в [файле конфигурации анализатора](configuration-files.md) с использованием синтаксиса `<option key> = <option value>` .</span><span class="sxs-lookup"><span data-stu-id="b99e2-105">These options are specified as key-value pairs in an [analyzer configuration file](configuration-files.md) using the syntax `<option key> = <option value>`.</span></span>

<span data-ttu-id="b99e2-106">Наиболее распространенным параметром, который вы настраиваете, является [серьезность правила](#severity-level).</span><span class="sxs-lookup"><span data-stu-id="b99e2-106">The most common option you'll configure is a [rule's severity](#severity-level).</span></span> <span data-ttu-id="b99e2-107">Уровень серьезности можно настроить для всех правил анализатора, включая [Правила качества кода](quality-rules/index.md) и [правила стиля кода](style-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="b99e2-107">You can configure severity level for all analyzer rules, including [code quality rules](quality-rules/index.md) and [code style rules](style-rules/index.md).</span></span> <span data-ttu-id="b99e2-108">Например, чтобы включить правило как предупреждение, можно добавить следующую пару "ключ-значение" в EditorConfig файл.</span><span class="sxs-lookup"><span data-stu-id="b99e2-108">For example, to enable a rule as a warning, you can add the following key-value pair to an EditorConfig file.</span></span>

`dotnet_diagnostic.<rule ID>.severity = warning`

<span data-ttu-id="b99e2-109">Кроме того, можно настроить дополнительные параметры для настройки поведения правила.</span><span class="sxs-lookup"><span data-stu-id="b99e2-109">You can also configure additional options to customize rule behavior:</span></span>

- <span data-ttu-id="b99e2-110">Правила качества кода имеют [Дополнительные параметры](code-quality-rule-options.md) для настройки поведения, такие как имена методов, к которым должно применяться правило.</span><span class="sxs-lookup"><span data-stu-id="b99e2-110">Code quality rules have [additional options](code-quality-rule-options.md) to configure behavior, such as which method names a rule should apply to.</span></span>
- <span data-ttu-id="b99e2-111">Правила стиля кода имеют [Параметры пользовательского стиля кода](code-style-rule-options.md).</span><span class="sxs-lookup"><span data-stu-id="b99e2-111">Code style rules have [custom code style options](code-style-rule-options.md).</span></span>
- <span data-ttu-id="b99e2-112">Сторонние правила анализатора могут определять собственные параметры конфигурации, имена пользовательских ключей и форматы значений.</span><span class="sxs-lookup"><span data-stu-id="b99e2-112">Third party analyzer rules can define their own configuration options, with custom key names and value formats.</span></span>

<span data-ttu-id="b99e2-113">Ниже приведен синтаксис для настройки важности определенного правила в [файле конфигурации анализатора](configuration-files.md) .</span><span class="sxs-lookup"><span data-stu-id="b99e2-113">The syntax for configuring a specific rule's severity in an [analyzer configuration file](configuration-files.md) is as follows:</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a><span data-ttu-id="b99e2-114">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="b99e2-114">General options</span></span>

<span data-ttu-id="b99e2-115">Эти параметры применяются к анализу кода в целом.</span><span class="sxs-lookup"><span data-stu-id="b99e2-115">These options apply to code analysis as a whole.</span></span> <span data-ttu-id="b99e2-116">Они не могут применяться только к одному правилу или набору правил.</span><span class="sxs-lookup"><span data-stu-id="b99e2-116">They cannot be applied only to a single rule or set of rules.</span></span>

### <a name="exclude-generated-code"></a><span data-ttu-id="b99e2-117">Исключить созданный код</span><span class="sxs-lookup"><span data-stu-id="b99e2-117">Exclude generated code</span></span>

<span data-ttu-id="b99e2-118">Можно настроить дополнительные файлы и папки для обработки в виде созданного кода, добавив `generated_code = true | false` запись в [файл конфигурации](configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="b99e2-118">You can configure additional files and folders to be treated as generated code by adding a `generated_code = true | false` entry to your [configuration file](configuration-files.md).</span></span> <span data-ttu-id="b99e2-119">Предупреждения анализатора кода .NET не полезны для созданных файлов кода, таких как создаваемые конструктором файлы, которые пользователи не могут изменять для устранения нарушений.</span><span class="sxs-lookup"><span data-stu-id="b99e2-119">.NET code analyzer warnings aren't useful on generated code files, such as designer-generated files, which users can't edit to fix any violations.</span></span> <span data-ttu-id="b99e2-120">В большинстве случаев анализаторы кода пропускают созданные файлы кода и не сообщают о нарушениях этих файлов.</span><span class="sxs-lookup"><span data-stu-id="b99e2-120">In most cases, code analyzers skip generated code files and don't report violations on these files.</span></span>

<span data-ttu-id="b99e2-121">По умолчанию файлы с определенными расширениями или автоматически создаваемыми заголовками обрабатываются как сформированные файлы кода.</span><span class="sxs-lookup"><span data-stu-id="b99e2-121">By default, files with certain file extensions or auto-generated file headers are treated as generated code files.</span></span> <span data-ttu-id="b99e2-122">Например, имя файла, завершающее `.designer.cs` или `.generated.cs` , считается сгенерированным кодом.</span><span class="sxs-lookup"><span data-stu-id="b99e2-122">For example, a file name ending with `.designer.cs` or `.generated.cs` is considered generated code.</span></span> <span data-ttu-id="b99e2-123">Этот параметр конфигурации позволяет указать дополнительные шаблоны именования.</span><span class="sxs-lookup"><span data-stu-id="b99e2-123">This configuration option lets you specify additional naming patterns.</span></span>

<span data-ttu-id="b99e2-124">Например, чтобы обрабатывать все файлы, имена которых оканчиваются на `.MyGenerated.cs` созданный код, добавьте следующую запись:</span><span class="sxs-lookup"><span data-stu-id="b99e2-124">For example, to treat all files whose name ends with `.MyGenerated.cs` as generated code, add the following entry:</span></span>

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a><span data-ttu-id="b99e2-125">Параметры, зависящие от правила</span><span class="sxs-lookup"><span data-stu-id="b99e2-125">Rule-specific options</span></span>

<span data-ttu-id="b99e2-126">Параметры, относящиеся к конкретному правилу, могут применяться к одному правилу, набору правил или всем правилам.</span><span class="sxs-lookup"><span data-stu-id="b99e2-126">Rule-specific options can be applied to a single rule, a set of rules, or all rules.</span></span> <span data-ttu-id="b99e2-127">Параметры, зависящие от правила, включают:</span><span class="sxs-lookup"><span data-stu-id="b99e2-127">The rule-specific options include:</span></span>

- [<span data-ttu-id="b99e2-128">Уровень серьезности правила</span><span class="sxs-lookup"><span data-stu-id="b99e2-128">Rule severity level</span></span>](#severity-level)
- [<span data-ttu-id="b99e2-129">Параметры, относящиеся к правилам *качества кода*</span><span class="sxs-lookup"><span data-stu-id="b99e2-129">Options specific to *code-quality* rules</span></span>](code-quality-rule-options.md)

### <a name="severity-level"></a><span data-ttu-id="b99e2-130">Степень серьезности</span><span class="sxs-lookup"><span data-stu-id="b99e2-130">Severity level</span></span>

<span data-ttu-id="b99e2-131">В следующей таблице показаны различные уровни серьезности правил, которые можно настроить для всех правил анализатора, включая правила [качества кода](quality-rules/index.md) и [стиля кода](style-rules/index.md) .</span><span class="sxs-lookup"><span data-stu-id="b99e2-131">The following table shows the different rule severities that you can configure for all analyzer rules, including [code quality](quality-rules/index.md) and [code style](style-rules/index.md) rules.</span></span>

| <span data-ttu-id="b99e2-132">Severity</span><span class="sxs-lookup"><span data-stu-id="b99e2-132">Severity</span></span> | <span data-ttu-id="b99e2-133">Реакция на событие во время сборки</span><span class="sxs-lookup"><span data-stu-id="b99e2-133">Build-time behavior</span></span> |
|-|-|
| `error` | <span data-ttu-id="b99e2-134">Нарушения отображаются как *ошибки* сборки и вызывают сбой сборок.</span><span class="sxs-lookup"><span data-stu-id="b99e2-134">Violations appear as build *errors* and cause builds to fail.</span></span>|
| `warning` | <span data-ttu-id="b99e2-135">Нарушения отображаются как *предупреждения* сборки, но не вызывают сбои сборок (если только у вас не установлен параметр, чтобы обрабатывать предупреждения как ошибки).</span><span class="sxs-lookup"><span data-stu-id="b99e2-135">Violations appear as build *warnings* but do not cause builds to fail (unless you have an option set to treat warnings as errors).</span></span> |
| `suggestion` | <span data-ttu-id="b99e2-136">Нарушения отображаются как *сообщения* сборки и как предложения в интегрированной среде разработки Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b99e2-136">Violations appear as build *messages* and as suggestions in the Visual Studio IDE.</span></span> |
| `silent` | <span data-ttu-id="b99e2-137">Нарушения не видны пользователю.</span><span class="sxs-lookup"><span data-stu-id="b99e2-137">Violations aren't visible to the user.</span></span> |
| `none` | <span data-ttu-id="b99e2-138">Правило подавляется полностью.</span><span class="sxs-lookup"><span data-stu-id="b99e2-138">Rule is suppressed completely.</span></span> |
| `default` | <span data-ttu-id="b99e2-139">По умолчанию используется серьезность правила.</span><span class="sxs-lookup"><span data-stu-id="b99e2-139">The default severity of the rule is used.</span></span> |

> [!TIP]
> <span data-ttu-id="b99e2-140">Сведения о том, как на уровне серьезности правил в Visual Studio, см. в разделе [уровни серьезности](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span><span class="sxs-lookup"><span data-stu-id="b99e2-140">For information about how rule severities surface in Visual Studio, see [Severity levels](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span></span>

#### <a name="scope"></a><span data-ttu-id="b99e2-141">Область</span><span class="sxs-lookup"><span data-stu-id="b99e2-141">Scope</span></span>

<span data-ttu-id="b99e2-142">Чтобы задать серьезность правила для одного правила, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="b99e2-142">To set the rule severity for a single rule, use the following syntax.</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

<span data-ttu-id="b99e2-143">Чтобы задать серьезность правила по умолчанию для [категории правил](categories.md), используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="b99e2-143">To set the default rule severity for a [category of rules](categories.md), use the following syntax.</span></span> <span data-ttu-id="b99e2-144">Категория для каждого правила предоставляется на страницах ссылок на отдельные правила, например [CA1000](quality-rules/ca1000.md).</span><span class="sxs-lookup"><span data-stu-id="b99e2-144">The category for each rule is provided in the individual rule reference pages, for example, [CA1000](quality-rules/ca1000.md).</span></span>

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

<span data-ttu-id="b99e2-145">Чтобы задать серьезность правила по умолчанию для всех правил анализатора, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="b99e2-145">To set the default rule severity for all analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

#### <a name="precedence"></a><span data-ttu-id="b99e2-146">Приоритет</span><span class="sxs-lookup"><span data-stu-id="b99e2-146">Precedence</span></span>

<span data-ttu-id="b99e2-147">При наличии нескольких записей конфигурации серьезности, которые можно применить к одному и тому же ИДЕНТИФИКАТОРу правила, приоритет выбирается в следующем порядке:</span><span class="sxs-lookup"><span data-stu-id="b99e2-147">If you have multiple severity configuration entries that can be applied to the same rule ID, precedence is chosen in the following order:</span></span>

- <span data-ttu-id="b99e2-148">Запись для отдельного правила по ИДЕНТИФИКАТОРу имеет приоритет над записью для категории.</span><span class="sxs-lookup"><span data-stu-id="b99e2-148">An entry for an individual rule by ID takes precedence over an entry for a category.</span></span>
- <span data-ttu-id="b99e2-149">Запись для категории имеет приоритет над записью для всех правил анализатора.</span><span class="sxs-lookup"><span data-stu-id="b99e2-149">An entry for a category takes precedence over an entry for all analyzer rules.</span></span>

<span data-ttu-id="b99e2-150">Рассмотрим следующий пример, где [CA1822](/visualstudio/code-quality/ca1822) имеет категорию "производительность":</span><span class="sxs-lookup"><span data-stu-id="b99e2-150">Consider the following example, where [CA1822](/visualstudio/code-quality/ca1822) has the category "Performance":</span></span>

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

<span data-ttu-id="b99e2-151">В предыдущем примере все три записи серьезности применимы к CA1822.</span><span class="sxs-lookup"><span data-stu-id="b99e2-151">In the preceding example, all three severity entries are applicable to CA1822.</span></span> <span data-ttu-id="b99e2-152">Однако при использовании указанных правил приоритета первая запись на основе идентификатора правила переносится на следующие записи.</span><span class="sxs-lookup"><span data-stu-id="b99e2-152">However, using the specified precedence rules, the first rule ID-based entry wins over the next entries.</span></span> <span data-ttu-id="b99e2-153">В этом примере CA1822 будет иметь действительный уровень серьезности `error` .</span><span class="sxs-lookup"><span data-stu-id="b99e2-153">In this example, CA1822 will have an effective severity of `error`.</span></span> <span data-ttu-id="b99e2-154">Все остальные правила в категории "производительность" будут иметь серьезность `warning` .</span><span class="sxs-lookup"><span data-stu-id="b99e2-154">All other rules within the "Performance" category will have a severity of `warning`.</span></span>

<span data-ttu-id="b99e2-155">Сведения о приоритетах между файлами см. в [разделе приоритет статьи файлы конфигурации](configuration-files.md#precedence).</span><span class="sxs-lookup"><span data-stu-id="b99e2-155">For information about how inter-file precedence is decided, see the [Precedence section of the Configuration files article](configuration-files.md#precedence).</span></span>
