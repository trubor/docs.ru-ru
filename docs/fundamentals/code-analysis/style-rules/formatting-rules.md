---
title: Правила форматирования для стиля кода
description: Сведения о правилах стиля кода для форматирования отступов, пробелов и новых строк.
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE0055
- formatting rules
helpviewer_keywords:
- IDE0055
- formatting code style rules [EditorConfig]
- formatting rules
- EditorConfig formatting conventions
ms.openlocfilehash: 866949692341f65a5b78c7dd5b8eec918873d3b7
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511805"
---
# <a name="formatting-rules"></a><span data-ttu-id="7ebc7-103">Правила форматирования</span><span class="sxs-lookup"><span data-stu-id="7ebc7-103">Formatting rules</span></span>

<span data-ttu-id="7ebc7-104">Правила форматирования влияют на то, как размещаются отступы, пробелы и новые строки вокруг конструкций языка программирования .NET.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-104">Formatting rules affect how indentation, spaces, and new lines are aligned around .NET programming language constructs.</span></span> <span data-ttu-id="7ebc7-105">Эти правила делятся на следующие категории:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-105">The rules fall into the following categories:</span></span>

- <span data-ttu-id="7ebc7-106">[Правила форматирования .NET](#net-formatting-rules) в равной мере применяются к C# и Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-106">[.NET formatting rules](#net-formatting-rules): Rules that apply to both C# and Visual Basic.</span></span> <span data-ttu-id="7ebc7-107">Имена параметров EditorConfig для этих правил начинаются с префикса `dotnet_`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-107">The EditorConfig option names for these rules start with `dotnet_` prefix.</span></span>
- <span data-ttu-id="7ebc7-108">[Правила форматирования C#](#c-formatting-rules) применяются только для языка C#.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-108">[C# formatting rules](#c-formatting-rules): Rules that are specific to C# language only.</span></span> <span data-ttu-id="7ebc7-109">Имена параметров EditorConfig для этих правил начинаются с префикса `csharp_`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-109">The EditorConfig option names for these rules start with `csharp_` prefix.</span></span>

## <a name="rule-id-ide0055-fix-formatting"></a><span data-ttu-id="7ebc7-110">Идентификатор правила: IDE0055 (исправление форматирования)</span><span class="sxs-lookup"><span data-stu-id="7ebc7-110">Rule ID: "IDE0055" (Fix formatting)</span></span>

<span data-ttu-id="7ebc7-111">Все параметры форматирования имеют идентификатор `IDE0055` и заголовок `Fix formatting`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-111">All formatting options have rule ID `IDE0055` and title `Fix formatting`.</span></span> <span data-ttu-id="7ebc7-112">Задайте серьезность нарушения правил форматирования в файле EditorConfig, используя следующую строку конфигурации.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-112">Set the severity of a formatting violation in an EditorConfig file using the following configuration line.</span></span>

```ini
dotnet_diagnostic.IDE0055.severity = <severity value>
```

<span data-ttu-id="7ebc7-113">Серьезность должна иметь значение `warning` или `error`, чтобы [принудительно применяться при сборке](../overview.md#code-style-analysis).</span><span class="sxs-lookup"><span data-stu-id="7ebc7-113">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="7ebc7-114">Все возможные значения серьезности перечислены на странице [об уровнях серьезности](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="7ebc7-114">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="option-format"></a><span data-ttu-id="7ebc7-115">Формат параметра</span><span class="sxs-lookup"><span data-stu-id="7ebc7-115">Option format</span></span>

<span data-ttu-id="7ebc7-116">Параметры для правил форматирования можно указывать в файле EditorConfig в следующем формате:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-116">Options for formatting rules can be specified in an EditorConfig file with the following format:</span></span>

`rule_name = value`

<span data-ttu-id="7ebc7-117">Для большинства правил вы указываете значение `true` (предпочитать этот стиль) или `value` (не предпочитать этот стиль) для `false`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-117">For many rules, you specify either `true` (prefer this style) or `false` (do not prefer this style) for `value`.</span></span> <span data-ttu-id="7ebc7-118">Для нескольких правил указываются другие значения, например `flush_left` или `before_and_after`, которые описывают порядок применения этих правил.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-118">For other rules, you specify a value such as `flush_left` or `before_and_after` to describe when and where to apply the rule.</span></span> <span data-ttu-id="7ebc7-119">Уровень серьезности указывать не нужно.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-119">You don't specify a severity.</span></span>

## <a name="net-formatting-rules"></a><span data-ttu-id="7ebc7-120">Правила форматирования .NET</span><span class="sxs-lookup"><span data-stu-id="7ebc7-120">.NET formatting rules</span></span>

<span data-ttu-id="7ebc7-121">Правила форматирования в этом разделе в равной мере применяются к C# и Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-121">The formatting rules in this section apply to both C# and Visual Basic.</span></span>

- [<span data-ttu-id="7ebc7-122">Управление директивами using</span><span class="sxs-lookup"><span data-stu-id="7ebc7-122">Organize usings</span></span>](#organize-using-directives)
  - <span data-ttu-id="7ebc7-123">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="7ebc7-123">dotnet_sort_system_directives_first</span></span>
  - <span data-ttu-id="7ebc7-124">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="7ebc7-124">dotnet_separate_import_directive_groups</span></span>

### <a name="organize-using-directives"></a><span data-ttu-id="7ebc7-125">Оптимизация директив Using</span><span class="sxs-lookup"><span data-stu-id="7ebc7-125">Organize using directives</span></span>

<span data-ttu-id="7ebc7-126">Эти правила форматирования относятся к сортировке и отображению директив `using` и инструкций `Imports`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-126">These formatting rules concern the sorting and display of `using` directives and `Imports` statements.</span></span>

<span data-ttu-id="7ebc7-127">Пример файла *EDITORCONFIG*:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-127">Example *.editorconfig* file:</span></span>

```ini
# .NET formatting rules
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a><span data-ttu-id="7ebc7-128">dotnet\_sort\_system\_directives_first</span><span class="sxs-lookup"><span data-stu-id="7ebc7-128">dotnet\_sort\_system\_directives_first</span></span>

|<span data-ttu-id="7ebc7-129">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-129">Property</span></span>|<span data-ttu-id="7ebc7-130">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-130">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-131">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-131">**Option name**</span></span> | <span data-ttu-id="7ebc7-132">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="7ebc7-132">dotnet_sort_system_directives_first</span></span> |
| <span data-ttu-id="7ebc7-133">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-133">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-134">C# и Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ebc7-134">C# and Visual Basic</span></span> |
| <span data-ttu-id="7ebc7-135">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-135">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-136">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-136">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-137">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-137">**Option values**</span></span> | <span data-ttu-id="7ebc7-138">`true` — сортировать директивы `System.*` `using` в алфавитном порядке, располагая их перед всеми остальными директивами using.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-138">`true` - Sort `System.*` `using` directives alphabetically, and place them before other using directives.</span></span><br /><br /><span data-ttu-id="7ebc7-139">`false` — не размещать директивы `System.*` `using` перед другими директивами `using`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-139">`false` - Do not place `System.*` `using` directives before other `using` directives.</span></span> |

<span data-ttu-id="7ebc7-140">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-140">Code examples:</span></span>

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

#### <a name="dotnet_separate_import_directive_groups"></a><span data-ttu-id="7ebc7-141">dotnet\_separate\_import\_directive\_groups</span><span class="sxs-lookup"><span data-stu-id="7ebc7-141">dotnet\_separate\_import\_directive\_groups</span></span>

|<span data-ttu-id="7ebc7-142">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-142">Property</span></span>|<span data-ttu-id="7ebc7-143">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-143">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-144">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-144">**Option name**</span></span> | <span data-ttu-id="7ebc7-145">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="7ebc7-145">dotnet_separate_import_directive_groups</span></span> |
| <span data-ttu-id="7ebc7-146">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-146">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-147">C# и Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ebc7-147">C# and Visual Basic</span></span> |
| <span data-ttu-id="7ebc7-148">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-148">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-149">Visual Studio 2017 версии 15.5</span><span class="sxs-lookup"><span data-stu-id="7ebc7-149">Visual Studio 2017 version 15.5</span></span> |
| <span data-ttu-id="7ebc7-150">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-150">**Option values**</span></span> | <span data-ttu-id="7ebc7-151">`true` — поместить пустую строку между группами директив `using`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-151">`true` - Place a blank line between `using` directive groups.</span></span><br /><br /><span data-ttu-id="7ebc7-152">`false` — не помещать пустую строку между группами директив `using`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-152">`false` - Do not place a blank line between `using` directive groups.</span></span> |

<span data-ttu-id="7ebc7-153">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-153">Code examples:</span></span>

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-rules"></a><span data-ttu-id="7ebc7-154">Правила форматирования C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-154">C# formatting rules</span></span>

<span data-ttu-id="7ebc7-155">Правила форматирования в этом разделе относятся только к коду C#.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-155">The formatting rules in this section apply only to C# code.</span></span>

- [<span data-ttu-id="7ebc7-156">Параметры перевода строки</span><span class="sxs-lookup"><span data-stu-id="7ebc7-156">Newline options</span></span>](#new-line-options)
  - <span data-ttu-id="7ebc7-157">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="7ebc7-157">csharp_new_line_before_open_brace</span></span>
  - <span data-ttu-id="7ebc7-158">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="7ebc7-158">csharp_new_line_before_else</span></span>
  - <span data-ttu-id="7ebc7-159">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="7ebc7-159">csharp_new_line_before_catch</span></span>
  - <span data-ttu-id="7ebc7-160">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="7ebc7-160">csharp_new_line_before_finally</span></span>
  - <span data-ttu-id="7ebc7-161">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="7ebc7-161">csharp_new_line_before_members_in_object_initializers</span></span>
  - <span data-ttu-id="7ebc7-162">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="7ebc7-162">csharp_new_line_before_members_in_anonymous_types</span></span>
  - <span data-ttu-id="7ebc7-163">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-163">csharp_new_line_between_query_expression_clauses</span></span>
- [<span data-ttu-id="7ebc7-164">Параметры отступа</span><span class="sxs-lookup"><span data-stu-id="7ebc7-164">Indentation options</span></span>](#indentation-options)
  - <span data-ttu-id="7ebc7-165">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="7ebc7-165">csharp_indent_case_contents</span></span>
  - <span data-ttu-id="7ebc7-166">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="7ebc7-166">csharp_indent_switch_labels</span></span>
  - <span data-ttu-id="7ebc7-167">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="7ebc7-167">csharp_indent_labels</span></span>
  - <span data-ttu-id="7ebc7-168">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="7ebc7-168">csharp_indent_block_contents</span></span>
  - <span data-ttu-id="7ebc7-169">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="7ebc7-169">csharp_indent_braces</span></span>
  - <span data-ttu-id="7ebc7-170">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="7ebc7-170">csharp_indent_case_contents_when_block</span></span>
- [<span data-ttu-id="7ebc7-171">Параметры интервалов</span><span class="sxs-lookup"><span data-stu-id="7ebc7-171">Spacing options</span></span>](#spacing-options)
  - <span data-ttu-id="7ebc7-172">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="7ebc7-172">csharp_space_after_cast</span></span>
  - <span data-ttu-id="7ebc7-173">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="7ebc7-173">csharp_space_after_keywords_in_control_flow_statements</span></span>
  - <span data-ttu-id="7ebc7-174">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-174">csharp_space_between_parentheses</span></span>
  - <span data-ttu-id="7ebc7-175">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="7ebc7-175">csharp_space_before_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="7ebc7-176">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="7ebc7-176">csharp_space_after_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="7ebc7-177">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="7ebc7-177">csharp_space_around_binary_operators</span></span>
  - <span data-ttu-id="7ebc7-178">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-178">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>
  - <span data-ttu-id="7ebc7-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="7ebc7-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="7ebc7-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>
  - <span data-ttu-id="7ebc7-181">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-181">csharp_space_between_method_call_parameter_list_parentheses</span></span>
  - <span data-ttu-id="7ebc7-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="7ebc7-183">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="7ebc7-183">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>
  - <span data-ttu-id="7ebc7-184">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="7ebc7-184">csharp_space_after_comma</span></span>
  - <span data-ttu-id="7ebc7-185">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="7ebc7-185">csharp_space_before_comma</span></span>
  - <span data-ttu-id="7ebc7-186">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="7ebc7-186">csharp_space_after_dot</span></span>
  - <span data-ttu-id="7ebc7-187">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="7ebc7-187">csharp_space_before_dot</span></span>
  - <span data-ttu-id="7ebc7-188">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="7ebc7-188">csharp_space_after_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="7ebc7-189">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="7ebc7-189">csharp_space_before_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="7ebc7-190">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="7ebc7-190">csharp_space_around_declaration_statements</span></span>
  - <span data-ttu-id="7ebc7-191">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="7ebc7-191">csharp_space_before_open_square_brackets</span></span>
  - <span data-ttu-id="7ebc7-192">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="7ebc7-192">csharp_space_between_empty_square_brackets</span></span>
  - <span data-ttu-id="7ebc7-193">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="7ebc7-193">csharp_space_between_square_brackets</span></span>
- [<span data-ttu-id="7ebc7-194">Параметры переноса</span><span class="sxs-lookup"><span data-stu-id="7ebc7-194">Wrap options</span></span>](#wrap-options)
  - <span data-ttu-id="7ebc7-195">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="7ebc7-195">csharp_preserve_single_line_statements</span></span>
  - <span data-ttu-id="7ebc7-196">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="7ebc7-196">csharp_preserve_single_line_blocks</span></span>
- [<span data-ttu-id="7ebc7-197">Параметры директивы using</span><span class="sxs-lookup"><span data-stu-id="7ebc7-197">Using directive options</span></span>](#using-directive-options)
  - <span data-ttu-id="7ebc7-198">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="7ebc7-198">csharp_using_directive_placement</span></span>

### <a name="new-line-options"></a><span data-ttu-id="7ebc7-199">Параметры новой строки</span><span class="sxs-lookup"><span data-stu-id="7ebc7-199">New-line options</span></span>

<span data-ttu-id="7ebc7-200">Эти правила форматирования относятся использованию новых строк для форматирования кода.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-200">These formatting rules concern the use of new lines to format code.</span></span>

<span data-ttu-id="7ebc7-201">Пример файла *EDITORCONFIG*:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-201">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="csharp_new_line_before_open_brace"></a><span data-ttu-id="7ebc7-202">csharp\_new\_line\_before\_open_brace</span><span class="sxs-lookup"><span data-stu-id="7ebc7-202">csharp\_new\_line\_before\_open_brace</span></span>

<span data-ttu-id="7ebc7-203">Это правило определяет, следует ли располагать открывающую фигурную скобку `{` одной строке с предшествующим кодом или на новой строке.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-203">This rule concerns whether an open brace `{` should be placed on the same line as the preceding code, or on a new line.</span></span> <span data-ttu-id="7ebc7-204">Для этого правила укажите **all**, **none** либо один или несколько элементов кода, таких как **methods** или **properties**, для которых следует применять это правило.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-204">For this rule, you specify **all**, **none**, or one or more code elements such as **methods** or **properties**, to define when this rule should be applied.</span></span> <span data-ttu-id="7ebc7-205">Если вы указываете несколько элементов кода, разделяйте их запятыми (,).</span><span class="sxs-lookup"><span data-stu-id="7ebc7-205">To specify multiple code elements, separate them with a comma (,).</span></span>

|<span data-ttu-id="7ebc7-206">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-206">Property</span></span>|<span data-ttu-id="7ebc7-207">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-207">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-208">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-208">**Option name**</span></span> | <span data-ttu-id="7ebc7-209">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="7ebc7-209">csharp_new_line_before_open_brace</span></span> |
| <span data-ttu-id="7ebc7-210">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-210">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-211">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-211">C#</span></span> |
| <span data-ttu-id="7ebc7-212">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-212">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-213">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-213">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-214">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-214">**Option values**</span></span> | <span data-ttu-id="7ebc7-215">`all` — требовать, чтобы фигурные скобки для всех выражений размещались в новой строке (стиль Олмана).</span><span class="sxs-lookup"><span data-stu-id="7ebc7-215">`all` - Require braces to be on a new line for all expressions ("Allman" style).</span></span><br /><br /><span data-ttu-id="7ebc7-216">`none` — требовать, чтобы фигурные скобки для всех выражений размещались в строке выражения (стиль Кернигана и Ритчи).</span><span class="sxs-lookup"><span data-stu-id="7ebc7-216">`none` - Require braces to be on the same line for all expressions ("K&R").</span></span><br /><br /><span data-ttu-id="7ebc7-217">`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` — требовать, чтобы фигурные скобки для указанного элемента кода размещались в новой строке (стиль Олмана).</span><span class="sxs-lookup"><span data-stu-id="7ebc7-217">`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` - Require braces to be on a new line for the specified code element ("Allman" style).</span></span> |

<span data-ttu-id="7ebc7-218">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-218">Code examples:</span></span>

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="csharp_new_line_before_else"></a><span data-ttu-id="7ebc7-219">csharp\_new\_line\_before_else</span><span class="sxs-lookup"><span data-stu-id="7ebc7-219">csharp\_new\_line\_before_else</span></span>

|<span data-ttu-id="7ebc7-220">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-220">Property</span></span>|<span data-ttu-id="7ebc7-221">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-221">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-222">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-222">**Option name**</span></span> | <span data-ttu-id="7ebc7-223">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="7ebc7-223">csharp_new_line_before_else</span></span> |
| <span data-ttu-id="7ebc7-224">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-224">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-225">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-225">C#</span></span> |
| <span data-ttu-id="7ebc7-226">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-226">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-227">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-227">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-228">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-228">**Option values**</span></span> | <span data-ttu-id="7ebc7-229">`true` — размещать инструкции `else` в новой строке.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-229">`true` - Place `else` statements on a new line.</span></span><br /><br /><span data-ttu-id="7ebc7-230">`false` — размещать инструкции `else` в той же строке.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-230">`false` - Place `else` statements on the same line.</span></span> |

<span data-ttu-id="7ebc7-231">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-231">Code examples:</span></span>

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="csharp_new_line_before_catch"></a><span data-ttu-id="7ebc7-232">csharp\_new\_line\_before_catch</span><span class="sxs-lookup"><span data-stu-id="7ebc7-232">csharp\_new\_line\_before_catch</span></span>

|<span data-ttu-id="7ebc7-233">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-233">Property</span></span>|<span data-ttu-id="7ebc7-234">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-234">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-235">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-235">**Option name**</span></span> | <span data-ttu-id="7ebc7-236">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="7ebc7-236">csharp_new_line_before_catch</span></span> |
| <span data-ttu-id="7ebc7-237">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-237">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-238">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-238">C#</span></span> |
| <span data-ttu-id="7ebc7-239">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-239">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-240">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-240">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-241">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-241">**Option values**</span></span> | <span data-ttu-id="7ebc7-242">`true` — размещать инструкции `catch` в новой строке.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-242">`true` - Place `catch` statements on a new line.</span></span><br /><br /><span data-ttu-id="7ebc7-243">`false` — размещать инструкции `catch` в той же строке.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-243">`false` - Place `catch` statements on the same line.</span></span> |

<span data-ttu-id="7ebc7-244">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-244">Code examples:</span></span>

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="csharp_new_line_before_finally"></a><span data-ttu-id="7ebc7-245">csharp\_new\_line\_before_finally</span><span class="sxs-lookup"><span data-stu-id="7ebc7-245">csharp\_new\_line\_before_finally</span></span>

|<span data-ttu-id="7ebc7-246">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-246">Property</span></span>|<span data-ttu-id="7ebc7-247">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-247">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-248">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-248">**Option name**</span></span> | <span data-ttu-id="7ebc7-249">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="7ebc7-249">csharp_new_line_before_finally</span></span> |
| <span data-ttu-id="7ebc7-250">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-250">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-251">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-251">C#</span></span> |
| <span data-ttu-id="7ebc7-252">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-252">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-253">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-253">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-254">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-254">**Option values**</span></span> | <span data-ttu-id="7ebc7-255">`true` — требовать, чтобы инструкции `finally` размещались в новой строке после закрывающей фигурной скобки.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-255">`true` - Require `finally` statements to be on a new line after the closing brace.</span></span><br /><br /><span data-ttu-id="7ebc7-256">`false` — требовать, чтобы инструкции `finally` размещались в той же строке после закрывающей фигурной скобки.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-256">`false` - Require `finally` statements to be on the same line as the closing brace.</span></span> |

<span data-ttu-id="7ebc7-257">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-257">Code examples:</span></span>

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="csharp_new_line_before_members_in_object_initializers"></a><span data-ttu-id="7ebc7-258">csharp\_new\_line\_before\_members\_in\_object_initializers</span><span class="sxs-lookup"><span data-stu-id="7ebc7-258">csharp\_new\_line\_before\_members\_in\_object_initializers</span></span>

|<span data-ttu-id="7ebc7-259">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-259">Property</span></span>|<span data-ttu-id="7ebc7-260">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-260">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-261">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-261">**Option name**</span></span> | <span data-ttu-id="7ebc7-262">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="7ebc7-262">csharp_new_line_before_members_in_object_initializers</span></span> |
| <span data-ttu-id="7ebc7-263">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-263">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-264">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-264">C#</span></span> |
| <span data-ttu-id="7ebc7-265">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-265">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-266">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-266">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-267">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-267">**Option values**</span></span> | <span data-ttu-id="7ebc7-268">`true` — требовать, чтобы элементы инициализаторов объектов размещались в разных строках.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-268">`true` - Require members of object initializers to be on separate lines</span></span><br /><br /><span data-ttu-id="7ebc7-269">`false` — требовать, чтобы элементы инициализаторов объектов размещались в той же строке.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-269">`false` - Require members of object initializers to be on the same line</span></span> |

<span data-ttu-id="7ebc7-270">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-270">Code examples:</span></span>

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a><span data-ttu-id="7ebc7-271">csharp\_new\_line\_before\_members\_in\_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="7ebc7-271">csharp\_new\_line\_before\_members\_in\_anonymous_types</span></span>

|<span data-ttu-id="7ebc7-272">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-272">Property</span></span>|<span data-ttu-id="7ebc7-273">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-273">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-274">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-274">**Option name**</span></span> | <span data-ttu-id="7ebc7-275">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="7ebc7-275">csharp_new_line_before_members_in_anonymous_types</span></span> |
| <span data-ttu-id="7ebc7-276">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-276">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-277">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-277">C#</span></span> |
| <span data-ttu-id="7ebc7-278">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-278">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-279">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-279">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-280">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-280">**Option values**</span></span> | <span data-ttu-id="7ebc7-281">`true` — требовать, чтобы элементы анонимных типов размещались в разных строках.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-281">`true` - Require members of anonymous types to be on separate lines</span></span><br /><br /><span data-ttu-id="7ebc7-282">`false` — требовать, чтобы элементы анонимных типов размещались в той же строке.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-282">`false` - Require members of anonymous types to be on the same line</span></span> |

<span data-ttu-id="7ebc7-283">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-283">Code examples:</span></span>

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_between_query_expression_clauses"></a><span data-ttu-id="7ebc7-284">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-284">csharp_new_line_between_query_expression_clauses</span></span>

|<span data-ttu-id="7ebc7-285">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-285">Property</span></span>|<span data-ttu-id="7ebc7-286">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-286">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-287">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-287">**Option name**</span></span> | <span data-ttu-id="7ebc7-288">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-288">csharp_new_line_between_query_expression_clauses</span></span> |
| <span data-ttu-id="7ebc7-289">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-289">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-290">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-290">C#</span></span> |
| <span data-ttu-id="7ebc7-291">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-291">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-292">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-292">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-293">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-293">**Option values**</span></span> | <span data-ttu-id="7ebc7-294">`true` — требовать, чтобы элементы в предложениях выражений запросов размещались в отдельных строках.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-294">`true` - Require elements of query expression clauses to be on separate lines</span></span><br /><br /><span data-ttu-id="7ebc7-295">`false` — требовать, чтобы элементы в предложениях выражений запросов размещались в той же строке.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-295">`false` - Require elements of query expression clauses to be on the same line</span></span> |

<span data-ttu-id="7ebc7-296">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-296">Code examples:</span></span>

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a><span data-ttu-id="7ebc7-297">Параметры отступа</span><span class="sxs-lookup"><span data-stu-id="7ebc7-297">Indentation options</span></span>

<span data-ttu-id="7ebc7-298">Эти правила форматирования относятся к использованию отступа для форматирования кода.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-298">These formatting rules concern the use of indentation to format code.</span></span>

<span data-ttu-id="7ebc7-299">Пример файла *EDITORCONFIG*:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-299">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### <a name="csharp_indent_case_contents"></a><span data-ttu-id="7ebc7-300">csharp\_indent\_case_contents</span><span class="sxs-lookup"><span data-stu-id="7ebc7-300">csharp\_indent\_case_contents</span></span>

|<span data-ttu-id="7ebc7-301">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-301">Property</span></span>|<span data-ttu-id="7ebc7-302">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-302">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-303">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-303">**Option name**</span></span> | <span data-ttu-id="7ebc7-304">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="7ebc7-304">csharp_indent_case_contents</span></span> |
| <span data-ttu-id="7ebc7-305">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-305">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-306">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-306">C#</span></span> |
| <span data-ttu-id="7ebc7-307">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-307">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-308">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-308">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-309">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-309">**Option values**</span></span> | <span data-ttu-id="7ebc7-310">`true` — отступ в конструкции `switch` case</span><span class="sxs-lookup"><span data-stu-id="7ebc7-310">`true` - Indent `switch` case contents</span></span><br /><br /><span data-ttu-id="7ebc7-311">`false` — не использовать отступ в конструкции `switch` case</span><span class="sxs-lookup"><span data-stu-id="7ebc7-311">`false` - Do not indent `switch` case contents</span></span> |

- <span data-ttu-id="7ebc7-312">Когда для этого правила задано значение **true**, i.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-312">When this rule is set to **true**, i.</span></span>
- <span data-ttu-id="7ebc7-313">Когда для этого правила задано значение **false**, d.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-313">When this rule is set to **false**, d.</span></span>

<span data-ttu-id="7ebc7-314">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-314">Code examples:</span></span>

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_switch_labels"></a><span data-ttu-id="7ebc7-315">csharp\_indent\_switch_labels</span><span class="sxs-lookup"><span data-stu-id="7ebc7-315">csharp\_indent\_switch_labels</span></span>

|<span data-ttu-id="7ebc7-316">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-316">Property</span></span>|<span data-ttu-id="7ebc7-317">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-317">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-318">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-318">**Option name**</span></span> | <span data-ttu-id="7ebc7-319">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="7ebc7-319">csharp_indent_switch_labels</span></span> |
| <span data-ttu-id="7ebc7-320">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-320">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-321">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-321">C#</span></span> |
| <span data-ttu-id="7ebc7-322">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-322">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-323">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-323">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-324">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-324">**Option values**</span></span> | <span data-ttu-id="7ebc7-325">`true` — отступ для меток `switch`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-325">`true` - Indent `switch` labels</span></span><br /><br /><span data-ttu-id="7ebc7-326">`false` — не использовать отступ для меток `switch`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-326">`false` - Do not indent `switch` labels</span></span> |

<span data-ttu-id="7ebc7-327">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-327">Code examples:</span></span>

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_labels"></a><span data-ttu-id="7ebc7-328">csharp\_indent_labels</span><span class="sxs-lookup"><span data-stu-id="7ebc7-328">csharp\_indent_labels</span></span>

|<span data-ttu-id="7ebc7-329">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-329">Property</span></span>|<span data-ttu-id="7ebc7-330">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-330">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-331">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-331">**Option name**</span></span> | <span data-ttu-id="7ebc7-332">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="7ebc7-332">csharp_indent_labels</span></span> |
| <span data-ttu-id="7ebc7-333">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-333">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-334">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-334">C#</span></span> |
| <span data-ttu-id="7ebc7-335">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-335">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-336">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-336">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-337">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-337">**Option values**</span></span> | <span data-ttu-id="7ebc7-338">`flush_left` — метки размещаются в крайнем левом столбце.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-338">`flush_left` - Labels are placed at the leftmost column</span></span><br /><br /><span data-ttu-id="7ebc7-339">`one_less_than_current` — метки размещаются на предыдущей позиции отступа относительно текущего контекста.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-339">`one_less_than_current` - Labels are placed at one less indent to the current context</span></span><br /><br /><span data-ttu-id="7ebc7-340">`no_change` — метки размещаются на той же позиции отступа, что и текущий контекст.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-340">`no_change` - Labels are placed at the same indent as the current context</span></span> |

<span data-ttu-id="7ebc7-341">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-341">Code examples:</span></span>

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

#### <a name="csharp_indent_block_contents"></a><span data-ttu-id="7ebc7-342">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="7ebc7-342">csharp_indent_block_contents</span></span>

|<span data-ttu-id="7ebc7-343">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-343">Property</span></span>|<span data-ttu-id="7ebc7-344">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-344">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-345">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-345">**Option name**</span></span> | <span data-ttu-id="7ebc7-346">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="7ebc7-346">csharp_indent_block_contents</span></span> |
| <span data-ttu-id="7ebc7-347">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-347">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-348">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-348">C#</span></span> |
| <span data-ttu-id="7ebc7-349">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-349">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="7ebc7-350">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-350">Code examples:</span></span>

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_braces"></a><span data-ttu-id="7ebc7-351">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="7ebc7-351">csharp_indent_braces</span></span>

|<span data-ttu-id="7ebc7-352">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-352">Property</span></span>|<span data-ttu-id="7ebc7-353">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-353">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-354">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-354">**Option name**</span></span> | <span data-ttu-id="7ebc7-355">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="7ebc7-355">csharp_indent_braces</span></span> |
| <span data-ttu-id="7ebc7-356">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-356">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-357">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-357">C#</span></span> |
| <span data-ttu-id="7ebc7-358">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-358">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="7ebc7-359">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-359">Code examples:</span></span>

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_case_contents_when_block"></a><span data-ttu-id="7ebc7-360">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="7ebc7-360">csharp_indent_case_contents_when_block</span></span>

|<span data-ttu-id="7ebc7-361">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-361">Property</span></span>|<span data-ttu-id="7ebc7-362">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-362">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-363">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-363">**Option name**</span></span> | <span data-ttu-id="7ebc7-364">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="7ebc7-364">csharp_indent_case_contents_when_block</span></span> |
| <span data-ttu-id="7ebc7-365">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-365">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-366">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-366">C#</span></span> |
| <span data-ttu-id="7ebc7-367">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-367">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="7ebc7-368">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-368">Code examples:</span></span>

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### <a name="spacing-options"></a><span data-ttu-id="7ebc7-369">Параметры интервалов</span><span class="sxs-lookup"><span data-stu-id="7ebc7-369">Spacing options</span></span>

<span data-ttu-id="7ebc7-370">Эти правила форматирования относятся к использованию пробелов для форматирования кода.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-370">These formatting rules concern the use of space characters to format code.</span></span>

<span data-ttu-id="7ebc7-371">Пример файла *EDITORCONFIG*:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-371">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### <a name="csharp_space_after_cast"></a><span data-ttu-id="7ebc7-372">csharp\_space\_after_cast</span><span class="sxs-lookup"><span data-stu-id="7ebc7-372">csharp\_space\_after_cast</span></span>

|<span data-ttu-id="7ebc7-373">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-373">Property</span></span>|<span data-ttu-id="7ebc7-374">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-374">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-375">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-375">**Option name**</span></span> | <span data-ttu-id="7ebc7-376">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="7ebc7-376">csharp_space_after_cast</span></span> |
| <span data-ttu-id="7ebc7-377">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-377">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-378">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-378">C#</span></span> |
| <span data-ttu-id="7ebc7-379">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-379">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-380">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-380">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-381">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-381">**Option values**</span></span> | <span data-ttu-id="7ebc7-382">`true` — разместить пробел между типом и значением в приведении</span><span class="sxs-lookup"><span data-stu-id="7ebc7-382">`true` - Place a space character between a cast and the value</span></span><br /><br /><span data-ttu-id="7ebc7-383">`false` — удалить пробел между типом и значением в приведении</span><span class="sxs-lookup"><span data-stu-id="7ebc7-383">`false` - Remove space between the cast and the value</span></span> |

<span data-ttu-id="7ebc7-384">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-384">Code examples:</span></span>

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a><span data-ttu-id="7ebc7-385">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="7ebc7-385">csharp_space_after_keywords_in_control_flow_statements</span></span>

|<span data-ttu-id="7ebc7-386">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-386">Property</span></span>|<span data-ttu-id="7ebc7-387">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-387">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-388">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-388">**Option name**</span></span> | <span data-ttu-id="7ebc7-389">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="7ebc7-389">csharp_space_after_keywords_in_control_flow_statements</span></span> |
| <span data-ttu-id="7ebc7-390">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-390">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-391">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-391">C#</span></span> |
| <span data-ttu-id="7ebc7-392">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-392">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-393">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-393">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-394">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-394">**Option values**</span></span> | <span data-ttu-id="7ebc7-395">`true` — поместить пробел после ключевого слова в операторе потока управления, например цикле `for`</span><span class="sxs-lookup"><span data-stu-id="7ebc7-395">`true` - Place a space character after a keyword in a control flow statement such as a `for` loop</span></span><br /><br /><span data-ttu-id="7ebc7-396">`false` — удалить пробел после ключевого слова в операторе потока управления, например цикле `for`</span><span class="sxs-lookup"><span data-stu-id="7ebc7-396">`false` - Remove space after a keyword in a control flow statement such as a `for` loop</span></span> |

<span data-ttu-id="7ebc7-397">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-397">Code examples:</span></span>

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a><span data-ttu-id="7ebc7-398">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-398">csharp_space_between_parentheses</span></span>

|<span data-ttu-id="7ebc7-399">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-399">Property</span></span>|<span data-ttu-id="7ebc7-400">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-400">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-401">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-401">**Option name**</span></span> | <span data-ttu-id="7ebc7-402">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-402">csharp_space_between_parentheses</span></span> |
| <span data-ttu-id="7ebc7-403">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-403">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-404">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-404">C#</span></span> |
| <span data-ttu-id="7ebc7-405">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-405">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-406">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-406">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-407">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-407">**Option values**</span></span> | <span data-ttu-id="7ebc7-408">`control_flow_statements` — добавлять пробел между скобками для операторов потока управления.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-408">`control_flow_statements` - Place space between parentheses of control flow statements</span></span><br /><br /><span data-ttu-id="7ebc7-409">`expressions` — добавлять пробел между скобками для выражений.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-409">`expressions` - Place space between parentheses of expressions</span></span><br /><br /><span data-ttu-id="7ebc7-410">`type_casts` — размещать пробел между скобками в приведениях типов.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-410">`type_casts` - Place space between parentheses in type casts</span></span> |

<span data-ttu-id="7ebc7-411">Если пропустить это правило или использовать значение, отличное от `control_flow_statements`, `expressions` или `type_casts`, этот параметр не применяется.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-411">If you omit this rule or use a value other than `control_flow_statements`, `expressions`, or `type_casts`, the setting is not applied.</span></span>

<span data-ttu-id="7ebc7-412">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-412">Code examples:</span></span>

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a><span data-ttu-id="7ebc7-413">csharp\_space\_before\_colon\_in\_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="7ebc7-413">csharp\_space\_before\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="7ebc7-414">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-414">Property</span></span>|<span data-ttu-id="7ebc7-415">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-415">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-416">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-416">**Option name**</span></span> | <span data-ttu-id="7ebc7-417">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="7ebc7-417">csharp_space_before_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="7ebc7-418">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-418">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-419">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-419">C#</span></span> |
| <span data-ttu-id="7ebc7-420">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-420">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-421">Visual Studio 2017 версии 15.7</span><span class="sxs-lookup"><span data-stu-id="7ebc7-421">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="7ebc7-422">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-422">**Option values**</span></span> | <span data-ttu-id="7ebc7-423">`true` — поместить пробел перед двоеточием для баз или интерфейсов в объявлении типа</span><span class="sxs-lookup"><span data-stu-id="7ebc7-423">`true` - Place a space character before the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="7ebc7-424">`false` — удалить пробел перед двоеточием для баз или интерфейсов в объявлении типа</span><span class="sxs-lookup"><span data-stu-id="7ebc7-424">`false` - Remove space before the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="7ebc7-425">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-425">Code examples:</span></span>

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a><span data-ttu-id="7ebc7-426">csharp\_space\_after\_colon\_in\_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="7ebc7-426">csharp\_space\_after\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="7ebc7-427">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-427">Property</span></span>|<span data-ttu-id="7ebc7-428">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-428">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-429">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-429">**Option name**</span></span> | <span data-ttu-id="7ebc7-430">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="7ebc7-430">csharp_space_after_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="7ebc7-431">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-431">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-432">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-432">C#</span></span> |
| <span data-ttu-id="7ebc7-433">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-433">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-434">Visual Studio 2017 версии 15.7</span><span class="sxs-lookup"><span data-stu-id="7ebc7-434">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="7ebc7-435">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-435">**Option values**</span></span> | <span data-ttu-id="7ebc7-436">`true` — поместить пробел после двоеточия для баз или интерфейсов в объявлении типа</span><span class="sxs-lookup"><span data-stu-id="7ebc7-436">`true` - Place a space character after the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="7ebc7-437">`false` — удалить пробел после двоеточия для баз или интерфейсов в объявлении типа</span><span class="sxs-lookup"><span data-stu-id="7ebc7-437">`false` - Remove space after the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="7ebc7-438">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-438">Code examples:</span></span>

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### <a name="csharp_space_around_binary_operators"></a><span data-ttu-id="7ebc7-439">csharp\_space\_around\_binary_operators</span><span class="sxs-lookup"><span data-stu-id="7ebc7-439">csharp\_space\_around\_binary_operators</span></span>

|<span data-ttu-id="7ebc7-440">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-440">Property</span></span>|<span data-ttu-id="7ebc7-441">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-441">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-442">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-442">**Option name**</span></span> | <span data-ttu-id="7ebc7-443">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="7ebc7-443">csharp_space_around_binary_operators</span></span> |
| <span data-ttu-id="7ebc7-444">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-444">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-445">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-445">C#</span></span> |
| <span data-ttu-id="7ebc7-446">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-446">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-447">Visual Studio 2017 версии 15.7</span><span class="sxs-lookup"><span data-stu-id="7ebc7-447">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="7ebc7-448">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-448">**Option values**</span></span> | <span data-ttu-id="7ebc7-449">`before_and_after` — вставлять пробел до и после бинарных операторов.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-449">`before_and_after` - Insert space before and after the binary operator</span></span><br /><br /><span data-ttu-id="7ebc7-450">`none` — удалять пробелы до и после бинарных операторов.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-450">`none` - Remove spaces before and after the binary operator</span></span><br /><br /><span data-ttu-id="7ebc7-451">`ignore` — игнорировать пробелы вокруг бинарных операторов.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-451">`ignore` - Ignore spaces around binary operators</span></span> |

<span data-ttu-id="7ebc7-452">Если пропустить это правило или использовать значение, отличное от `before_and_after`, `none` или `ignore`, этот параметр не применяется.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-452">If you omit this rule, or use a value other than `before_and_after`, `none`, or `ignore`, the setting is not applied.</span></span>

<span data-ttu-id="7ebc7-453">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-453">Code examples:</span></span>

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a><span data-ttu-id="7ebc7-454">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-454">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>

|<span data-ttu-id="7ebc7-455">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-455">Property</span></span>|<span data-ttu-id="7ebc7-456">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-456">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-457">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-457">**Option name**</span></span> | <span data-ttu-id="7ebc7-458">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-458">csharp_space_between_method_declaration_parameter_list_parentheses</span></span> |
| <span data-ttu-id="7ebc7-459">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-459">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-460">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-460">C#</span></span> |
| <span data-ttu-id="7ebc7-461">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-461">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-462">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-462">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-463">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-463">**Option values**</span></span> | <span data-ttu-id="7ebc7-464">`true` — размещать пробел после открывающей скобки и перед закрывающей скобкой в списке параметров объявления метода.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-464">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span><br /><br /><span data-ttu-id="7ebc7-465">`false` — удалить пробел после открывающей скобки и перед закрывающей скобкой в списке параметров объявления метода</span><span class="sxs-lookup"><span data-stu-id="7ebc7-465">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span> |

<span data-ttu-id="7ebc7-466">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-466">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a><span data-ttu-id="7ebc7-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="7ebc7-468">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-468">Property</span></span>|<span data-ttu-id="7ebc7-469">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-469">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-470">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-470">**Option name**</span></span> | <span data-ttu-id="7ebc7-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="7ebc7-472">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-472">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-473">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-473">C#</span></span> |
| <span data-ttu-id="7ebc7-474">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-474">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-475">Visual Studio 2017 версии 15.7</span><span class="sxs-lookup"><span data-stu-id="7ebc7-475">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="7ebc7-476">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-476">**Option values**</span></span> | <span data-ttu-id="7ebc7-477">`true` — вставлять пробел между скобками пустого списка параметров при объявлении метода.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-477">`true` - Insert space within empty parameter list parentheses for a method declaration</span></span><br /><br /><span data-ttu-id="7ebc7-478">`false` — удалять пробел между скобками пустого списка параметров при объявлении метода.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-478">`false` - Remove space within empty parameter list parentheses for a method declaration</span></span> |

<span data-ttu-id="7ebc7-479">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-479">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a><span data-ttu-id="7ebc7-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="7ebc7-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>

|<span data-ttu-id="7ebc7-481">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-481">Property</span></span>|<span data-ttu-id="7ebc7-482">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-482">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-483">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-483">**Option name**</span></span> | <span data-ttu-id="7ebc7-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="7ebc7-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span> |
| <span data-ttu-id="7ebc7-485">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-485">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-486">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-486">C#</span></span> |
| <span data-ttu-id="7ebc7-487">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-487">**Option values**</span></span> | <span data-ttu-id="7ebc7-488">`true` — поместить пробел между именем метода и открывающей круглой скобкой в объявлении метода</span><span class="sxs-lookup"><span data-stu-id="7ebc7-488">`true` - Place a space character between the method name and opening parenthesis in the method declaration</span></span><br /><br /><span data-ttu-id="7ebc7-489">`false` — удалить пробелы между именем метода и открывающей круглой скобкой в объявлении метода</span><span class="sxs-lookup"><span data-stu-id="7ebc7-489">`false` - Remove space characters between the method name and opening parenthesis in the method declaration</span></span> |

<span data-ttu-id="7ebc7-490">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-490">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a><span data-ttu-id="7ebc7-491">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-491">csharp_space_between_method_call_parameter_list_parentheses</span></span>

|<span data-ttu-id="7ebc7-492">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-492">Property</span></span>|<span data-ttu-id="7ebc7-493">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-493">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-494">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-494">**Option name**</span></span> | <span data-ttu-id="7ebc7-495">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-495">csharp_space_between_method_call_parameter_list_parentheses</span></span> |
| <span data-ttu-id="7ebc7-496">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-496">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-497">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-497">C#</span></span> |
| <span data-ttu-id="7ebc7-498">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-498">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-499">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-499">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-500">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-500">**Option values**</span></span> | <span data-ttu-id="7ebc7-501">`true` — размещать пробел после открывающей скобки и перед закрывающей скобкой в вызове метода.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-501">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method call</span></span><br /><br /><span data-ttu-id="7ebc7-502">`false` — удалять пробел после открывающей скобки и перед закрывающей скобкой в вызове метода</span><span class="sxs-lookup"><span data-stu-id="7ebc7-502">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method call</span></span> |

<span data-ttu-id="7ebc7-503">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-503">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a><span data-ttu-id="7ebc7-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="7ebc7-505">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-505">Property</span></span>|<span data-ttu-id="7ebc7-506">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-506">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-507">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-507">**Option name**</span></span> | <span data-ttu-id="7ebc7-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="7ebc7-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="7ebc7-509">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-509">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-510">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-510">C#</span></span> |
| <span data-ttu-id="7ebc7-511">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-511">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-512">Visual Studio 2017 версии 15.7</span><span class="sxs-lookup"><span data-stu-id="7ebc7-512">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="7ebc7-513">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-513">**Option values**</span></span> | <span data-ttu-id="7ebc7-514">`true` — вставлять пробел между скобками в пустом списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-514">`true` - Insert space within empty argument list parentheses</span></span><br /><br /><span data-ttu-id="7ebc7-515">`false` — удалять пробел между скобками в пустом списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-515">`false` - Remove space within empty argument list parentheses</span></span> |

<span data-ttu-id="7ebc7-516">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-516">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a><span data-ttu-id="7ebc7-517">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="7ebc7-517">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>

|<span data-ttu-id="7ebc7-518">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-518">Property</span></span>|<span data-ttu-id="7ebc7-519">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-519">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-520">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-520">**Option name**</span></span> | <span data-ttu-id="7ebc7-521">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="7ebc7-521">csharp_space_between_method_call_name_and_opening_parenthesis</span></span> |
| <span data-ttu-id="7ebc7-522">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-522">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-523">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-523">C#</span></span> |
| <span data-ttu-id="7ebc7-524">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-524">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-525">Visual Studio 2017 версии 15.7</span><span class="sxs-lookup"><span data-stu-id="7ebc7-525">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="7ebc7-526">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-526">**Option values**</span></span> | <span data-ttu-id="7ebc7-527">`true` — вставлять пробел между именем вызываемого метода и открывающей скобкой.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-527">`true` - Insert space between method call name and opening parenthesis</span></span><br /><br /><span data-ttu-id="7ebc7-528">`false` — удалять пробел между именем вызываемого метода и открывающей скобкой.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-528">`false` - Remove space between method call name and opening parenthesis</span></span> |

<span data-ttu-id="7ebc7-529">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-529">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_after_comma"></a><span data-ttu-id="7ebc7-530">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="7ebc7-530">csharp_space_after_comma</span></span>

|<span data-ttu-id="7ebc7-531">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-531">Property</span></span>|<span data-ttu-id="7ebc7-532">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-532">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-533">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-533">**Option name**</span></span> | <span data-ttu-id="7ebc7-534">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="7ebc7-534">csharp_space_after_comma</span></span> |
| <span data-ttu-id="7ebc7-535">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-535">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-536">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-536">C#</span></span> |
| <span data-ttu-id="7ebc7-537">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-537">**Option values**</span></span> | <span data-ttu-id="7ebc7-538">`true` — вставлять пробел после запятой.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-538">`true` - Insert space after a comma</span></span><br /><br /><span data-ttu-id="7ebc7-539">`false` — удалять пробел после запятой.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-539">`false` - Remove space after a comma</span></span> |

<span data-ttu-id="7ebc7-540">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-540">Code examples:</span></span>

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a><span data-ttu-id="7ebc7-541">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="7ebc7-541">csharp_space_before_comma</span></span>

|<span data-ttu-id="7ebc7-542">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-542">Property</span></span>|<span data-ttu-id="7ebc7-543">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-543">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-544">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-544">**Option name**</span></span> | <span data-ttu-id="7ebc7-545">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="7ebc7-545">csharp_space_before_comma</span></span> |
| <span data-ttu-id="7ebc7-546">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-546">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-547">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-547">C#</span></span> |
| <span data-ttu-id="7ebc7-548">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-548">**Option values**</span></span> | <span data-ttu-id="7ebc7-549">`true` — вставлять пробел перед запятой</span><span class="sxs-lookup"><span data-stu-id="7ebc7-549">`true` - Insert space before a comma</span></span><br /><br /><span data-ttu-id="7ebc7-550">`false` — удалять пробел перед запятой</span><span class="sxs-lookup"><span data-stu-id="7ebc7-550">`false` - Remove space before a comma</span></span> |

<span data-ttu-id="7ebc7-551">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-551">Code examples:</span></span>

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a><span data-ttu-id="7ebc7-552">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="7ebc7-552">csharp_space_after_dot</span></span>

|<span data-ttu-id="7ebc7-553">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-553">Property</span></span>|<span data-ttu-id="7ebc7-554">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-554">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-555">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-555">**Option name**</span></span> | <span data-ttu-id="7ebc7-556">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="7ebc7-556">csharp_space_after_dot</span></span> |
| <span data-ttu-id="7ebc7-557">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-557">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-558">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-558">C#</span></span> |
| <span data-ttu-id="7ebc7-559">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-559">**Option values**</span></span> | <span data-ttu-id="7ebc7-560">`true` — вставлять пробел после точки.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-560">`true` - Insert space after a dot</span></span><br /><br /><span data-ttu-id="7ebc7-561">`false` — удалять пробел после точки.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-561">`false` - Remove space after a dot</span></span> |

<span data-ttu-id="7ebc7-562">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-562">Code examples:</span></span>

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a><span data-ttu-id="7ebc7-563">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="7ebc7-563">csharp_space_before_dot</span></span>

|<span data-ttu-id="7ebc7-564">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-564">Property</span></span>|<span data-ttu-id="7ebc7-565">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-565">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-566">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-566">**Option name**</span></span> | <span data-ttu-id="7ebc7-567">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="7ebc7-567">csharp_space_before_dot</span></span> |
| <span data-ttu-id="7ebc7-568">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-568">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-569">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-569">C#</span></span> |
| <span data-ttu-id="7ebc7-570">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-570">**Option values**</span></span> | <span data-ttu-id="7ebc7-571">`true` — вставлять пробел перед точкой</span><span class="sxs-lookup"><span data-stu-id="7ebc7-571">`true` - Insert space before a dot</span></span> <br /><br /><span data-ttu-id="7ebc7-572">`false` — удалять пробел перед точкой</span><span class="sxs-lookup"><span data-stu-id="7ebc7-572">`false` - Remove space before a dot</span></span> |

<span data-ttu-id="7ebc7-573">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-573">Code examples:</span></span>

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a><span data-ttu-id="7ebc7-574">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="7ebc7-574">csharp_space_after_semicolon_in_for_statement</span></span>

|<span data-ttu-id="7ebc7-575">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-575">Property</span></span>|<span data-ttu-id="7ebc7-576">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-576">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-577">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-577">**Option name**</span></span> | <span data-ttu-id="7ebc7-578">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="7ebc7-578">csharp_space_after_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="7ebc7-579">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-579">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-580">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-580">C#</span></span> |
| <span data-ttu-id="7ebc7-581">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-581">**Option values**</span></span> | <span data-ttu-id="7ebc7-582">`true` — вставлять пробел после каждой точки с запятой в операторах `for`</span><span class="sxs-lookup"><span data-stu-id="7ebc7-582">`true` - Insert space after each semicolon in a `for` statement</span></span><br /><br /><span data-ttu-id="7ebc7-583">`false` — удалять пробел после каждой точки с запятой в операторах `for`</span><span class="sxs-lookup"><span data-stu-id="7ebc7-583">`false` - Remove space after each semicolon in a `for` statement</span></span> |

<span data-ttu-id="7ebc7-584">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-584">Code examples:</span></span>

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

#### <a name="csharp_space_before_semicolon_in_for_statement"></a><span data-ttu-id="7ebc7-585">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="7ebc7-585">csharp_space_before_semicolon_in_for_statement</span></span>

|<span data-ttu-id="7ebc7-586">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-586">Property</span></span>|<span data-ttu-id="7ebc7-587">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-587">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-588">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-588">**Option name**</span></span> | <span data-ttu-id="7ebc7-589">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="7ebc7-589">csharp_space_before_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="7ebc7-590">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-590">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-591">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-591">C#</span></span> |
| <span data-ttu-id="7ebc7-592">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-592">**Option values**</span></span> | <span data-ttu-id="7ebc7-593">`true` — вставлять пробел перед каждой точкой с запятой в операторах `for`</span><span class="sxs-lookup"><span data-stu-id="7ebc7-593">`true` - Insert space before each semicolon in a `for` statement</span></span> <br /><br /><span data-ttu-id="7ebc7-594">`false` — удалять пробел перед каждой точкой с запятой в операторах `for`</span><span class="sxs-lookup"><span data-stu-id="7ebc7-594">`false` - Remove space before each semicolon in a `for` statement</span></span> |

<span data-ttu-id="7ebc7-595">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-595">Code examples:</span></span>

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a><span data-ttu-id="7ebc7-596">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="7ebc7-596">csharp_space_around_declaration_statements</span></span>

|<span data-ttu-id="7ebc7-597">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-597">Property</span></span>|<span data-ttu-id="7ebc7-598">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-598">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-599">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-599">**Option name**</span></span> | <span data-ttu-id="7ebc7-600">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="7ebc7-600">csharp_space_around_declaration_statements</span></span> |
| <span data-ttu-id="7ebc7-601">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-601">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-602">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-602">C#</span></span> |
| <span data-ttu-id="7ebc7-603">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-603">**Option values**</span></span> | <span data-ttu-id="7ebc7-604">`ignore` — не удалять лишние пробелы в операторах объявления</span><span class="sxs-lookup"><span data-stu-id="7ebc7-604">`ignore` - Don't remove extra space characters in declaration statements</span></span><br /><br /><span data-ttu-id="7ebc7-605">`false` — удалять лишние пробелы в операторах объявления</span><span class="sxs-lookup"><span data-stu-id="7ebc7-605">`false` - Remove extra space characters in declaration statements</span></span> |

<span data-ttu-id="7ebc7-606">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-606">Code examples:</span></span>

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a><span data-ttu-id="7ebc7-607">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="7ebc7-607">csharp_space_before_open_square_brackets</span></span>

|<span data-ttu-id="7ebc7-608">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-608">Property</span></span>|<span data-ttu-id="7ebc7-609">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-609">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-610">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-610">**Option name**</span></span> | <span data-ttu-id="7ebc7-611">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="7ebc7-611">csharp_space_before_open_square_brackets</span></span> |
| <span data-ttu-id="7ebc7-612">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-612">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-613">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-613">C#</span></span> |
| <span data-ttu-id="7ebc7-614">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-614">**Option values**</span></span> | <span data-ttu-id="7ebc7-615">`true` — вставлять пробел перед открывающей квадратной скобкой `[`</span><span class="sxs-lookup"><span data-stu-id="7ebc7-615">`true` - Insert space before opening square brackets `[`</span></span> <br /><br /><span data-ttu-id="7ebc7-616">`false` — удалять пробел перед открывающей квадратной скобкой `[`</span><span class="sxs-lookup"><span data-stu-id="7ebc7-616">`false` - Remove space before opening square brackets `[`</span></span> |

<span data-ttu-id="7ebc7-617">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-617">Code examples:</span></span>

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a><span data-ttu-id="7ebc7-618">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="7ebc7-618">csharp_space_between_empty_square_brackets</span></span>

|<span data-ttu-id="7ebc7-619">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-619">Property</span></span>|<span data-ttu-id="7ebc7-620">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-620">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-621">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-621">**Option name**</span></span> | <span data-ttu-id="7ebc7-622">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="7ebc7-622">csharp_space_between_empty_square_brackets</span></span> |
| <span data-ttu-id="7ebc7-623">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-623">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-624">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-624">C#</span></span> |
| <span data-ttu-id="7ebc7-625">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-625">**Option values**</span></span> | <span data-ttu-id="7ebc7-626">`true` — вставлять пробел перед пустыми квадратными скобками `[ ]`</span><span class="sxs-lookup"><span data-stu-id="7ebc7-626">`true` - Insert space between empty square brackets `[ ]`</span></span> <br /><br /><span data-ttu-id="7ebc7-627">`false` — удалять пробел перед пустыми квадратными скобками `[]`</span><span class="sxs-lookup"><span data-stu-id="7ebc7-627">`false` - Remove space between empty square brackets `[]`</span></span> |

<span data-ttu-id="7ebc7-628">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-628">Code examples:</span></span>

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a><span data-ttu-id="7ebc7-629">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="7ebc7-629">csharp_space_between_square_brackets</span></span>

|<span data-ttu-id="7ebc7-630">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-630">Property</span></span>|<span data-ttu-id="7ebc7-631">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-631">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-632">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-632">**Option name**</span></span> | <span data-ttu-id="7ebc7-633">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="7ebc7-633">csharp_space_between_square_brackets</span></span> |
| <span data-ttu-id="7ebc7-634">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-634">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-635">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-635">C#</span></span> |
| <span data-ttu-id="7ebc7-636">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-636">**Option values**</span></span> | <span data-ttu-id="7ebc7-637">`true` — вставлять пробел в непустых квадратных скобках `[ 0 ]`</span><span class="sxs-lookup"><span data-stu-id="7ebc7-637">`true` - Insert space characters in non-empty square brackets `[ 0 ]`</span></span> <br /><br /><span data-ttu-id="7ebc7-638">`false` — удалять пробел в непустых квадратных скобках `[0]`</span><span class="sxs-lookup"><span data-stu-id="7ebc7-638">`false` - Remove space characters in non-empty square brackets `[0]`</span></span> |

<span data-ttu-id="7ebc7-639">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-639">Code examples:</span></span>

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a><span data-ttu-id="7ebc7-640">Параметры переноса</span><span class="sxs-lookup"><span data-stu-id="7ebc7-640">Wrap options</span></span>

<span data-ttu-id="7ebc7-641">Эти правила форматирования определяют размещение операторов и блоков кода в одной или разных строках.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-641">These formatting rules concern the use of single lines versus separate lines for statements and code blocks.</span></span>

<span data-ttu-id="7ebc7-642">Пример файла *EDITORCONFIG*:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-642">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a><span data-ttu-id="7ebc7-643">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="7ebc7-643">csharp_preserve_single_line_statements</span></span>

|<span data-ttu-id="7ebc7-644">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-644">Property</span></span>|<span data-ttu-id="7ebc7-645">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-645">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-646">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-646">**Option name**</span></span> | <span data-ttu-id="7ebc7-647">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="7ebc7-647">csharp_preserve_single_line_statements</span></span> |
| <span data-ttu-id="7ebc7-648">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-648">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-649">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-649">C#</span></span> |
| <span data-ttu-id="7ebc7-650">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-650">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-651">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-651">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-652">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-652">**Option values**</span></span> | <span data-ttu-id="7ebc7-653">`true` — оставлять выражения и объявления элемента в одной строке.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-653">`true` - Leave statements and member declarations on the same line</span></span><br /><br /><span data-ttu-id="7ebc7-654">`false` — оставлять выражения и объявления элемента в разных строках.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-654">`false` - Leave statements and member declarations on different lines</span></span> |

<span data-ttu-id="7ebc7-655">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-655">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a><span data-ttu-id="7ebc7-656">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="7ebc7-656">csharp_preserve_single_line_blocks</span></span>

|<span data-ttu-id="7ebc7-657">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-657">Property</span></span>|<span data-ttu-id="7ebc7-658">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-658">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-659">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-659">**Option name**</span></span> | <span data-ttu-id="7ebc7-660">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="7ebc7-660">csharp_preserve_single_line_blocks</span></span> |
| <span data-ttu-id="7ebc7-661">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-661">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-662">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-662">C#</span></span> |
| <span data-ttu-id="7ebc7-663">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-663">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-664">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="7ebc7-664">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="7ebc7-665">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-665">**Option values**</span></span> | <span data-ttu-id="7ebc7-666">`true` — оставлять блок кода в одной строке.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-666">`true` - Leave code block on single line</span></span><br /><br /><span data-ttu-id="7ebc7-667">`false` — оставлять блок кода в разных строках.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-667">`false` - Leave code block on separate lines</span></span> |

<span data-ttu-id="7ebc7-668">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-668">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

### <a name="using-directive-options"></a><span data-ttu-id="7ebc7-669">Параметры директивы using</span><span class="sxs-lookup"><span data-stu-id="7ebc7-669">Using directive options</span></span>

<span data-ttu-id="7ebc7-670">Это правило форматирования относится к использованию директив using, размещаемых внутри и вне пространства имен.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-670">This formatting rule concerns the use of using directives being placed inside versus outside a namespace.</span></span>

<span data-ttu-id="7ebc7-671">Пример файла *EDITORCONFIG*:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-671">Example *.editorconfig* file:</span></span>

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a><span data-ttu-id="7ebc7-672">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="7ebc7-672">csharp_using_directive_placement</span></span>

|<span data-ttu-id="7ebc7-673">Свойство.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-673">Property</span></span>|<span data-ttu-id="7ebc7-674">Значение</span><span class="sxs-lookup"><span data-stu-id="7ebc7-674">Value</span></span>|
|-|-|
| <span data-ttu-id="7ebc7-675">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-675">**Option name**</span></span> | <span data-ttu-id="7ebc7-676">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="7ebc7-676">csharp_using_directive_placement</span></span> |
| <span data-ttu-id="7ebc7-677">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-677">**Applicable languages**</span></span> | <span data-ttu-id="7ebc7-678">C#</span><span class="sxs-lookup"><span data-stu-id="7ebc7-678">C#</span></span> |
| <span data-ttu-id="7ebc7-679">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-679">**Introduced version**</span></span> | <span data-ttu-id="7ebc7-680">Visual Studio 2019 версии 16.1</span><span class="sxs-lookup"><span data-stu-id="7ebc7-680">Visual Studio 2019 version 16.1</span></span> |
| <span data-ttu-id="7ebc7-681">**Значения параметра**</span><span class="sxs-lookup"><span data-stu-id="7ebc7-681">**Option values**</span></span> | <span data-ttu-id="7ebc7-682">`outside_namespace` — размещать директивы using вне пространства имен</span><span class="sxs-lookup"><span data-stu-id="7ebc7-682">`outside_namespace` - Leave using directives outside namespace</span></span><br /><br /><span data-ttu-id="7ebc7-683">`inside_namespace` — размещать директивы using внутри пространства имен</span><span class="sxs-lookup"><span data-stu-id="7ebc7-683">`inside_namespace` - Leave using directives inside namespace</span></span> |

<span data-ttu-id="7ebc7-684">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="7ebc7-684">Code examples:</span></span>

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{

}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
}
```

## <a name="see-also"></a><span data-ttu-id="7ebc7-685">См. также</span><span class="sxs-lookup"><span data-stu-id="7ebc7-685">See also</span></span>

- [<span data-ttu-id="7ebc7-686">Правила языка</span><span class="sxs-lookup"><span data-stu-id="7ebc7-686">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="7ebc7-687">Правила именования</span><span class="sxs-lookup"><span data-stu-id="7ebc7-687">Naming rules</span></span>](naming-rules.md)
- [<span data-ttu-id="7ebc7-688">Справочник по правилам стиля кода для .NET</span><span class="sxs-lookup"><span data-stu-id="7ebc7-688">.NET code style rules reference</span></span>](index.md)
