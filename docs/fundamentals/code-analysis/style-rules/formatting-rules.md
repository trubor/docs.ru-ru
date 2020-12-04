---
title: Правила форматирования стиля кода
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
ms.openlocfilehash: 61e6f6a6afdc6aaf9710eef3143af8ae700ef612
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2020
ms.locfileid: "96593198"
---
# <a name="formatting-rules"></a><span data-ttu-id="03c0b-103">Правила форматирования</span><span class="sxs-lookup"><span data-stu-id="03c0b-103">Formatting rules</span></span>

<span data-ttu-id="03c0b-104">Правила форматирования влияют на то, как отступы, пробелы и новые строки выровнены по конструкциям языка программирования .NET.</span><span class="sxs-lookup"><span data-stu-id="03c0b-104">Formatting rules affect how indentation, spaces, and new lines are aligned around .NET programming language constructs.</span></span> <span data-ttu-id="03c0b-105">Правила делятся на следующие категории:</span><span class="sxs-lookup"><span data-stu-id="03c0b-105">The rules fall into the following categories:</span></span>

- <span data-ttu-id="03c0b-106">[Правила форматирования .NET](#net-formatting-rules): правила, применяемые к C# и Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="03c0b-106">[.NET formatting rules](#net-formatting-rules): Rules that apply to both C# and Visual Basic.</span></span> <span data-ttu-id="03c0b-107">Имена параметров EditorConfig для этих правил начинаются с `dotnet_` префикса.</span><span class="sxs-lookup"><span data-stu-id="03c0b-107">The EditorConfig option names for these rules start with `dotnet_` prefix.</span></span>
- <span data-ttu-id="03c0b-108">[Правила форматирования C#](#c-formatting-rules). правила, относящиеся только к языку c#.</span><span class="sxs-lookup"><span data-stu-id="03c0b-108">[C# formatting rules](#c-formatting-rules): Rules that are specific to C# language only.</span></span> <span data-ttu-id="03c0b-109">Имена параметров EditorConfig для этих правил начинаются с `csharp_` префикса.</span><span class="sxs-lookup"><span data-stu-id="03c0b-109">The EditorConfig option names for these rules start with `csharp_` prefix.</span></span>

## <a name="rule-id-ide0055-fix-formatting"></a><span data-ttu-id="03c0b-110">Идентификатор правила: "IDE0055" (исправление форматирования)</span><span class="sxs-lookup"><span data-stu-id="03c0b-110">Rule ID: "IDE0055" (Fix formatting)</span></span>

<span data-ttu-id="03c0b-111">Все параметры форматирования имеют идентификатор `IDE0055` и заголовок правила `Fix formatting` .</span><span class="sxs-lookup"><span data-stu-id="03c0b-111">All formatting options have rule ID `IDE0055` and title `Fix formatting`.</span></span> <span data-ttu-id="03c0b-112">Задайте серьезность нарушения форматирования в файле EditorConfig, используя следующую строку конфигурации.</span><span class="sxs-lookup"><span data-stu-id="03c0b-112">Set the severity of a formatting violation in an EditorConfig file using the following configuration line.</span></span>

```ini
dotnet_diagnostic.IDE0055.severity = <severity value>
```

<span data-ttu-id="03c0b-113">Значение серьезности должно быть `warning` или `error` [принудительно применено при сборке](../overview.md#code-style-analysis).</span><span class="sxs-lookup"><span data-stu-id="03c0b-113">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="03c0b-114">Все возможные значения серьезности см. в разделе [уровень серьезности](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="03c0b-114">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="option-format"></a><span data-ttu-id="03c0b-115">Формат параметра</span><span class="sxs-lookup"><span data-stu-id="03c0b-115">Option format</span></span>

<span data-ttu-id="03c0b-116">Параметры для правил форматирования можно указать в файле EditorConfig в следующем формате:</span><span class="sxs-lookup"><span data-stu-id="03c0b-116">Options for formatting rules can be specified in an EditorConfig file with the following format:</span></span>

`rule_name = value`

<span data-ttu-id="03c0b-117">Для большинства правил вы указываете значение `true` (предпочитать этот стиль) или `value` (не предпочитать этот стиль) для `false`.</span><span class="sxs-lookup"><span data-stu-id="03c0b-117">For many rules, you specify either `true` (prefer this style) or `false` (do not prefer this style) for `value`.</span></span> <span data-ttu-id="03c0b-118">Для нескольких правил указываются другие значения, например `flush_left` или `before_and_after`, которые описывают порядок применения этих правил.</span><span class="sxs-lookup"><span data-stu-id="03c0b-118">For other rules, you specify a value such as `flush_left` or `before_and_after` to describe when and where to apply the rule.</span></span> <span data-ttu-id="03c0b-119">Уровень серьезности указывать не нужно.</span><span class="sxs-lookup"><span data-stu-id="03c0b-119">You don't specify a severity.</span></span>

## <a name="net-formatting-rules"></a><span data-ttu-id="03c0b-120">Правила форматирования .NET</span><span class="sxs-lookup"><span data-stu-id="03c0b-120">.NET formatting rules</span></span>

<span data-ttu-id="03c0b-121">Правила форматирования в этом разделе применимы как к C#, так и к Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="03c0b-121">The formatting rules in this section apply to both C# and Visual Basic.</span></span>

- [<span data-ttu-id="03c0b-122">Управление директивами using</span><span class="sxs-lookup"><span data-stu-id="03c0b-122">Organize usings</span></span>](#organize-using-directives)
  - <span data-ttu-id="03c0b-123">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="03c0b-123">dotnet_sort_system_directives_first</span></span>
  - <span data-ttu-id="03c0b-124">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="03c0b-124">dotnet_separate_import_directive_groups</span></span>

### <a name="organize-using-directives"></a><span data-ttu-id="03c0b-125">Оптимизация директив Using</span><span class="sxs-lookup"><span data-stu-id="03c0b-125">Organize using directives</span></span>

<span data-ttu-id="03c0b-126">Эти правила форматирования относятся к сортировке и отображению директив `using` и инструкций `Imports`.</span><span class="sxs-lookup"><span data-stu-id="03c0b-126">These formatting rules concern the sorting and display of `using` directives and `Imports` statements.</span></span>

<span data-ttu-id="03c0b-127">Пример файла *EDITORCONFIG*:</span><span class="sxs-lookup"><span data-stu-id="03c0b-127">Example *.editorconfig* file:</span></span>

```ini
# .NET formatting rules
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a><span data-ttu-id="03c0b-128">dotnet\_sort\_system\_directives_first</span><span class="sxs-lookup"><span data-stu-id="03c0b-128">dotnet\_sort\_system\_directives_first</span></span>

|<span data-ttu-id="03c0b-129">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-129">Property</span></span>|<span data-ttu-id="03c0b-130">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-130">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-131">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-131">**Option name**</span></span> | <span data-ttu-id="03c0b-132">dotnet_sort_system_directives_first</span><span class="sxs-lookup"><span data-stu-id="03c0b-132">dotnet_sort_system_directives_first</span></span> |
| <span data-ttu-id="03c0b-133">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-133">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-134">C# и Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03c0b-134">C# and Visual Basic</span></span> |
| <span data-ttu-id="03c0b-135">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-135">**Introduced version**</span></span> | <span data-ttu-id="03c0b-136">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-136">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-137">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-137">**Option values**</span></span> | <span data-ttu-id="03c0b-138">`true` — Сортировка `System.*` `using` директив по алфавиту и размещение их перед другими директивами using.</span><span class="sxs-lookup"><span data-stu-id="03c0b-138">`true` - Sort `System.*` `using` directives alphabetically, and place them before other using directives.</span></span><br /><br /><span data-ttu-id="03c0b-139">`false` — Не размещать `System.*` `using` директивы перед другими `using` директивами.</span><span class="sxs-lookup"><span data-stu-id="03c0b-139">`false` - Do not place `System.*` `using` directives before other `using` directives.</span></span> |

<span data-ttu-id="03c0b-140">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-140">Code examples:</span></span>

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

#### <a name="dotnet_separate_import_directive_groups"></a><span data-ttu-id="03c0b-141">dotnet\_separate\_import\_directive\_groups</span><span class="sxs-lookup"><span data-stu-id="03c0b-141">dotnet\_separate\_import\_directive\_groups</span></span>

|<span data-ttu-id="03c0b-142">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-142">Property</span></span>|<span data-ttu-id="03c0b-143">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-143">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-144">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-144">**Option name**</span></span> | <span data-ttu-id="03c0b-145">dotnet_separate_import_directive_groups</span><span class="sxs-lookup"><span data-stu-id="03c0b-145">dotnet_separate_import_directive_groups</span></span> |
| <span data-ttu-id="03c0b-146">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-146">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-147">C# и Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03c0b-147">C# and Visual Basic</span></span> |
| <span data-ttu-id="03c0b-148">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-148">**Introduced version**</span></span> | <span data-ttu-id="03c0b-149">Visual Studio 2017 версии 15.5</span><span class="sxs-lookup"><span data-stu-id="03c0b-149">Visual Studio 2017 version 15.5</span></span> |
| <span data-ttu-id="03c0b-150">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-150">**Option values**</span></span> | <span data-ttu-id="03c0b-151">`true` — поместить пустую строку между группами директив `using`.</span><span class="sxs-lookup"><span data-stu-id="03c0b-151">`true` - Place a blank line between `using` directive groups.</span></span><br /><br /><span data-ttu-id="03c0b-152">`false` — не помещать пустую строку между группами директив `using`.</span><span class="sxs-lookup"><span data-stu-id="03c0b-152">`false` - Do not place a blank line between `using` directive groups.</span></span> |

<span data-ttu-id="03c0b-153">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-153">Code examples:</span></span>

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

## <a name="c-formatting-rules"></a><span data-ttu-id="03c0b-154">Правила форматирования C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-154">C# formatting rules</span></span>

<span data-ttu-id="03c0b-155">Правила форматирования в этом разделе относятся только к коду C#.</span><span class="sxs-lookup"><span data-stu-id="03c0b-155">The formatting rules in this section apply only to C# code.</span></span>

- [<span data-ttu-id="03c0b-156">Параметры перевода строки</span><span class="sxs-lookup"><span data-stu-id="03c0b-156">Newline options</span></span>](#new-line-options)
  - <span data-ttu-id="03c0b-157">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="03c0b-157">csharp_new_line_before_open_brace</span></span>
  - <span data-ttu-id="03c0b-158">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="03c0b-158">csharp_new_line_before_else</span></span>
  - <span data-ttu-id="03c0b-159">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="03c0b-159">csharp_new_line_before_catch</span></span>
  - <span data-ttu-id="03c0b-160">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="03c0b-160">csharp_new_line_before_finally</span></span>
  - <span data-ttu-id="03c0b-161">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="03c0b-161">csharp_new_line_before_members_in_object_initializers</span></span>
  - <span data-ttu-id="03c0b-162">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="03c0b-162">csharp_new_line_before_members_in_anonymous_types</span></span>
  - <span data-ttu-id="03c0b-163">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="03c0b-163">csharp_new_line_between_query_expression_clauses</span></span>
- [<span data-ttu-id="03c0b-164">Параметры отступа</span><span class="sxs-lookup"><span data-stu-id="03c0b-164">Indentation options</span></span>](#indentation-options)
  - <span data-ttu-id="03c0b-165">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="03c0b-165">csharp_indent_case_contents</span></span>
  - <span data-ttu-id="03c0b-166">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="03c0b-166">csharp_indent_switch_labels</span></span>
  - <span data-ttu-id="03c0b-167">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="03c0b-167">csharp_indent_labels</span></span>
  - <span data-ttu-id="03c0b-168">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="03c0b-168">csharp_indent_block_contents</span></span>
  - <span data-ttu-id="03c0b-169">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="03c0b-169">csharp_indent_braces</span></span>
  - <span data-ttu-id="03c0b-170">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="03c0b-170">csharp_indent_case_contents_when_block</span></span>
- [<span data-ttu-id="03c0b-171">Параметры интервалов</span><span class="sxs-lookup"><span data-stu-id="03c0b-171">Spacing options</span></span>](#spacing-options)
  - <span data-ttu-id="03c0b-172">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="03c0b-172">csharp_space_after_cast</span></span>
  - <span data-ttu-id="03c0b-173">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="03c0b-173">csharp_space_after_keywords_in_control_flow_statements</span></span>
  - <span data-ttu-id="03c0b-174">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-174">csharp_space_between_parentheses</span></span>
  - <span data-ttu-id="03c0b-175">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="03c0b-175">csharp_space_before_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="03c0b-176">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="03c0b-176">csharp_space_after_colon_in_inheritance_clause</span></span>
  - <span data-ttu-id="03c0b-177">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="03c0b-177">csharp_space_around_binary_operators</span></span>
  - <span data-ttu-id="03c0b-178">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-178">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>
  - <span data-ttu-id="03c0b-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-179">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="03c0b-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="03c0b-180">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>
  - <span data-ttu-id="03c0b-181">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-181">csharp_space_between_method_call_parameter_list_parentheses</span></span>
  - <span data-ttu-id="03c0b-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-182">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>
  - <span data-ttu-id="03c0b-183">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="03c0b-183">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>
  - <span data-ttu-id="03c0b-184">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="03c0b-184">csharp_space_after_comma</span></span>
  - <span data-ttu-id="03c0b-185">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="03c0b-185">csharp_space_before_comma</span></span>
  - <span data-ttu-id="03c0b-186">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="03c0b-186">csharp_space_after_dot</span></span>
  - <span data-ttu-id="03c0b-187">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="03c0b-187">csharp_space_before_dot</span></span>
  - <span data-ttu-id="03c0b-188">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="03c0b-188">csharp_space_after_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="03c0b-189">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="03c0b-189">csharp_space_before_semicolon_in_for_statement</span></span>
  - <span data-ttu-id="03c0b-190">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="03c0b-190">csharp_space_around_declaration_statements</span></span>
  - <span data-ttu-id="03c0b-191">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="03c0b-191">csharp_space_before_open_square_brackets</span></span>
  - <span data-ttu-id="03c0b-192">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="03c0b-192">csharp_space_between_empty_square_brackets</span></span>
  - <span data-ttu-id="03c0b-193">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="03c0b-193">csharp_space_between_square_brackets</span></span>
- [<span data-ttu-id="03c0b-194">Параметры переноса</span><span class="sxs-lookup"><span data-stu-id="03c0b-194">Wrap options</span></span>](#wrap-options)
  - <span data-ttu-id="03c0b-195">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="03c0b-195">csharp_preserve_single_line_statements</span></span>
  - <span data-ttu-id="03c0b-196">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="03c0b-196">csharp_preserve_single_line_blocks</span></span>
- [<span data-ttu-id="03c0b-197">Параметры директивы using</span><span class="sxs-lookup"><span data-stu-id="03c0b-197">Using directive options</span></span>](#using-directive-options)
  - <span data-ttu-id="03c0b-198">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="03c0b-198">csharp_using_directive_placement</span></span>

### <a name="new-line-options"></a><span data-ttu-id="03c0b-199">Параметры новой строки</span><span class="sxs-lookup"><span data-stu-id="03c0b-199">New-line options</span></span>

<span data-ttu-id="03c0b-200">Эти правила форматирования относятся использованию новых строк для форматирования кода.</span><span class="sxs-lookup"><span data-stu-id="03c0b-200">These formatting rules concern the use of new lines to format code.</span></span>

<span data-ttu-id="03c0b-201">Пример файла *EDITORCONFIG*:</span><span class="sxs-lookup"><span data-stu-id="03c0b-201">Example *.editorconfig* file:</span></span>

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

#### <a name="csharp_new_line_before_open_brace"></a><span data-ttu-id="03c0b-202">csharp\_new\_line\_before\_open_brace</span><span class="sxs-lookup"><span data-stu-id="03c0b-202">csharp\_new\_line\_before\_open_brace</span></span>

<span data-ttu-id="03c0b-203">Это правило определяет, следует ли располагать открывающую фигурную скобку `{` одной строке с предшествующим кодом или на новой строке.</span><span class="sxs-lookup"><span data-stu-id="03c0b-203">This rule concerns whether an open brace `{` should be placed on the same line as the preceding code, or on a new line.</span></span> <span data-ttu-id="03c0b-204">Для этого правила укажите **all**, **none** либо один или несколько элементов кода, таких как **methods** или **properties**, для которых следует применять это правило.</span><span class="sxs-lookup"><span data-stu-id="03c0b-204">For this rule, you specify **all**, **none**, or one or more code elements such as **methods** or **properties**, to define when this rule should be applied.</span></span> <span data-ttu-id="03c0b-205">Если вы указываете несколько элементов кода, разделяйте их запятыми (,).</span><span class="sxs-lookup"><span data-stu-id="03c0b-205">To specify multiple code elements, separate them with a comma (,).</span></span>

|<span data-ttu-id="03c0b-206">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-206">Property</span></span>|<span data-ttu-id="03c0b-207">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-207">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-208">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-208">**Option name**</span></span> | <span data-ttu-id="03c0b-209">csharp_new_line_before_open_brace</span><span class="sxs-lookup"><span data-stu-id="03c0b-209">csharp_new_line_before_open_brace</span></span> |
| <span data-ttu-id="03c0b-210">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-210">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-211">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-211">C#</span></span> |
| <span data-ttu-id="03c0b-212">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-212">**Introduced version**</span></span> | <span data-ttu-id="03c0b-213">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-213">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-214">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-214">**Option values**</span></span> | <span data-ttu-id="03c0b-215">`all` — требовать, чтобы фигурные скобки для всех выражений размещались в новой строке (стиль Олмана).</span><span class="sxs-lookup"><span data-stu-id="03c0b-215">`all` - Require braces to be on a new line for all expressions ("Allman" style).</span></span><br /><br /><span data-ttu-id="03c0b-216">`none` — требовать, чтобы фигурные скобки для всех выражений размещались в строке выражения (стиль Кернигана и Ритчи).</span><span class="sxs-lookup"><span data-stu-id="03c0b-216">`none` - Require braces to be on the same line for all expressions ("K&R").</span></span><br /><br /><span data-ttu-id="03c0b-217">`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` — требовать, чтобы фигурные скобки для указанного элемента кода размещались в новой строке (стиль Олмана).</span><span class="sxs-lookup"><span data-stu-id="03c0b-217">`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` - Require braces to be on a new line for the specified code element ("Allman" style).</span></span> |

<span data-ttu-id="03c0b-218">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-218">Code examples:</span></span>

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

#### <a name="csharp_new_line_before_else"></a><span data-ttu-id="03c0b-219">csharp\_new\_line\_before_else</span><span class="sxs-lookup"><span data-stu-id="03c0b-219">csharp\_new\_line\_before_else</span></span>

|<span data-ttu-id="03c0b-220">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-220">Property</span></span>|<span data-ttu-id="03c0b-221">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-221">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-222">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-222">**Option name**</span></span> | <span data-ttu-id="03c0b-223">csharp_new_line_before_else</span><span class="sxs-lookup"><span data-stu-id="03c0b-223">csharp_new_line_before_else</span></span> |
| <span data-ttu-id="03c0b-224">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-224">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-225">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-225">C#</span></span> |
| <span data-ttu-id="03c0b-226">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-226">**Introduced version**</span></span> | <span data-ttu-id="03c0b-227">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-227">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-228">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-228">**Option values**</span></span> | <span data-ttu-id="03c0b-229">`true` — размещать инструкции `else` в новой строке.</span><span class="sxs-lookup"><span data-stu-id="03c0b-229">`true` - Place `else` statements on a new line.</span></span><br /><br /><span data-ttu-id="03c0b-230">`false` — размещать инструкции `else` в той же строке.</span><span class="sxs-lookup"><span data-stu-id="03c0b-230">`false` - Place `else` statements on the same line.</span></span> |

<span data-ttu-id="03c0b-231">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-231">Code examples:</span></span>

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

#### <a name="csharp_new_line_before_catch"></a><span data-ttu-id="03c0b-232">csharp\_new\_line\_before_catch</span><span class="sxs-lookup"><span data-stu-id="03c0b-232">csharp\_new\_line\_before_catch</span></span>

|<span data-ttu-id="03c0b-233">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-233">Property</span></span>|<span data-ttu-id="03c0b-234">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-234">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-235">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-235">**Option name**</span></span> | <span data-ttu-id="03c0b-236">csharp_new_line_before_catch</span><span class="sxs-lookup"><span data-stu-id="03c0b-236">csharp_new_line_before_catch</span></span> |
| <span data-ttu-id="03c0b-237">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-237">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-238">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-238">C#</span></span> |
| <span data-ttu-id="03c0b-239">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-239">**Introduced version**</span></span> | <span data-ttu-id="03c0b-240">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-240">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-241">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-241">**Option values**</span></span> | <span data-ttu-id="03c0b-242">`true` — размещать инструкции `catch` в новой строке.</span><span class="sxs-lookup"><span data-stu-id="03c0b-242">`true` - Place `catch` statements on a new line.</span></span><br /><br /><span data-ttu-id="03c0b-243">`false` — размещать инструкции `catch` в той же строке.</span><span class="sxs-lookup"><span data-stu-id="03c0b-243">`false` - Place `catch` statements on the same line.</span></span> |

<span data-ttu-id="03c0b-244">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-244">Code examples:</span></span>

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

#### <a name="csharp_new_line_before_finally"></a><span data-ttu-id="03c0b-245">csharp\_new\_line\_before_finally</span><span class="sxs-lookup"><span data-stu-id="03c0b-245">csharp\_new\_line\_before_finally</span></span>

|<span data-ttu-id="03c0b-246">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-246">Property</span></span>|<span data-ttu-id="03c0b-247">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-247">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-248">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-248">**Option name**</span></span> | <span data-ttu-id="03c0b-249">csharp_new_line_before_finally</span><span class="sxs-lookup"><span data-stu-id="03c0b-249">csharp_new_line_before_finally</span></span> |
| <span data-ttu-id="03c0b-250">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-250">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-251">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-251">C#</span></span> |
| <span data-ttu-id="03c0b-252">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-252">**Introduced version**</span></span> | <span data-ttu-id="03c0b-253">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-253">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-254">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-254">**Option values**</span></span> | <span data-ttu-id="03c0b-255">`true` — требовать, чтобы инструкции `finally` размещались в новой строке после закрывающей фигурной скобки.</span><span class="sxs-lookup"><span data-stu-id="03c0b-255">`true` - Require `finally` statements to be on a new line after the closing brace.</span></span><br /><br /><span data-ttu-id="03c0b-256">`false` — требовать, чтобы инструкции `finally` размещались в той же строке после закрывающей фигурной скобки.</span><span class="sxs-lookup"><span data-stu-id="03c0b-256">`false` - Require `finally` statements to be on the same line as the closing brace.</span></span> |

<span data-ttu-id="03c0b-257">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-257">Code examples:</span></span>

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

#### <a name="csharp_new_line_before_members_in_object_initializers"></a><span data-ttu-id="03c0b-258">csharp\_new\_line\_before\_members\_in\_object_initializers</span><span class="sxs-lookup"><span data-stu-id="03c0b-258">csharp\_new\_line\_before\_members\_in\_object_initializers</span></span>

|<span data-ttu-id="03c0b-259">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-259">Property</span></span>|<span data-ttu-id="03c0b-260">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-260">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-261">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-261">**Option name**</span></span> | <span data-ttu-id="03c0b-262">csharp_new_line_before_members_in_object_initializers</span><span class="sxs-lookup"><span data-stu-id="03c0b-262">csharp_new_line_before_members_in_object_initializers</span></span> |
| <span data-ttu-id="03c0b-263">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-263">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-264">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-264">C#</span></span> |
| <span data-ttu-id="03c0b-265">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-265">**Introduced version**</span></span> | <span data-ttu-id="03c0b-266">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-266">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-267">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-267">**Option values**</span></span> | <span data-ttu-id="03c0b-268">`true` — требовать, чтобы элементы инициализаторов объектов размещались в разных строках.</span><span class="sxs-lookup"><span data-stu-id="03c0b-268">`true` - Require members of object initializers to be on separate lines</span></span><br /><br /><span data-ttu-id="03c0b-269">`false` — требовать, чтобы элементы инициализаторов объектов размещались в той же строке.</span><span class="sxs-lookup"><span data-stu-id="03c0b-269">`false` - Require members of object initializers to be on the same line</span></span> |

<span data-ttu-id="03c0b-270">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-270">Code examples:</span></span>

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

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a><span data-ttu-id="03c0b-271">csharp\_new\_line\_before\_members\_in\_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="03c0b-271">csharp\_new\_line\_before\_members\_in\_anonymous_types</span></span>

|<span data-ttu-id="03c0b-272">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-272">Property</span></span>|<span data-ttu-id="03c0b-273">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-273">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-274">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-274">**Option name**</span></span> | <span data-ttu-id="03c0b-275">csharp_new_line_before_members_in_anonymous_types</span><span class="sxs-lookup"><span data-stu-id="03c0b-275">csharp_new_line_before_members_in_anonymous_types</span></span> |
| <span data-ttu-id="03c0b-276">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-276">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-277">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-277">C#</span></span> |
| <span data-ttu-id="03c0b-278">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-278">**Introduced version**</span></span> | <span data-ttu-id="03c0b-279">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-279">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-280">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-280">**Option values**</span></span> | <span data-ttu-id="03c0b-281">`true` — требовать, чтобы элементы анонимных типов размещались в разных строках.</span><span class="sxs-lookup"><span data-stu-id="03c0b-281">`true` - Require members of anonymous types to be on separate lines</span></span><br /><br /><span data-ttu-id="03c0b-282">`false` — требовать, чтобы элементы анонимных типов размещались в той же строке.</span><span class="sxs-lookup"><span data-stu-id="03c0b-282">`false` - Require members of anonymous types to be on the same line</span></span> |

<span data-ttu-id="03c0b-283">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-283">Code examples:</span></span>

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

#### <a name="csharp_new_line_between_query_expression_clauses"></a><span data-ttu-id="03c0b-284">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="03c0b-284">csharp_new_line_between_query_expression_clauses</span></span>

|<span data-ttu-id="03c0b-285">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-285">Property</span></span>|<span data-ttu-id="03c0b-286">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-286">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-287">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-287">**Option name**</span></span> | <span data-ttu-id="03c0b-288">csharp_new_line_between_query_expression_clauses</span><span class="sxs-lookup"><span data-stu-id="03c0b-288">csharp_new_line_between_query_expression_clauses</span></span> |
| <span data-ttu-id="03c0b-289">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-289">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-290">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-290">C#</span></span> |
| <span data-ttu-id="03c0b-291">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-291">**Introduced version**</span></span> | <span data-ttu-id="03c0b-292">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-292">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-293">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-293">**Option values**</span></span> | <span data-ttu-id="03c0b-294">`true` — требовать, чтобы элементы в предложениях выражений запросов размещались в отдельных строках.</span><span class="sxs-lookup"><span data-stu-id="03c0b-294">`true` - Require elements of query expression clauses to be on separate lines</span></span><br /><br /><span data-ttu-id="03c0b-295">`false` — требовать, чтобы элементы в предложениях выражений запросов размещались в той же строке.</span><span class="sxs-lookup"><span data-stu-id="03c0b-295">`false` - Require elements of query expression clauses to be on the same line</span></span> |

<span data-ttu-id="03c0b-296">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-296">Code examples:</span></span>

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a><span data-ttu-id="03c0b-297">Параметры отступа</span><span class="sxs-lookup"><span data-stu-id="03c0b-297">Indentation options</span></span>

<span data-ttu-id="03c0b-298">Эти правила форматирования относятся к использованию отступа для форматирования кода.</span><span class="sxs-lookup"><span data-stu-id="03c0b-298">These formatting rules concern the use of indentation to format code.</span></span>

<span data-ttu-id="03c0b-299">Пример файла *EDITORCONFIG*:</span><span class="sxs-lookup"><span data-stu-id="03c0b-299">Example *.editorconfig* file:</span></span>

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

#### <a name="csharp_indent_case_contents"></a><span data-ttu-id="03c0b-300">csharp\_indent\_case_contents</span><span class="sxs-lookup"><span data-stu-id="03c0b-300">csharp\_indent\_case_contents</span></span>

|<span data-ttu-id="03c0b-301">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-301">Property</span></span>|<span data-ttu-id="03c0b-302">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-302">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-303">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-303">**Option name**</span></span> | <span data-ttu-id="03c0b-304">csharp_indent_case_contents</span><span class="sxs-lookup"><span data-stu-id="03c0b-304">csharp_indent_case_contents</span></span> |
| <span data-ttu-id="03c0b-305">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-305">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-306">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-306">C#</span></span> |
| <span data-ttu-id="03c0b-307">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-307">**Introduced version**</span></span> | <span data-ttu-id="03c0b-308">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-308">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-309">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-309">**Option values**</span></span> | <span data-ttu-id="03c0b-310">`true` — отступ в конструкции `switch` case</span><span class="sxs-lookup"><span data-stu-id="03c0b-310">`true` - Indent `switch` case contents</span></span><br /><br /><span data-ttu-id="03c0b-311">`false` — не использовать отступ в конструкции `switch` case</span><span class="sxs-lookup"><span data-stu-id="03c0b-311">`false` - Do not indent `switch` case contents</span></span> |

- <span data-ttu-id="03c0b-312">Когда для этого правила задано значение **true**, i.</span><span class="sxs-lookup"><span data-stu-id="03c0b-312">When this rule is set to **true**, i.</span></span>
- <span data-ttu-id="03c0b-313">Когда для этого правила задано значение **false**, d.</span><span class="sxs-lookup"><span data-stu-id="03c0b-313">When this rule is set to **false**, d.</span></span>

<span data-ttu-id="03c0b-314">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-314">Code examples:</span></span>

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

#### <a name="csharp_indent_switch_labels"></a><span data-ttu-id="03c0b-315">csharp\_indent\_switch_labels</span><span class="sxs-lookup"><span data-stu-id="03c0b-315">csharp\_indent\_switch_labels</span></span>

|<span data-ttu-id="03c0b-316">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-316">Property</span></span>|<span data-ttu-id="03c0b-317">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-317">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-318">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-318">**Option name**</span></span> | <span data-ttu-id="03c0b-319">csharp_indent_switch_labels</span><span class="sxs-lookup"><span data-stu-id="03c0b-319">csharp_indent_switch_labels</span></span> |
| <span data-ttu-id="03c0b-320">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-320">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-321">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-321">C#</span></span> |
| <span data-ttu-id="03c0b-322">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-322">**Introduced version**</span></span> | <span data-ttu-id="03c0b-323">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-323">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-324">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-324">**Option values**</span></span> | <span data-ttu-id="03c0b-325">`true` — отступ для меток `switch`.</span><span class="sxs-lookup"><span data-stu-id="03c0b-325">`true` - Indent `switch` labels</span></span><br /><br /><span data-ttu-id="03c0b-326">`false` — не использовать отступ для меток `switch`.</span><span class="sxs-lookup"><span data-stu-id="03c0b-326">`false` - Do not indent `switch` labels</span></span> |

<span data-ttu-id="03c0b-327">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-327">Code examples:</span></span>

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

#### <a name="csharp_indent_labels"></a><span data-ttu-id="03c0b-328">csharp\_indent_labels</span><span class="sxs-lookup"><span data-stu-id="03c0b-328">csharp\_indent_labels</span></span>

|<span data-ttu-id="03c0b-329">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-329">Property</span></span>|<span data-ttu-id="03c0b-330">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-330">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-331">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-331">**Option name**</span></span> | <span data-ttu-id="03c0b-332">csharp_indent_labels</span><span class="sxs-lookup"><span data-stu-id="03c0b-332">csharp_indent_labels</span></span> |
| <span data-ttu-id="03c0b-333">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-333">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-334">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-334">C#</span></span> |
| <span data-ttu-id="03c0b-335">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-335">**Introduced version**</span></span> | <span data-ttu-id="03c0b-336">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-336">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-337">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-337">**Option values**</span></span> | <span data-ttu-id="03c0b-338">`flush_left` — метки размещаются в крайнем левом столбце.</span><span class="sxs-lookup"><span data-stu-id="03c0b-338">`flush_left` - Labels are placed at the leftmost column</span></span><br /><br /><span data-ttu-id="03c0b-339">`one_less_than_current` — метки размещаются на предыдущей позиции отступа относительно текущего контекста.</span><span class="sxs-lookup"><span data-stu-id="03c0b-339">`one_less_than_current` - Labels are placed at one less indent to the current context</span></span><br /><br /><span data-ttu-id="03c0b-340">`no_change` — метки размещаются на той же позиции отступа, что и текущий контекст.</span><span class="sxs-lookup"><span data-stu-id="03c0b-340">`no_change` - Labels are placed at the same indent as the current context</span></span> |

<span data-ttu-id="03c0b-341">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-341">Code examples:</span></span>

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

#### <a name="csharp_indent_block_contents"></a><span data-ttu-id="03c0b-342">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="03c0b-342">csharp_indent_block_contents</span></span>

|<span data-ttu-id="03c0b-343">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-343">Property</span></span>|<span data-ttu-id="03c0b-344">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-344">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-345">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-345">**Option name**</span></span> | <span data-ttu-id="03c0b-346">csharp_indent_block_contents</span><span class="sxs-lookup"><span data-stu-id="03c0b-346">csharp_indent_block_contents</span></span> |
| <span data-ttu-id="03c0b-347">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-347">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-348">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-348">C#</span></span> |
| <span data-ttu-id="03c0b-349">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-349">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="03c0b-350">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-350">Code examples:</span></span>

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

#### <a name="csharp_indent_braces"></a><span data-ttu-id="03c0b-351">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="03c0b-351">csharp_indent_braces</span></span>

|<span data-ttu-id="03c0b-352">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-352">Property</span></span>|<span data-ttu-id="03c0b-353">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-353">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-354">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-354">**Option name**</span></span> | <span data-ttu-id="03c0b-355">csharp_indent_braces</span><span class="sxs-lookup"><span data-stu-id="03c0b-355">csharp_indent_braces</span></span> |
| <span data-ttu-id="03c0b-356">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-356">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-357">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-357">C#</span></span> |
| <span data-ttu-id="03c0b-358">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-358">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="03c0b-359">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-359">Code examples:</span></span>

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

#### <a name="csharp_indent_case_contents_when_block"></a><span data-ttu-id="03c0b-360">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="03c0b-360">csharp_indent_case_contents_when_block</span></span>

|<span data-ttu-id="03c0b-361">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-361">Property</span></span>|<span data-ttu-id="03c0b-362">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-362">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-363">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-363">**Option name**</span></span> | <span data-ttu-id="03c0b-364">csharp_indent_case_contents_when_block</span><span class="sxs-lookup"><span data-stu-id="03c0b-364">csharp_indent_case_contents_when_block</span></span> |
| <span data-ttu-id="03c0b-365">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-365">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-366">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-366">C#</span></span> |
| <span data-ttu-id="03c0b-367">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-367">**Option values**</span></span> | `true` - <br /><br />`false` -  |

<span data-ttu-id="03c0b-368">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-368">Code examples:</span></span>

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

### <a name="spacing-options"></a><span data-ttu-id="03c0b-369">Параметры интервалов</span><span class="sxs-lookup"><span data-stu-id="03c0b-369">Spacing options</span></span>

<span data-ttu-id="03c0b-370">Эти правила форматирования относятся к использованию пробелов для форматирования кода.</span><span class="sxs-lookup"><span data-stu-id="03c0b-370">These formatting rules concern the use of space characters to format code.</span></span>

<span data-ttu-id="03c0b-371">Пример файла *EDITORCONFIG*:</span><span class="sxs-lookup"><span data-stu-id="03c0b-371">Example *.editorconfig* file:</span></span>

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

#### <a name="csharp_space_after_cast"></a><span data-ttu-id="03c0b-372">csharp\_space\_after_cast</span><span class="sxs-lookup"><span data-stu-id="03c0b-372">csharp\_space\_after_cast</span></span>

|<span data-ttu-id="03c0b-373">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-373">Property</span></span>|<span data-ttu-id="03c0b-374">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-374">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-375">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-375">**Option name**</span></span> | <span data-ttu-id="03c0b-376">csharp_space_after_cast</span><span class="sxs-lookup"><span data-stu-id="03c0b-376">csharp_space_after_cast</span></span> |
| <span data-ttu-id="03c0b-377">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-377">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-378">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-378">C#</span></span> |
| <span data-ttu-id="03c0b-379">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-379">**Introduced version**</span></span> | <span data-ttu-id="03c0b-380">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-380">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-381">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-381">**Option values**</span></span> | <span data-ttu-id="03c0b-382">`true` — разместить пробел между типом и значением в приведении</span><span class="sxs-lookup"><span data-stu-id="03c0b-382">`true` - Place a space character between a cast and the value</span></span><br /><br /><span data-ttu-id="03c0b-383">`false` — удалить пробел между типом и значением в приведении</span><span class="sxs-lookup"><span data-stu-id="03c0b-383">`false` - Remove space between the cast and the value</span></span> |

<span data-ttu-id="03c0b-384">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-384">Code examples:</span></span>

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a><span data-ttu-id="03c0b-385">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="03c0b-385">csharp_space_after_keywords_in_control_flow_statements</span></span>

|<span data-ttu-id="03c0b-386">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-386">Property</span></span>|<span data-ttu-id="03c0b-387">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-387">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-388">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-388">**Option name**</span></span> | <span data-ttu-id="03c0b-389">csharp_space_after_keywords_in_control_flow_statements</span><span class="sxs-lookup"><span data-stu-id="03c0b-389">csharp_space_after_keywords_in_control_flow_statements</span></span> |
| <span data-ttu-id="03c0b-390">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-390">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-391">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-391">C#</span></span> |
| <span data-ttu-id="03c0b-392">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-392">**Introduced version**</span></span> | <span data-ttu-id="03c0b-393">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-393">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-394">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-394">**Option values**</span></span> | <span data-ttu-id="03c0b-395">`true` — поместить пробел после ключевого слова в операторе потока управления, например цикле `for`</span><span class="sxs-lookup"><span data-stu-id="03c0b-395">`true` - Place a space character after a keyword in a control flow statement such as a `for` loop</span></span><br /><br /><span data-ttu-id="03c0b-396">`false` — удалить пробел после ключевого слова в операторе потока управления, например цикле `for`</span><span class="sxs-lookup"><span data-stu-id="03c0b-396">`false` - Remove space after a keyword in a control flow statement such as a `for` loop</span></span> |

<span data-ttu-id="03c0b-397">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-397">Code examples:</span></span>

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a><span data-ttu-id="03c0b-398">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-398">csharp_space_between_parentheses</span></span>

|<span data-ttu-id="03c0b-399">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-399">Property</span></span>|<span data-ttu-id="03c0b-400">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-400">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-401">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-401">**Option name**</span></span> | <span data-ttu-id="03c0b-402">csharp_space_between_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-402">csharp_space_between_parentheses</span></span> |
| <span data-ttu-id="03c0b-403">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-403">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-404">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-404">C#</span></span> |
| <span data-ttu-id="03c0b-405">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-405">**Introduced version**</span></span> | <span data-ttu-id="03c0b-406">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-406">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-407">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-407">**Option values**</span></span> | <span data-ttu-id="03c0b-408">`control_flow_statements` — добавлять пробел между скобками для операторов потока управления.</span><span class="sxs-lookup"><span data-stu-id="03c0b-408">`control_flow_statements` - Place space between parentheses of control flow statements</span></span><br /><br /><span data-ttu-id="03c0b-409">`expressions` — добавлять пробел между скобками для выражений.</span><span class="sxs-lookup"><span data-stu-id="03c0b-409">`expressions` - Place space between parentheses of expressions</span></span><br /><br /><span data-ttu-id="03c0b-410">`type_casts` — размещать пробел между скобками в приведениях типов.</span><span class="sxs-lookup"><span data-stu-id="03c0b-410">`type_casts` - Place space between parentheses in type casts</span></span> |

<span data-ttu-id="03c0b-411">Если пропустить это правило или использовать значение, отличное от `control_flow_statements`, `expressions` или `type_casts`, этот параметр не применяется.</span><span class="sxs-lookup"><span data-stu-id="03c0b-411">If you omit this rule or use a value other than `control_flow_statements`, `expressions`, or `type_casts`, the setting is not applied.</span></span>

<span data-ttu-id="03c0b-412">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-412">Code examples:</span></span>

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a><span data-ttu-id="03c0b-413">csharp\_space\_before\_colon\_in\_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="03c0b-413">csharp\_space\_before\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="03c0b-414">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-414">Property</span></span>|<span data-ttu-id="03c0b-415">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-415">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-416">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-416">**Option name**</span></span> | <span data-ttu-id="03c0b-417">csharp_space_before_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="03c0b-417">csharp_space_before_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="03c0b-418">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-418">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-419">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-419">C#</span></span> |
| <span data-ttu-id="03c0b-420">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-420">**Introduced version**</span></span> | <span data-ttu-id="03c0b-421">Visual Studio 2017 версии 15.7</span><span class="sxs-lookup"><span data-stu-id="03c0b-421">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="03c0b-422">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-422">**Option values**</span></span> | <span data-ttu-id="03c0b-423">`true` — поместить пробел перед двоеточием для баз или интерфейсов в объявлении типа</span><span class="sxs-lookup"><span data-stu-id="03c0b-423">`true` - Place a space character before the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="03c0b-424">`false` — удалить пробел перед двоеточием для баз или интерфейсов в объявлении типа</span><span class="sxs-lookup"><span data-stu-id="03c0b-424">`false` - Remove space before the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="03c0b-425">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-425">Code examples:</span></span>

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

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a><span data-ttu-id="03c0b-426">csharp\_space\_after\_colon\_in\_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="03c0b-426">csharp\_space\_after\_colon\_in\_inheritance_clause</span></span>

|<span data-ttu-id="03c0b-427">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-427">Property</span></span>|<span data-ttu-id="03c0b-428">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-428">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-429">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-429">**Option name**</span></span> | <span data-ttu-id="03c0b-430">csharp_space_after_colon_in_inheritance_clause</span><span class="sxs-lookup"><span data-stu-id="03c0b-430">csharp_space_after_colon_in_inheritance_clause</span></span> |
| <span data-ttu-id="03c0b-431">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-431">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-432">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-432">C#</span></span> |
| <span data-ttu-id="03c0b-433">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-433">**Introduced version**</span></span> | <span data-ttu-id="03c0b-434">Visual Studio 2017 версии 15.7</span><span class="sxs-lookup"><span data-stu-id="03c0b-434">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="03c0b-435">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-435">**Option values**</span></span> | <span data-ttu-id="03c0b-436">`true` — поместить пробел после двоеточия для баз или интерфейсов в объявлении типа</span><span class="sxs-lookup"><span data-stu-id="03c0b-436">`true` - Place a space character after the colon for bases or interfaces in a type declaration</span></span><br /><br /><span data-ttu-id="03c0b-437">`false` — удалить пробел после двоеточия для баз или интерфейсов в объявлении типа</span><span class="sxs-lookup"><span data-stu-id="03c0b-437">`false` - Remove space after the colon for bases or interfaces in a type declaration</span></span> |

<span data-ttu-id="03c0b-438">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-438">Code examples:</span></span>

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

#### <a name="csharp_space_around_binary_operators"></a><span data-ttu-id="03c0b-439">csharp\_space\_around\_binary_operators</span><span class="sxs-lookup"><span data-stu-id="03c0b-439">csharp\_space\_around\_binary_operators</span></span>

|<span data-ttu-id="03c0b-440">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-440">Property</span></span>|<span data-ttu-id="03c0b-441">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-441">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-442">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-442">**Option name**</span></span> | <span data-ttu-id="03c0b-443">csharp_space_around_binary_operators</span><span class="sxs-lookup"><span data-stu-id="03c0b-443">csharp_space_around_binary_operators</span></span> |
| <span data-ttu-id="03c0b-444">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-444">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-445">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-445">C#</span></span> |
| <span data-ttu-id="03c0b-446">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-446">**Introduced version**</span></span> | <span data-ttu-id="03c0b-447">Visual Studio 2017 версии 15.7</span><span class="sxs-lookup"><span data-stu-id="03c0b-447">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="03c0b-448">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-448">**Option values**</span></span> | <span data-ttu-id="03c0b-449">`before_and_after` — вставлять пробел до и после бинарных операторов.</span><span class="sxs-lookup"><span data-stu-id="03c0b-449">`before_and_after` - Insert space before and after the binary operator</span></span><br /><br /><span data-ttu-id="03c0b-450">`none` — удалять пробелы до и после бинарных операторов.</span><span class="sxs-lookup"><span data-stu-id="03c0b-450">`none` - Remove spaces before and after the binary operator</span></span><br /><br /><span data-ttu-id="03c0b-451">`ignore` — игнорировать пробелы вокруг бинарных операторов.</span><span class="sxs-lookup"><span data-stu-id="03c0b-451">`ignore` - Ignore spaces around binary operators</span></span> |

<span data-ttu-id="03c0b-452">Если пропустить это правило или использовать значение, отличное от `before_and_after`, `none` или `ignore`, этот параметр не применяется.</span><span class="sxs-lookup"><span data-stu-id="03c0b-452">If you omit this rule, or use a value other than `before_and_after`, `none`, or `ignore`, the setting is not applied.</span></span>

<span data-ttu-id="03c0b-453">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-453">Code examples:</span></span>

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a><span data-ttu-id="03c0b-454">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-454">csharp_space_between_method_declaration_parameter_list_parentheses</span></span>

|<span data-ttu-id="03c0b-455">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-455">Property</span></span>|<span data-ttu-id="03c0b-456">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-456">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-457">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-457">**Option name**</span></span> | <span data-ttu-id="03c0b-458">csharp_space_between_method_declaration_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-458">csharp_space_between_method_declaration_parameter_list_parentheses</span></span> |
| <span data-ttu-id="03c0b-459">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-459">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-460">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-460">C#</span></span> |
| <span data-ttu-id="03c0b-461">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-461">**Introduced version**</span></span> | <span data-ttu-id="03c0b-462">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-462">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-463">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-463">**Option values**</span></span> | <span data-ttu-id="03c0b-464">`true` — размещать пробел после открывающей скобки и перед закрывающей скобкой в списке параметров объявления метода.</span><span class="sxs-lookup"><span data-stu-id="03c0b-464">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span><br /><br /><span data-ttu-id="03c0b-465">`false` — удалить пробел после открывающей скобки и перед закрывающей скобкой в списке параметров объявления метода</span><span class="sxs-lookup"><span data-stu-id="03c0b-465">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method declaration parameter list</span></span> |

<span data-ttu-id="03c0b-466">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-466">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a><span data-ttu-id="03c0b-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-467">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="03c0b-468">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-468">Property</span></span>|<span data-ttu-id="03c0b-469">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-469">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-470">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-470">**Option name**</span></span> | <span data-ttu-id="03c0b-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-471">csharp_space_between_method_declaration_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="03c0b-472">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-472">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-473">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-473">C#</span></span> |
| <span data-ttu-id="03c0b-474">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-474">**Introduced version**</span></span> | <span data-ttu-id="03c0b-475">Visual Studio 2017 версии 15.7</span><span class="sxs-lookup"><span data-stu-id="03c0b-475">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="03c0b-476">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-476">**Option values**</span></span> | <span data-ttu-id="03c0b-477">`true` — вставлять пробел между скобками пустого списка параметров при объявлении метода.</span><span class="sxs-lookup"><span data-stu-id="03c0b-477">`true` - Insert space within empty parameter list parentheses for a method declaration</span></span><br /><br /><span data-ttu-id="03c0b-478">`false` — удалять пробел между скобками пустого списка параметров при объявлении метода.</span><span class="sxs-lookup"><span data-stu-id="03c0b-478">`false` - Remove space within empty parameter list parentheses for a method declaration</span></span> |

<span data-ttu-id="03c0b-479">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-479">Code examples:</span></span>

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

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a><span data-ttu-id="03c0b-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="03c0b-480">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span>

|<span data-ttu-id="03c0b-481">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-481">Property</span></span>|<span data-ttu-id="03c0b-482">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-482">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-483">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-483">**Option name**</span></span> | <span data-ttu-id="03c0b-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span><span class="sxs-lookup"><span data-stu-id="03c0b-484">csharp_space_between_method_declaration_name_and_open_parenthesis</span></span> |
| <span data-ttu-id="03c0b-485">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-485">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-486">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-486">C#</span></span> |
| <span data-ttu-id="03c0b-487">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-487">**Option values**</span></span> | <span data-ttu-id="03c0b-488">`true` — поместить пробел между именем метода и открывающей круглой скобкой в объявлении метода</span><span class="sxs-lookup"><span data-stu-id="03c0b-488">`true` - Place a space character between the method name and opening parenthesis in the method declaration</span></span><br /><br /><span data-ttu-id="03c0b-489">`false` — удалить пробелы между именем метода и открывающей круглой скобкой в объявлении метода</span><span class="sxs-lookup"><span data-stu-id="03c0b-489">`false` - Remove space characters between the method name and opening parenthesis in the method declaration</span></span> |

<span data-ttu-id="03c0b-490">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-490">Code examples:</span></span>

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a><span data-ttu-id="03c0b-491">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-491">csharp_space_between_method_call_parameter_list_parentheses</span></span>

|<span data-ttu-id="03c0b-492">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-492">Property</span></span>|<span data-ttu-id="03c0b-493">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-493">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-494">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-494">**Option name**</span></span> | <span data-ttu-id="03c0b-495">csharp_space_between_method_call_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-495">csharp_space_between_method_call_parameter_list_parentheses</span></span> |
| <span data-ttu-id="03c0b-496">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-496">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-497">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-497">C#</span></span> |
| <span data-ttu-id="03c0b-498">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-498">**Introduced version**</span></span> | <span data-ttu-id="03c0b-499">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-499">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-500">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-500">**Option values**</span></span> | <span data-ttu-id="03c0b-501">`true` — размещать пробел после открывающей скобки и перед закрывающей скобкой в вызове метода.</span><span class="sxs-lookup"><span data-stu-id="03c0b-501">`true` - Place a space character after the opening parenthesis and before the closing parenthesis of a method call</span></span><br /><br /><span data-ttu-id="03c0b-502">`false` — удалять пробел после открывающей скобки и перед закрывающей скобкой в вызове метода</span><span class="sxs-lookup"><span data-stu-id="03c0b-502">`false` - Remove space characters after the opening parenthesis and before the closing parenthesis of a method call</span></span> |

<span data-ttu-id="03c0b-503">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-503">Code examples:</span></span>

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a><span data-ttu-id="03c0b-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-504">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span>

|<span data-ttu-id="03c0b-505">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-505">Property</span></span>|<span data-ttu-id="03c0b-506">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-506">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-507">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-507">**Option name**</span></span> | <span data-ttu-id="03c0b-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span><span class="sxs-lookup"><span data-stu-id="03c0b-508">csharp_space_between_method_call_empty_parameter_list_parentheses</span></span> |
| <span data-ttu-id="03c0b-509">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-509">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-510">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-510">C#</span></span> |
| <span data-ttu-id="03c0b-511">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-511">**Introduced version**</span></span> | <span data-ttu-id="03c0b-512">Visual Studio 2017 версии 15.7</span><span class="sxs-lookup"><span data-stu-id="03c0b-512">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="03c0b-513">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-513">**Option values**</span></span> | <span data-ttu-id="03c0b-514">`true` — вставлять пробел между скобками в пустом списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="03c0b-514">`true` - Insert space within empty argument list parentheses</span></span><br /><br /><span data-ttu-id="03c0b-515">`false` — удалять пробел между скобками в пустом списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="03c0b-515">`false` - Remove space within empty argument list parentheses</span></span> |

<span data-ttu-id="03c0b-516">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-516">Code examples:</span></span>

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

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a><span data-ttu-id="03c0b-517">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="03c0b-517">csharp_space_between_method_call_name_and_opening_parenthesis</span></span>

|<span data-ttu-id="03c0b-518">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-518">Property</span></span>|<span data-ttu-id="03c0b-519">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-519">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-520">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-520">**Option name**</span></span> | <span data-ttu-id="03c0b-521">csharp_space_between_method_call_name_and_opening_parenthesis</span><span class="sxs-lookup"><span data-stu-id="03c0b-521">csharp_space_between_method_call_name_and_opening_parenthesis</span></span> |
| <span data-ttu-id="03c0b-522">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-522">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-523">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-523">C#</span></span> |
| <span data-ttu-id="03c0b-524">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-524">**Introduced version**</span></span> | <span data-ttu-id="03c0b-525">Visual Studio 2017 версии 15.7</span><span class="sxs-lookup"><span data-stu-id="03c0b-525">Visual Studio 2017 version 15.7</span></span> |
| <span data-ttu-id="03c0b-526">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-526">**Option values**</span></span> | <span data-ttu-id="03c0b-527">`true` — вставлять пробел между именем вызываемого метода и открывающей скобкой.</span><span class="sxs-lookup"><span data-stu-id="03c0b-527">`true` - Insert space between method call name and opening parenthesis</span></span><br /><br /><span data-ttu-id="03c0b-528">`false` — удалять пробел между именем вызываемого метода и открывающей скобкой.</span><span class="sxs-lookup"><span data-stu-id="03c0b-528">`false` - Remove space between method call name and opening parenthesis</span></span> |

<span data-ttu-id="03c0b-529">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-529">Code examples:</span></span>

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

#### <a name="csharp_space_after_comma"></a><span data-ttu-id="03c0b-530">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="03c0b-530">csharp_space_after_comma</span></span>

|<span data-ttu-id="03c0b-531">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-531">Property</span></span>|<span data-ttu-id="03c0b-532">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-532">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-533">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-533">**Option name**</span></span> | <span data-ttu-id="03c0b-534">csharp_space_after_comma</span><span class="sxs-lookup"><span data-stu-id="03c0b-534">csharp_space_after_comma</span></span> |
| <span data-ttu-id="03c0b-535">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-535">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-536">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-536">C#</span></span> |
| <span data-ttu-id="03c0b-537">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-537">**Option values**</span></span> | <span data-ttu-id="03c0b-538">`true` — вставлять пробел после запятой.</span><span class="sxs-lookup"><span data-stu-id="03c0b-538">`true` - Insert space after a comma</span></span><br /><br /><span data-ttu-id="03c0b-539">`false` — удалять пробел после запятой.</span><span class="sxs-lookup"><span data-stu-id="03c0b-539">`false` - Remove space after a comma</span></span> |

<span data-ttu-id="03c0b-540">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-540">Code examples:</span></span>

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a><span data-ttu-id="03c0b-541">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="03c0b-541">csharp_space_before_comma</span></span>

|<span data-ttu-id="03c0b-542">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-542">Property</span></span>|<span data-ttu-id="03c0b-543">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-543">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-544">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-544">**Option name**</span></span> | <span data-ttu-id="03c0b-545">csharp_space_before_comma</span><span class="sxs-lookup"><span data-stu-id="03c0b-545">csharp_space_before_comma</span></span> |
| <span data-ttu-id="03c0b-546">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-546">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-547">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-547">C#</span></span> |
| <span data-ttu-id="03c0b-548">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-548">**Option values**</span></span> | <span data-ttu-id="03c0b-549">`true` — вставлять пробел перед запятой</span><span class="sxs-lookup"><span data-stu-id="03c0b-549">`true` - Insert space before a comma</span></span><br /><br /><span data-ttu-id="03c0b-550">`false` — удалять пробел перед запятой</span><span class="sxs-lookup"><span data-stu-id="03c0b-550">`false` - Remove space before a comma</span></span> |

<span data-ttu-id="03c0b-551">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-551">Code examples:</span></span>

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a><span data-ttu-id="03c0b-552">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="03c0b-552">csharp_space_after_dot</span></span>

|<span data-ttu-id="03c0b-553">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-553">Property</span></span>|<span data-ttu-id="03c0b-554">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-554">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-555">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-555">**Option name**</span></span> | <span data-ttu-id="03c0b-556">csharp_space_after_dot</span><span class="sxs-lookup"><span data-stu-id="03c0b-556">csharp_space_after_dot</span></span> |
| <span data-ttu-id="03c0b-557">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-557">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-558">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-558">C#</span></span> |
| <span data-ttu-id="03c0b-559">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-559">**Option values**</span></span> | <span data-ttu-id="03c0b-560">`true` — вставлять пробел после точки.</span><span class="sxs-lookup"><span data-stu-id="03c0b-560">`true` - Insert space after a dot</span></span><br /><br /><span data-ttu-id="03c0b-561">`false` — удалять пробел после точки.</span><span class="sxs-lookup"><span data-stu-id="03c0b-561">`false` - Remove space after a dot</span></span> |

<span data-ttu-id="03c0b-562">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-562">Code examples:</span></span>

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a><span data-ttu-id="03c0b-563">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="03c0b-563">csharp_space_before_dot</span></span>

|<span data-ttu-id="03c0b-564">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-564">Property</span></span>|<span data-ttu-id="03c0b-565">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-565">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-566">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-566">**Option name**</span></span> | <span data-ttu-id="03c0b-567">csharp_space_before_dot</span><span class="sxs-lookup"><span data-stu-id="03c0b-567">csharp_space_before_dot</span></span> |
| <span data-ttu-id="03c0b-568">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-568">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-569">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-569">C#</span></span> |
| <span data-ttu-id="03c0b-570">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-570">**Option values**</span></span> | <span data-ttu-id="03c0b-571">`true` — вставлять пробел перед точкой</span><span class="sxs-lookup"><span data-stu-id="03c0b-571">`true` - Insert space before a dot</span></span> <br /><br /><span data-ttu-id="03c0b-572">`false` — удалять пробел перед точкой</span><span class="sxs-lookup"><span data-stu-id="03c0b-572">`false` - Remove space before a dot</span></span> |

<span data-ttu-id="03c0b-573">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-573">Code examples:</span></span>

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a><span data-ttu-id="03c0b-574">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="03c0b-574">csharp_space_after_semicolon_in_for_statement</span></span>

|<span data-ttu-id="03c0b-575">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-575">Property</span></span>|<span data-ttu-id="03c0b-576">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-576">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-577">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-577">**Option name**</span></span> | <span data-ttu-id="03c0b-578">csharp_space_after_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="03c0b-578">csharp_space_after_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="03c0b-579">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-579">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-580">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-580">C#</span></span> |
| <span data-ttu-id="03c0b-581">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-581">**Option values**</span></span> | <span data-ttu-id="03c0b-582">`true` — вставлять пробел после каждой точки с запятой в операторах `for`</span><span class="sxs-lookup"><span data-stu-id="03c0b-582">`true` - Insert space after each semicolon in a `for` statement</span></span><br /><br /><span data-ttu-id="03c0b-583">`false` — удалять пробел после каждой точки с запятой в операторах `for`</span><span class="sxs-lookup"><span data-stu-id="03c0b-583">`false` - Remove space after each semicolon in a `for` statement</span></span> |

<span data-ttu-id="03c0b-584">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-584">Code examples:</span></span>

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharp_space_before_semicolon_in_for_statement"></a><span data-ttu-id="03c0b-585">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="03c0b-585">csharp_space_before_semicolon_in_for_statement</span></span>

|<span data-ttu-id="03c0b-586">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-586">Property</span></span>|<span data-ttu-id="03c0b-587">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-587">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-588">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-588">**Option name**</span></span> | <span data-ttu-id="03c0b-589">csharp_space_before_semicolon_in_for_statement</span><span class="sxs-lookup"><span data-stu-id="03c0b-589">csharp_space_before_semicolon_in_for_statement</span></span> |
| <span data-ttu-id="03c0b-590">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-590">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-591">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-591">C#</span></span> |
| <span data-ttu-id="03c0b-592">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-592">**Option values**</span></span> | <span data-ttu-id="03c0b-593">`true` — вставлять пробел перед каждой точкой с запятой в операторах `for`</span><span class="sxs-lookup"><span data-stu-id="03c0b-593">`true` - Insert space before each semicolon in a `for` statement</span></span> <br /><br /><span data-ttu-id="03c0b-594">`false` — удалять пробел перед каждой точкой с запятой в операторах `for`</span><span class="sxs-lookup"><span data-stu-id="03c0b-594">`false` - Remove space before each semicolon in a `for` statement</span></span> |

<span data-ttu-id="03c0b-595">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-595">Code examples:</span></span>

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a><span data-ttu-id="03c0b-596">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="03c0b-596">csharp_space_around_declaration_statements</span></span>

|<span data-ttu-id="03c0b-597">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-597">Property</span></span>|<span data-ttu-id="03c0b-598">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-598">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-599">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-599">**Option name**</span></span> | <span data-ttu-id="03c0b-600">csharp_space_around_declaration_statements</span><span class="sxs-lookup"><span data-stu-id="03c0b-600">csharp_space_around_declaration_statements</span></span> |
| <span data-ttu-id="03c0b-601">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-601">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-602">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-602">C#</span></span> |
| <span data-ttu-id="03c0b-603">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-603">**Option values**</span></span> | <span data-ttu-id="03c0b-604">`ignore` — не удалять лишние пробелы в операторах объявления</span><span class="sxs-lookup"><span data-stu-id="03c0b-604">`ignore` - Don't remove extra space characters in declaration statements</span></span><br /><br /><span data-ttu-id="03c0b-605">`false` — удалять лишние пробелы в операторах объявления</span><span class="sxs-lookup"><span data-stu-id="03c0b-605">`false` - Remove extra space characters in declaration statements</span></span> |

<span data-ttu-id="03c0b-606">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-606">Code examples:</span></span>

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a><span data-ttu-id="03c0b-607">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="03c0b-607">csharp_space_before_open_square_brackets</span></span>

|<span data-ttu-id="03c0b-608">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-608">Property</span></span>|<span data-ttu-id="03c0b-609">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-609">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-610">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-610">**Option name**</span></span> | <span data-ttu-id="03c0b-611">csharp_space_before_open_square_brackets</span><span class="sxs-lookup"><span data-stu-id="03c0b-611">csharp_space_before_open_square_brackets</span></span> |
| <span data-ttu-id="03c0b-612">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-612">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-613">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-613">C#</span></span> |
| <span data-ttu-id="03c0b-614">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-614">**Option values**</span></span> | <span data-ttu-id="03c0b-615">`true` — вставлять пробел перед открывающей квадратной скобкой `[`</span><span class="sxs-lookup"><span data-stu-id="03c0b-615">`true` - Insert space before opening square brackets `[`</span></span> <br /><br /><span data-ttu-id="03c0b-616">`false` — удалять пробел перед открывающей квадратной скобкой `[`</span><span class="sxs-lookup"><span data-stu-id="03c0b-616">`false` - Remove space before opening square brackets `[`</span></span> |

<span data-ttu-id="03c0b-617">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-617">Code examples:</span></span>

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a><span data-ttu-id="03c0b-618">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="03c0b-618">csharp_space_between_empty_square_brackets</span></span>

|<span data-ttu-id="03c0b-619">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-619">Property</span></span>|<span data-ttu-id="03c0b-620">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-620">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-621">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-621">**Option name**</span></span> | <span data-ttu-id="03c0b-622">csharp_space_between_empty_square_brackets</span><span class="sxs-lookup"><span data-stu-id="03c0b-622">csharp_space_between_empty_square_brackets</span></span> |
| <span data-ttu-id="03c0b-623">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-623">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-624">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-624">C#</span></span> |
| <span data-ttu-id="03c0b-625">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-625">**Option values**</span></span> | <span data-ttu-id="03c0b-626">`true` — вставлять пробел перед пустыми квадратными скобками `[ ]`</span><span class="sxs-lookup"><span data-stu-id="03c0b-626">`true` - Insert space between empty square brackets `[ ]`</span></span> <br /><br /><span data-ttu-id="03c0b-627">`false` — удалять пробел перед пустыми квадратными скобками `[]`</span><span class="sxs-lookup"><span data-stu-id="03c0b-627">`false` - Remove space between empty square brackets `[]`</span></span> |

<span data-ttu-id="03c0b-628">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-628">Code examples:</span></span>

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a><span data-ttu-id="03c0b-629">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="03c0b-629">csharp_space_between_square_brackets</span></span>

|<span data-ttu-id="03c0b-630">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-630">Property</span></span>|<span data-ttu-id="03c0b-631">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-631">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-632">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-632">**Option name**</span></span> | <span data-ttu-id="03c0b-633">csharp_space_between_square_brackets</span><span class="sxs-lookup"><span data-stu-id="03c0b-633">csharp_space_between_square_brackets</span></span> |
| <span data-ttu-id="03c0b-634">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-634">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-635">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-635">C#</span></span> |
| <span data-ttu-id="03c0b-636">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-636">**Option values**</span></span> | <span data-ttu-id="03c0b-637">`true` — вставлять пробел в непустых квадратных скобках `[ 0 ]`</span><span class="sxs-lookup"><span data-stu-id="03c0b-637">`true` - Insert space characters in non-empty square brackets `[ 0 ]`</span></span> <br /><br /><span data-ttu-id="03c0b-638">`false` — удалять пробел в непустых квадратных скобках `[0]`</span><span class="sxs-lookup"><span data-stu-id="03c0b-638">`false` - Remove space characters in non-empty square brackets `[0]`</span></span> |

<span data-ttu-id="03c0b-639">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-639">Code examples:</span></span>

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a><span data-ttu-id="03c0b-640">Параметры переноса</span><span class="sxs-lookup"><span data-stu-id="03c0b-640">Wrap options</span></span>

<span data-ttu-id="03c0b-641">Эти правила форматирования определяют размещение операторов и блоков кода в одной или разных строках.</span><span class="sxs-lookup"><span data-stu-id="03c0b-641">These formatting rules concern the use of single lines versus separate lines for statements and code blocks.</span></span>

<span data-ttu-id="03c0b-642">Пример файла *EDITORCONFIG*:</span><span class="sxs-lookup"><span data-stu-id="03c0b-642">Example *.editorconfig* file:</span></span>

```ini
# CSharp formatting rules:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a><span data-ttu-id="03c0b-643">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="03c0b-643">csharp_preserve_single_line_statements</span></span>

|<span data-ttu-id="03c0b-644">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-644">Property</span></span>|<span data-ttu-id="03c0b-645">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-645">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-646">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-646">**Option name**</span></span> | <span data-ttu-id="03c0b-647">csharp_preserve_single_line_statements</span><span class="sxs-lookup"><span data-stu-id="03c0b-647">csharp_preserve_single_line_statements</span></span> |
| <span data-ttu-id="03c0b-648">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-648">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-649">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-649">C#</span></span> |
| <span data-ttu-id="03c0b-650">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-650">**Introduced version**</span></span> | <span data-ttu-id="03c0b-651">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-651">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-652">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-652">**Option values**</span></span> | <span data-ttu-id="03c0b-653">`true` — оставлять выражения и объявления элемента в одной строке.</span><span class="sxs-lookup"><span data-stu-id="03c0b-653">`true` - Leave statements and member declarations on the same line</span></span><br /><br /><span data-ttu-id="03c0b-654">`false` — оставлять выражения и объявления элемента в разных строках.</span><span class="sxs-lookup"><span data-stu-id="03c0b-654">`false` - Leave statements and member declarations on different lines</span></span> |

<span data-ttu-id="03c0b-655">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-655">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a><span data-ttu-id="03c0b-656">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="03c0b-656">csharp_preserve_single_line_blocks</span></span>

|<span data-ttu-id="03c0b-657">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-657">Property</span></span>|<span data-ttu-id="03c0b-658">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-658">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-659">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-659">**Option name**</span></span> | <span data-ttu-id="03c0b-660">csharp_preserve_single_line_blocks</span><span class="sxs-lookup"><span data-stu-id="03c0b-660">csharp_preserve_single_line_blocks</span></span> |
| <span data-ttu-id="03c0b-661">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-661">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-662">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-662">C#</span></span> |
| <span data-ttu-id="03c0b-663">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-663">**Introduced version**</span></span> | <span data-ttu-id="03c0b-664">Visual Studio 2017 версия 15.3</span><span class="sxs-lookup"><span data-stu-id="03c0b-664">Visual Studio 2017 version 15.3</span></span> |
| <span data-ttu-id="03c0b-665">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-665">**Option values**</span></span> | <span data-ttu-id="03c0b-666">`true` — оставлять блок кода в одной строке.</span><span class="sxs-lookup"><span data-stu-id="03c0b-666">`true` - Leave code block on single line</span></span><br /><br /><span data-ttu-id="03c0b-667">`false` — оставлять блок кода в разных строках.</span><span class="sxs-lookup"><span data-stu-id="03c0b-667">`false` - Leave code block on separate lines</span></span> |

<span data-ttu-id="03c0b-668">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-668">Code examples:</span></span>

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

### <a name="using-directive-options"></a><span data-ttu-id="03c0b-669">Параметры директивы using</span><span class="sxs-lookup"><span data-stu-id="03c0b-669">Using directive options</span></span>

<span data-ttu-id="03c0b-670">Это правило форматирования относится к использованию директив using, размещаемых внутри и вне пространства имен.</span><span class="sxs-lookup"><span data-stu-id="03c0b-670">This formatting rule concerns the use of using directives being placed inside versus outside a namespace.</span></span>

<span data-ttu-id="03c0b-671">Пример файла *EDITORCONFIG*:</span><span class="sxs-lookup"><span data-stu-id="03c0b-671">Example *.editorconfig* file:</span></span>

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a><span data-ttu-id="03c0b-672">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="03c0b-672">csharp_using_directive_placement</span></span>

|<span data-ttu-id="03c0b-673">Свойство.</span><span class="sxs-lookup"><span data-stu-id="03c0b-673">Property</span></span>|<span data-ttu-id="03c0b-674">Значение</span><span class="sxs-lookup"><span data-stu-id="03c0b-674">Value</span></span>|
|-|-|
| <span data-ttu-id="03c0b-675">**Имя параметра**</span><span class="sxs-lookup"><span data-stu-id="03c0b-675">**Option name**</span></span> | <span data-ttu-id="03c0b-676">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="03c0b-676">csharp_using_directive_placement</span></span> |
| <span data-ttu-id="03c0b-677">**Применимые языки**</span><span class="sxs-lookup"><span data-stu-id="03c0b-677">**Applicable languages**</span></span> | <span data-ttu-id="03c0b-678">C#</span><span class="sxs-lookup"><span data-stu-id="03c0b-678">C#</span></span> |
| <span data-ttu-id="03c0b-679">**Представленные версии**</span><span class="sxs-lookup"><span data-stu-id="03c0b-679">**Introduced version**</span></span> | <span data-ttu-id="03c0b-680">Visual Studio 2019 версии 16.1</span><span class="sxs-lookup"><span data-stu-id="03c0b-680">Visual Studio 2019 version 16.1</span></span> |
| <span data-ttu-id="03c0b-681">**Значения параметров**</span><span class="sxs-lookup"><span data-stu-id="03c0b-681">**Option values**</span></span> | <span data-ttu-id="03c0b-682">`outside_namespace` — размещать директивы using вне пространства имен</span><span class="sxs-lookup"><span data-stu-id="03c0b-682">`outside_namespace` - Leave using directives outside namespace</span></span><br /><br /><span data-ttu-id="03c0b-683">`inside_namespace` — размещать директивы using внутри пространства имен</span><span class="sxs-lookup"><span data-stu-id="03c0b-683">`inside_namespace` - Leave using directives inside namespace</span></span> |

<span data-ttu-id="03c0b-684">Примеры кода:</span><span class="sxs-lookup"><span data-stu-id="03c0b-684">Code examples:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="03c0b-685">См. также</span><span class="sxs-lookup"><span data-stu-id="03c0b-685">See also</span></span>

- [<span data-ttu-id="03c0b-686">Правила языка</span><span class="sxs-lookup"><span data-stu-id="03c0b-686">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="03c0b-687">Правила именования</span><span class="sxs-lookup"><span data-stu-id="03c0b-687">Naming rules</span></span>](naming-rules.md)
- [<span data-ttu-id="03c0b-688">Справочник по правилам стиля кода .NET</span><span class="sxs-lookup"><span data-stu-id="03c0b-688">.NET code style rules reference</span></span>](index.md)
