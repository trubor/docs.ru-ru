---
title: Настройка правил анализа кода
description: Узнайте, как настроить правила анализа кода в файле конфигурации анализатора.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 4f7b392a2b066023fec75c5295bd94651654d645
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851794"
---
# <a name="configuration-options-for-code-analysis"></a><span data-ttu-id="dd63f-103">Параметры конфигурации для анализа кода</span><span class="sxs-lookup"><span data-stu-id="dd63f-103">Configuration options for code analysis</span></span>

<span data-ttu-id="dd63f-104">Правила анализа кода имеют различные параметры конфигурации.</span><span class="sxs-lookup"><span data-stu-id="dd63f-104">Code analysis rules have various configuration options.</span></span> <span data-ttu-id="dd63f-105">Эти параметры указываются в виде пар "ключ-значение" в [файле конфигурации анализатора](configuration-files.md) с использованием синтаксиса `<option key> = <option value>` .</span><span class="sxs-lookup"><span data-stu-id="dd63f-105">These options are specified as key-value pairs in an [analyzer configuration file](configuration-files.md) using the syntax `<option key> = <option value>`.</span></span>

<span data-ttu-id="dd63f-106">Наиболее распространенным параметром, который вы настраиваете, является [серьезность правила](#severity-level).</span><span class="sxs-lookup"><span data-stu-id="dd63f-106">The most common option you'll configure is a [rule's severity](#severity-level).</span></span> <span data-ttu-id="dd63f-107">Уровень серьезности можно настроить для всех правил анализатора, включая [Правила качества кода](quality-rules/index.md) и [правила стиля кода](style-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="dd63f-107">You can configure severity level for all analyzer rules, including [code quality rules](quality-rules/index.md) and [code style rules](style-rules/index.md).</span></span> <span data-ttu-id="dd63f-108">Например, чтобы включить правило как предупреждение, можно добавить следующую пару "ключ-значение" в EditorConfig файл.</span><span class="sxs-lookup"><span data-stu-id="dd63f-108">For example, to enable a rule as a warning, you can add the following key-value pair to an EditorConfig file.</span></span>

`dotnet_diagnostic.<rule ID>.severity = warning`

<span data-ttu-id="dd63f-109">Кроме того, можно настроить дополнительные параметры для настройки поведения правила.</span><span class="sxs-lookup"><span data-stu-id="dd63f-109">You can also configure additional options to customize rule behavior:</span></span>

- <span data-ttu-id="dd63f-110">Правила качества кода имеют [Дополнительные параметры](code-quality-rule-options.md) для настройки поведения, такие как имена методов, к которым должно применяться правило.</span><span class="sxs-lookup"><span data-stu-id="dd63f-110">Code quality rules have [additional options](code-quality-rule-options.md) to configure behavior, such as which method names a rule should apply to.</span></span>
- <span data-ttu-id="dd63f-111">Правила стиля кода имеют [Параметры пользовательского стиля кода](code-style-rule-options.md).</span><span class="sxs-lookup"><span data-stu-id="dd63f-111">Code style rules have [custom code style options](code-style-rule-options.md).</span></span>
- <span data-ttu-id="dd63f-112">Сторонние правила анализатора могут определять собственные параметры конфигурации, имена пользовательских ключей и форматы значений.</span><span class="sxs-lookup"><span data-stu-id="dd63f-112">Third party analyzer rules can define their own configuration options, with custom key names and value formats.</span></span>

<span data-ttu-id="dd63f-113">Ниже приведен синтаксис для настройки важности определенного правила в [файле конфигурации анализатора](configuration-files.md) .</span><span class="sxs-lookup"><span data-stu-id="dd63f-113">The syntax for configuring a specific rule's severity in an [analyzer configuration file](configuration-files.md) is as follows:</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a><span data-ttu-id="dd63f-114">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="dd63f-114">General options</span></span>

<span data-ttu-id="dd63f-115">Эти параметры применяются к анализу кода в целом.</span><span class="sxs-lookup"><span data-stu-id="dd63f-115">These options apply to code analysis as a whole.</span></span> <span data-ttu-id="dd63f-116">Они не могут применяться только к одному правилу или набору правил.</span><span class="sxs-lookup"><span data-stu-id="dd63f-116">They cannot be applied only to a single rule or set of rules.</span></span>

### <a name="exclude-generated-code"></a><span data-ttu-id="dd63f-117">Исключить созданный код</span><span class="sxs-lookup"><span data-stu-id="dd63f-117">Exclude generated code</span></span>

<span data-ttu-id="dd63f-118">Можно настроить дополнительные файлы и папки для обработки в виде созданного кода, добавив `generated_code = true | false` запись в [файл конфигурации](configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="dd63f-118">You can configure additional files and folders to be treated as generated code by adding a `generated_code = true | false` entry to your [configuration file](configuration-files.md).</span></span> <span data-ttu-id="dd63f-119">Предупреждения анализатора кода .NET не полезны для созданных файлов кода, таких как создаваемые конструктором файлы, которые пользователи не могут изменять для устранения нарушений.</span><span class="sxs-lookup"><span data-stu-id="dd63f-119">.NET code analyzer warnings aren't useful on generated code files, such as designer-generated files, which users can't edit to fix any violations.</span></span> <span data-ttu-id="dd63f-120">В большинстве случаев анализаторы кода пропускают созданные файлы кода и не сообщают о нарушениях этих файлов.</span><span class="sxs-lookup"><span data-stu-id="dd63f-120">In most cases, code analyzers skip generated code files and don't report violations on these files.</span></span>

<span data-ttu-id="dd63f-121">По умолчанию файлы с определенными расширениями или автоматически создаваемыми заголовками обрабатываются как сформированные файлы кода.</span><span class="sxs-lookup"><span data-stu-id="dd63f-121">By default, files with certain file extensions or auto-generated file headers are treated as generated code files.</span></span> <span data-ttu-id="dd63f-122">Например, имя файла, завершающее `.designer.cs` или `.generated.cs` , считается сгенерированным кодом.</span><span class="sxs-lookup"><span data-stu-id="dd63f-122">For example, a file name ending with `.designer.cs` or `.generated.cs` is considered generated code.</span></span> <span data-ttu-id="dd63f-123">Этот параметр конфигурации позволяет указать дополнительные шаблоны именования.</span><span class="sxs-lookup"><span data-stu-id="dd63f-123">This configuration option lets you specify additional naming patterns.</span></span>

<span data-ttu-id="dd63f-124">Например, чтобы обрабатывать все файлы, имена которых оканчиваются на `.MyGenerated.cs` созданный код, добавьте следующую запись:</span><span class="sxs-lookup"><span data-stu-id="dd63f-124">For example, to treat all files whose name ends with `.MyGenerated.cs` as generated code, add the following entry:</span></span>

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a><span data-ttu-id="dd63f-125">Параметры, зависящие от правила</span><span class="sxs-lookup"><span data-stu-id="dd63f-125">Rule-specific options</span></span>

<span data-ttu-id="dd63f-126">Параметры, относящиеся к конкретному правилу, могут применяться к одному правилу, набору правил или всем правилам.</span><span class="sxs-lookup"><span data-stu-id="dd63f-126">Rule-specific options can be applied to a single rule, a set of rules, or all rules.</span></span> <span data-ttu-id="dd63f-127">Параметры, зависящие от правила, включают:</span><span class="sxs-lookup"><span data-stu-id="dd63f-127">The rule-specific options include:</span></span>

- [<span data-ttu-id="dd63f-128">Уровень серьезности правила</span><span class="sxs-lookup"><span data-stu-id="dd63f-128">Rule severity level</span></span>](#severity-level)
- [<span data-ttu-id="dd63f-129">Параметры, относящиеся к правилам *качества кода*</span><span class="sxs-lookup"><span data-stu-id="dd63f-129">Options specific to *code-quality* rules</span></span>](code-quality-rule-options.md)

### <a name="severity-level"></a><span data-ttu-id="dd63f-130">Степень серьезности</span><span class="sxs-lookup"><span data-stu-id="dd63f-130">Severity level</span></span>

<span data-ttu-id="dd63f-131">В следующей таблице показаны различные уровни серьезности правил, которые можно настроить для всех правил анализатора, включая правила [качества кода](quality-rules/index.md) и [стиля кода](style-rules/index.md) .</span><span class="sxs-lookup"><span data-stu-id="dd63f-131">The following table shows the different rule severities that you can configure for all analyzer rules, including [code quality](quality-rules/index.md) and [code style](style-rules/index.md) rules.</span></span>

| <span data-ttu-id="dd63f-132">Статус</span><span class="sxs-lookup"><span data-stu-id="dd63f-132">Severity</span></span> | <span data-ttu-id="dd63f-133">Реакция на событие во время сборки</span><span class="sxs-lookup"><span data-stu-id="dd63f-133">Build-time behavior</span></span> |
|-|-|
| `error` | <span data-ttu-id="dd63f-134">Нарушения отображаются как *ошибки* сборки и вызывают сбой сборок.</span><span class="sxs-lookup"><span data-stu-id="dd63f-134">Violations appear as build *errors* and cause builds to fail.</span></span>|
| `warning` | <span data-ttu-id="dd63f-135">Нарушения отображаются как *предупреждения* сборки, но не вызывают сбои сборок (если только у вас не установлен параметр, чтобы обрабатывать предупреждения как ошибки).</span><span class="sxs-lookup"><span data-stu-id="dd63f-135">Violations appear as build *warnings* but do not cause builds to fail (unless you have an option set to treat warnings as errors).</span></span> |
| `suggestion` | <span data-ttu-id="dd63f-136">Нарушения отображаются как *сообщения* сборки и как предложения в интегрированной среде разработки Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dd63f-136">Violations appear as build *messages* and as suggestions in the Visual Studio IDE.</span></span> |
| `silent` | <span data-ttu-id="dd63f-137">Нарушения не видны пользователю.</span><span class="sxs-lookup"><span data-stu-id="dd63f-137">Violations aren't visible to the user.</span></span> |
| `none` | <span data-ttu-id="dd63f-138">Правило подавляется полностью.</span><span class="sxs-lookup"><span data-stu-id="dd63f-138">Rule is suppressed completely.</span></span> |
| `default` | <span data-ttu-id="dd63f-139">По умолчанию используется серьезность правила.</span><span class="sxs-lookup"><span data-stu-id="dd63f-139">The default severity of the rule is used.</span></span> |

> [!TIP]
> <span data-ttu-id="dd63f-140">Сведения о том, как на уровне серьезности правил в Visual Studio, см. в разделе [уровни серьезности](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span><span class="sxs-lookup"><span data-stu-id="dd63f-140">For information about how rule severities surface in Visual Studio, see [Severity levels](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span></span>

#### <a name="scope"></a><span data-ttu-id="dd63f-141">Область</span><span class="sxs-lookup"><span data-stu-id="dd63f-141">Scope</span></span>

<span data-ttu-id="dd63f-142">Чтобы задать серьезность правила для одного правила, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="dd63f-142">To set the rule severity for a single rule, use the following syntax.</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

<span data-ttu-id="dd63f-143">Чтобы задать серьезность правила по умолчанию для категории правил анализатора, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="dd63f-143">To set the default rule severity for a category of analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

<span data-ttu-id="dd63f-144">Чтобы задать серьезность правила по умолчанию для всех правил анализатора, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="dd63f-144">To set the default rule severity for all analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

#### <a name="precedence"></a><span data-ttu-id="dd63f-145">Приоритет</span><span class="sxs-lookup"><span data-stu-id="dd63f-145">Precedence</span></span>

<span data-ttu-id="dd63f-146">При наличии нескольких записей конфигурации серьезности, которые можно применить к одному и тому же ИДЕНТИФИКАТОРу правила, приоритет выбирается в следующем порядке:</span><span class="sxs-lookup"><span data-stu-id="dd63f-146">If you have multiple severity configuration entries that can be applied to the same rule ID, precedence is chosen in the following order:</span></span>

- <span data-ttu-id="dd63f-147">Запись для отдельного правила по ИДЕНТИФИКАТОРу имеет приоритет над записью для категории.</span><span class="sxs-lookup"><span data-stu-id="dd63f-147">An entry for an individual rule by ID takes precedence over an entry for a category.</span></span>
- <span data-ttu-id="dd63f-148">Запись для категории имеет приоритет над записью для всех правил анализатора.</span><span class="sxs-lookup"><span data-stu-id="dd63f-148">An entry for a category takes precedence over an entry for all analyzer rules.</span></span>

<span data-ttu-id="dd63f-149">Рассмотрим следующий пример, где [CA1822](/visualstudio/code-quality/ca1822) имеет категорию "производительность":</span><span class="sxs-lookup"><span data-stu-id="dd63f-149">Consider the following example, where [CA1822](/visualstudio/code-quality/ca1822) has the category "Performance":</span></span>

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

<span data-ttu-id="dd63f-150">В предыдущем примере все три записи серьезности применимы к CA1822.</span><span class="sxs-lookup"><span data-stu-id="dd63f-150">In the preceding example, all three severity entries are applicable to CA1822.</span></span> <span data-ttu-id="dd63f-151">Однако при использовании указанных правил приоритета первая запись на основе идентификатора правила переносится на следующие записи.</span><span class="sxs-lookup"><span data-stu-id="dd63f-151">However, using the specified precedence rules, the first rule ID-based entry wins over the next entries.</span></span> <span data-ttu-id="dd63f-152">В этом примере CA1822 будет иметь действительный уровень серьезности `error` .</span><span class="sxs-lookup"><span data-stu-id="dd63f-152">In this example, CA1822 will have an effective severity of `error`.</span></span> <span data-ttu-id="dd63f-153">Все остальные правила в категории "производительность" будут иметь серьезность `warning` .</span><span class="sxs-lookup"><span data-stu-id="dd63f-153">All other rules within the "Performance" category will have a severity of `warning`.</span></span>

<span data-ttu-id="dd63f-154">Сведения о приоритетах между файлами см. в [разделе приоритет статьи файлы конфигурации](configuration-files.md#precedence).</span><span class="sxs-lookup"><span data-stu-id="dd63f-154">For information about how inter-file precedence is decided, see the [Precedence section of the Configuration files article](configuration-files.md#precedence).</span></span>
