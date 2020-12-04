---
title: Настройка правил анализа кода
description: Узнайте, как настроить правила анализа кода в файле конфигурации анализатора.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: af2ebb74786f0ae884ffee4636765cae43fcb23f
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2020
ms.locfileid: "96593142"
---
# <a name="configuration-options-for-code-analysis"></a><span data-ttu-id="6d916-103">Параметры конфигурации для анализа кода</span><span class="sxs-lookup"><span data-stu-id="6d916-103">Configuration options for code analysis</span></span>

<span data-ttu-id="6d916-104">Правила анализа кода имеют различные параметры конфигурации.</span><span class="sxs-lookup"><span data-stu-id="6d916-104">Code analysis rules have various configuration options.</span></span> <span data-ttu-id="6d916-105">Эти параметры указываются в виде пар "ключ-значение" в [файле конфигурации анализатора](configuration-files.md) с использованием синтаксиса `<option key> = <option value>` .</span><span class="sxs-lookup"><span data-stu-id="6d916-105">These options are specified as key-value pairs in an [analyzer configuration file](configuration-files.md) using the syntax `<option key> = <option value>`.</span></span>

<span data-ttu-id="6d916-106">Наиболее распространенным параметром, который вы настраиваете, является серьезность правила.</span><span class="sxs-lookup"><span data-stu-id="6d916-106">The most common option you'll configure is a rule's severity.</span></span> <span data-ttu-id="6d916-107">Уровень серьезности можно настроить для всех правил анализатора, включая [Правила качества кода](quality-rules/index.md) и [правила стиля кода](style-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="6d916-107">You can configure severity level for all analyzer rules, including [code quality rules](quality-rules/index.md) and [code style rules](style-rules/index.md).</span></span>

<span data-ttu-id="6d916-108">Кроме того, можно настроить дополнительные параметры для настройки поведения правила.</span><span class="sxs-lookup"><span data-stu-id="6d916-108">You can also configure additional options to customize rule behavior:</span></span>

- <span data-ttu-id="6d916-109">Правила качества кода имеют [Дополнительные параметры](code-quality-rule-options.md) для настройки поведения, такие как имена методов, к которым должно применяться правило.</span><span class="sxs-lookup"><span data-stu-id="6d916-109">Code quality rules have [additional options](code-quality-rule-options.md) to configure behavior, such as which method names a rule should apply to.</span></span>
- <span data-ttu-id="6d916-110">Правила стиля кода имеют [Параметры пользовательского стиля кода](code-style-rule-options.md).</span><span class="sxs-lookup"><span data-stu-id="6d916-110">Code style rules have [custom code style options](code-style-rule-options.md).</span></span>
- <span data-ttu-id="6d916-111">Сторонние правила анализатора могут определять собственные параметры конфигурации, имена пользовательских ключей и форматы значений.</span><span class="sxs-lookup"><span data-stu-id="6d916-111">Third party analyzer rules can define their own configuration options, with custom key names and value formats.</span></span>

<span data-ttu-id="6d916-112">Ниже приведен синтаксис для настройки важности определенного правила в [файле конфигурации анализатора](configuration-files.md) .</span><span class="sxs-lookup"><span data-stu-id="6d916-112">The syntax for configuring a specific rule's severity in an [analyzer configuration file](configuration-files.md) is as follows:</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a><span data-ttu-id="6d916-113">Общие параметры</span><span class="sxs-lookup"><span data-stu-id="6d916-113">General options</span></span>

<span data-ttu-id="6d916-114">Эти параметры применяются к анализу кода в целом.</span><span class="sxs-lookup"><span data-stu-id="6d916-114">These options apply to code analysis as a whole.</span></span> <span data-ttu-id="6d916-115">Они не могут применяться только к одному правилу или набору правил.</span><span class="sxs-lookup"><span data-stu-id="6d916-115">They cannot be applied only to a single rule or set of rules.</span></span>

### <a name="exclude-generated-code"></a><span data-ttu-id="6d916-116">Исключить созданный код</span><span class="sxs-lookup"><span data-stu-id="6d916-116">Exclude generated code</span></span>

<span data-ttu-id="6d916-117">Можно настроить дополнительные файлы и папки для обработки в виде созданного кода, добавив `generated_code = true | false` запись в [файл конфигурации](configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="6d916-117">You can configure additional files and folders to be treated as generated code by adding a `generated_code = true | false` entry to your [configuration file](configuration-files.md).</span></span> <span data-ttu-id="6d916-118">Предупреждения анализатора кода .NET не полезны для созданных файлов кода, таких как создаваемые конструктором файлы, которые пользователи не могут изменять для устранения нарушений.</span><span class="sxs-lookup"><span data-stu-id="6d916-118">.NET code analyzer warnings aren't useful on generated code files, such as designer-generated files, which users can't edit to fix any violations.</span></span> <span data-ttu-id="6d916-119">В большинстве случаев анализаторы кода пропускают созданные файлы кода и не сообщают о нарушениях этих файлов.</span><span class="sxs-lookup"><span data-stu-id="6d916-119">In most cases, code analyzers skip generated code files and don't report violations on these files.</span></span>

<span data-ttu-id="6d916-120">По умолчанию файлы с определенными расширениями или автоматически создаваемыми заголовками обрабатываются как сформированные файлы кода.</span><span class="sxs-lookup"><span data-stu-id="6d916-120">By default, files with certain file extensions or auto-generated file headers are treated as generated code files.</span></span> <span data-ttu-id="6d916-121">Например, имя файла, завершающее `.designer.cs` или `.generated.cs` , считается сгенерированным кодом.</span><span class="sxs-lookup"><span data-stu-id="6d916-121">For example, a file name ending with `.designer.cs` or `.generated.cs` is considered generated code.</span></span> <span data-ttu-id="6d916-122">Этот параметр конфигурации позволяет указать дополнительные шаблоны именования.</span><span class="sxs-lookup"><span data-stu-id="6d916-122">This configuration option lets you specify additional naming patterns.</span></span>

<span data-ttu-id="6d916-123">Например, чтобы обрабатывать все файлы, имена которых оканчиваются на `.MyGenerated.cs` созданный код, добавьте следующую запись:</span><span class="sxs-lookup"><span data-stu-id="6d916-123">For example, to treat all files whose name ends with `.MyGenerated.cs` as generated code, add the following entry:</span></span>

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a><span data-ttu-id="6d916-124">Параметры, зависящие от правила</span><span class="sxs-lookup"><span data-stu-id="6d916-124">Rule-specific options</span></span>

<span data-ttu-id="6d916-125">Параметры, относящиеся к конкретному правилу, могут применяться к одному правилу, набору правил или всем правилам.</span><span class="sxs-lookup"><span data-stu-id="6d916-125">Rule-specific options can be applied to a single rule, a set of rules, or all rules.</span></span> <span data-ttu-id="6d916-126">Параметры, зависящие от правила, включают:</span><span class="sxs-lookup"><span data-stu-id="6d916-126">The rule-specific options include:</span></span>

- [<span data-ttu-id="6d916-127">Уровень серьезности правила</span><span class="sxs-lookup"><span data-stu-id="6d916-127">Rule severity level</span></span>](#severity-level)
- [<span data-ttu-id="6d916-128">Параметры, относящиеся к правилам *качества кода*</span><span class="sxs-lookup"><span data-stu-id="6d916-128">Options specific to *code-quality* rules</span></span>](code-quality-rule-options.md)

### <a name="severity-level"></a><span data-ttu-id="6d916-129">Степень серьезности</span><span class="sxs-lookup"><span data-stu-id="6d916-129">Severity level</span></span>

<span data-ttu-id="6d916-130">В следующей таблице показаны различные уровни серьезности правил, которые можно настроить для всех правил анализатора, включая правила [качества кода](quality-rules/index.md) и [стиля кода](style-rules/index.md) .</span><span class="sxs-lookup"><span data-stu-id="6d916-130">The following table shows the different rule severities that you can configure for all analyzer rules, including [code quality](quality-rules/index.md) and [code style](style-rules/index.md) rules.</span></span>

| <span data-ttu-id="6d916-131">Статус</span><span class="sxs-lookup"><span data-stu-id="6d916-131">Severity</span></span> | <span data-ttu-id="6d916-132">Реакция на событие во время сборки</span><span class="sxs-lookup"><span data-stu-id="6d916-132">Build-time behavior</span></span> |
|-|-|
| `error` | <span data-ttu-id="6d916-133">Нарушения отображаются как *ошибки* сборки и вызывают сбой сборок.</span><span class="sxs-lookup"><span data-stu-id="6d916-133">Violations appear as build *errors* and cause builds to fail.</span></span>|
| `warning` | <span data-ttu-id="6d916-134">Нарушения отображаются как *предупреждения* сборки, но не вызывают сбои сборок (если только у вас не установлен параметр, чтобы обрабатывать предупреждения как ошибки).</span><span class="sxs-lookup"><span data-stu-id="6d916-134">Violations appear as build *warnings* but do not cause builds to fail (unless you have an option set to treat warnings as errors).</span></span> |
| `suggestion` | <span data-ttu-id="6d916-135">Нарушения отображаются как *сообщения* сборки и как предложения в интегрированной среде разработки Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6d916-135">Violations appear as build *messages* and as suggestions in the Visual Studio IDE.</span></span> |
| `silent` | <span data-ttu-id="6d916-136">Нарушения не видны пользователю.</span><span class="sxs-lookup"><span data-stu-id="6d916-136">Violations aren't visible to the user.</span></span> |
| `none` | <span data-ttu-id="6d916-137">Правило подавляется полностью.</span><span class="sxs-lookup"><span data-stu-id="6d916-137">Rule is suppressed completely.</span></span> |
| `default` | <span data-ttu-id="6d916-138">По умолчанию используется серьезность правила.</span><span class="sxs-lookup"><span data-stu-id="6d916-138">The default severity of the rule is used.</span></span> |

> [!TIP]
> <span data-ttu-id="6d916-139">Сведения о том, как на уровне серьезности правил в Visual Studio, см. в разделе [уровни серьезности](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span><span class="sxs-lookup"><span data-stu-id="6d916-139">For information about how rule severities surface in Visual Studio, see [Severity levels](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span></span>

#### <a name="scope"></a><span data-ttu-id="6d916-140">Область</span><span class="sxs-lookup"><span data-stu-id="6d916-140">Scope</span></span>

<span data-ttu-id="6d916-141">Чтобы задать серьезность правила для одного правила, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="6d916-141">To set the rule severity for a single rule, use the following syntax.</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

<span data-ttu-id="6d916-142">Чтобы задать серьезность правила по умолчанию для категории правил анализатора, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="6d916-142">To set the default rule severity for a category of analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

<span data-ttu-id="6d916-143">Чтобы задать серьезность правила по умолчанию для всех правил анализатора, используйте следующий синтаксис.</span><span class="sxs-lookup"><span data-stu-id="6d916-143">To set the default rule severity for all analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

#### <a name="precedence"></a><span data-ttu-id="6d916-144">Приоритет</span><span class="sxs-lookup"><span data-stu-id="6d916-144">Precedence</span></span>

<span data-ttu-id="6d916-145">При наличии нескольких записей конфигурации серьезности, которые можно применить к одному и тому же ИДЕНТИФИКАТОРу правила, приоритет выбирается в следующем порядке:</span><span class="sxs-lookup"><span data-stu-id="6d916-145">If you have multiple severity configuration entries that can be applied to the same rule ID, precedence is chosen in the following order:</span></span>

- <span data-ttu-id="6d916-146">Запись для отдельного правила по ИДЕНТИФИКАТОРу имеет приоритет над записью для категории.</span><span class="sxs-lookup"><span data-stu-id="6d916-146">An entry for an individual rule by ID takes precedence over an entry for a category.</span></span>
- <span data-ttu-id="6d916-147">Запись для категории имеет приоритет над записью для всех правил анализатора.</span><span class="sxs-lookup"><span data-stu-id="6d916-147">An entry for a category takes precedence over an entry for all analyzer rules.</span></span>

<span data-ttu-id="6d916-148">Рассмотрим следующий пример, где [CA1822](/visualstudio/code-quality/ca1822) имеет категорию "производительность":</span><span class="sxs-lookup"><span data-stu-id="6d916-148">Consider the following example, where [CA1822](/visualstudio/code-quality/ca1822) has the category "Performance":</span></span>

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

<span data-ttu-id="6d916-149">В предыдущем примере все три записи серьезности применимы к CA1822.</span><span class="sxs-lookup"><span data-stu-id="6d916-149">In the preceding example, all three severity entries are applicable to CA1822.</span></span> <span data-ttu-id="6d916-150">Однако при использовании указанных правил приоритета первая запись на основе идентификатора правила переносится на следующие записи.</span><span class="sxs-lookup"><span data-stu-id="6d916-150">However, using the specified precedence rules, the first rule ID-based entry wins over the next entries.</span></span> <span data-ttu-id="6d916-151">В этом примере CA1822 будет иметь действительный уровень серьезности `error` .</span><span class="sxs-lookup"><span data-stu-id="6d916-151">In this example, CA1822 will have an effective severity of `error`.</span></span> <span data-ttu-id="6d916-152">Все остальные правила в категории "производительность" будут иметь серьезность `warning` .</span><span class="sxs-lookup"><span data-stu-id="6d916-152">All other rules within the "Performance" category will have a severity of `warning`.</span></span>

<span data-ttu-id="6d916-153">Сведения о приоритетах между файлами см. в [разделе приоритет статьи файлы конфигурации](configuration-files.md#precedence).</span><span class="sxs-lookup"><span data-stu-id="6d916-153">For information about how inter-file precedence is decided, see the [Precedence section of the Configuration files article](configuration-files.md#precedence).</span></span>
