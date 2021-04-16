---
title: Правила языка для стиля кода
description: Сведения о различных правилах стиля кода для использования языковых конструкций C# и Visual Basic.
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
- language rules
- EditorConfig language conventions
ms.openlocfilehash: 2aa2261534363f1da6a2109f092e08d210ebd915
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "98957979"
---
# <a name="language-rules"></a><span data-ttu-id="43213-103">Правила языка</span><span class="sxs-lookup"><span data-stu-id="43213-103">Language rules</span></span>

<span data-ttu-id="43213-104">Правила языка для стиля кода влияют на использование различных конструкций языков программирования .NET, например модификаторов и круглых скобок.</span><span class="sxs-lookup"><span data-stu-id="43213-104">Code style language rules affect how various constructs of .NET programming languages, for example, modifiers and parentheses, are used.</span></span> <span data-ttu-id="43213-105">Эти правила делятся на следующие категории:</span><span class="sxs-lookup"><span data-stu-id="43213-105">The rules fall into the following categories:</span></span>

- <span data-ttu-id="43213-106">[Правила стиля .NET](#net-style-rules) в равной мере применяются к C# и Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="43213-106">[.NET style rules](#net-style-rules): Rules that apply to both C# and Visual Basic.</span></span> <span data-ttu-id="43213-107">Имена параметров EditorConfig для этих правил начинаются с префикса `dotnet_style_`.</span><span class="sxs-lookup"><span data-stu-id="43213-107">The EditorConfig option names for these rules start with `dotnet_style_` prefix.</span></span>
- <span data-ttu-id="43213-108">[Правила стиля C#](#c-style-rules) применяются только для языка C#.</span><span class="sxs-lookup"><span data-stu-id="43213-108">[C# style rules](#c-style-rules): Rules that are specific to C# language only.</span></span> <span data-ttu-id="43213-109">Имена параметров EditorConfig для этих правил начинаются с префикса `csharp_style_`.</span><span class="sxs-lookup"><span data-stu-id="43213-109">The EditorConfig option names for these rules start with `csharp_style_` prefix.</span></span>
- <span data-ttu-id="43213-110">[Правила стиля Visual Basic](#visual-basic-style-rules) применяются только для языка Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="43213-110">[Visual Basic style rules](#visual-basic-style-rules): Rules that are specific to Visual Bsic language only.</span></span> <span data-ttu-id="43213-111">Имена параметров EditorConfig для этих правил начинаются с префикса `visual_basic_style_`.</span><span class="sxs-lookup"><span data-stu-id="43213-111">The EditorConfig option names for these rules start with `visual_basic_style_` prefix.</span></span>

## <a name="option-format"></a><span data-ttu-id="43213-112">Формат параметра</span><span class="sxs-lookup"><span data-stu-id="43213-112">Option format</span></span>

<span data-ttu-id="43213-113">Параметры для правил языка можно указывать в файле EditorConfig в следующем формате:</span><span class="sxs-lookup"><span data-stu-id="43213-113">Options for language rules can be specified in an EditorConfig file with the following format:</span></span>

<span data-ttu-id="43213-114">`option_name = value` (Visual Studio 2019 версии 16.9, предварительная версия 2 и более поздние версии)</span><span class="sxs-lookup"><span data-stu-id="43213-114">`option_name = value` (Visual Studio 2019 version 16.9 Preview 2 and later)</span></span>

<span data-ttu-id="43213-115">или</span><span class="sxs-lookup"><span data-stu-id="43213-115">or</span></span>

`option_name = value:severity`

- <span data-ttu-id="43213-116">**Значение**</span><span class="sxs-lookup"><span data-stu-id="43213-116">**Value**</span></span>

  <span data-ttu-id="43213-117">Для каждого правила языка укажите значение, которое определяет условия выбора соответствующего стиля.</span><span class="sxs-lookup"><span data-stu-id="43213-117">For each language rule, you specify a value that defines if or when to prefer the style.</span></span> <span data-ttu-id="43213-118">Многие правила принимают значение `true` (предпочитать этот стиль) или `false` (не предпочитать этот стиль).</span><span class="sxs-lookup"><span data-stu-id="43213-118">Many rules accept a value of `true` (prefer this style) or `false` (do not prefer this style).</span></span> <span data-ttu-id="43213-119">Другие правила принимают значения `when_on_single_line` или `never`.</span><span class="sxs-lookup"><span data-stu-id="43213-119">Other rules accept values such as `when_on_single_line` or `never`.</span></span>

- <span data-ttu-id="43213-120">**Уровень серьезности** (необязательно в Visual Studio 2019 версии 16.9, предварительная версия 2 и более поздние версии)</span><span class="sxs-lookup"><span data-stu-id="43213-120">**Severity** (optional in Visual Studio 2019 version 16.9 Preview 2 and later versions)</span></span>

  <span data-ttu-id="43213-121">Вторая часть правила определяет [уровень серьезности](../configuration-options.md#severity-level) правила.</span><span class="sxs-lookup"><span data-stu-id="43213-121">The second part of the rule specifies the [severity level](../configuration-options.md#severity-level) for the rule.</span></span> <span data-ttu-id="43213-122">Если параметр уровня серьезности задан таким образом, он учитывается только в таких средах IDE, как Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="43213-122">When specified in this way, the severity setting is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="43213-123">Он *не* учитывается во время сборки.</span><span class="sxs-lookup"><span data-stu-id="43213-123">It is *not* respected during build.</span></span>

  <span data-ttu-id="43213-124">Чтобы применить правила стиля кода во время сборки, задайте уровень серьезности с помощью синтаксиса конфигурации серьезности на основе идентификатора правила для анализаторов.</span><span class="sxs-lookup"><span data-stu-id="43213-124">To enforce code style rules at build time, set the severity by using the rule ID-based severity configuration syntax for analyzers instead.</span></span> <span data-ttu-id="43213-125">Синтаксис имеет вид `dotnet_diagnostic.<rule ID>.severity = <severity>`, например `dotnet_diagnostic.IDE0040.severity = silent`.</span><span class="sxs-lookup"><span data-stu-id="43213-125">The syntax takes the form `dotnet_diagnostic.<rule ID>.severity = <severity>`, for example, `dotnet_diagnostic.IDE0040.severity = silent`.</span></span> <span data-ttu-id="43213-126">Дополнительные сведения см. в разделе об [уровне серьезности](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="43213-126">For more information, see [severity level](../configuration-options.md#severity-level).</span></span>

> [!TIP]
>
> <span data-ttu-id="43213-127">Начиная с Visual Studio 2019 версии 16.3, в меню [Быстрые действия](/visualstudio/ide/quick-actions) можно настроить правила стиля кода после нарушения стиля.</span><span class="sxs-lookup"><span data-stu-id="43213-127">Starting in Visual Studio 2019 version 16.3, you can configure code style rules from the [Quick Actions](/visualstudio/ide/quick-actions) light bulb menu after a style violation occurs.</span></span> <span data-ttu-id="43213-128">Дополнительные сведения см. в разделе [Автоматическая настройка стилей кода в Visual Studio](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="43213-128">For more information, see [Automatically configure code styles in Visual Studio](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio).</span></span>

## <a name="net-style-rules"></a><span data-ttu-id="43213-129">Правила стиля .NET</span><span class="sxs-lookup"><span data-stu-id="43213-129">.NET style rules</span></span>

<span data-ttu-id="43213-130">Правила стилей в этом разделе относятся как к C#, так и к Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="43213-130">The style rules in this section are applicable to both C# and Visual Basic.</span></span>

- [<span data-ttu-id="43213-131">Квалификаторы "this." и "Me."</span><span class="sxs-lookup"><span data-stu-id="43213-131">'this.' and 'Me.' qualifiers</span></span>](ide0003-ide0009.md)
  - [<span data-ttu-id="43213-132">dotnet_style_qualification_for_field</span><span class="sxs-lookup"><span data-stu-id="43213-132">dotnet_style_qualification_for_field</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_field)
  - [<span data-ttu-id="43213-133">dotnet_style_qualification_for_property</span><span class="sxs-lookup"><span data-stu-id="43213-133">dotnet_style_qualification_for_property</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_property)
  - [<span data-ttu-id="43213-134">dotnet_style_qualification_for_method</span><span class="sxs-lookup"><span data-stu-id="43213-134">dotnet_style_qualification_for_method</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_method)
  - [<span data-ttu-id="43213-135">dotnet_style_qualification_for_event</span><span class="sxs-lookup"><span data-stu-id="43213-135">dotnet_style_qualification_for_event</span></span>](ide0003-ide0009.md#dotnet_style_qualification_for_event)
- [<span data-ttu-id="43213-136">Ключевые слова языка вместо имен типов .NET Framework для ссылок на типы</span><span class="sxs-lookup"><span data-stu-id="43213-136">Language keywords instead of framework type names for type references</span></span>](ide0049.md)
  - [<span data-ttu-id="43213-137">dotnet_style_predefined_type_for_locals_parameters_members</span><span class="sxs-lookup"><span data-stu-id="43213-137">dotnet_style_predefined_type_for_locals_parameters_members</span></span>](ide0049.md#dotnet_style_predefined_type_for_locals_parameters_members)
  - [<span data-ttu-id="43213-138">dotnet_style_predefined_type_for_member_access</span><span class="sxs-lookup"><span data-stu-id="43213-138">dotnet_style_predefined_type_for_member_access</span></span>](ide0049.md#dotnet_style_predefined_type_for_member_access)
- [<span data-ttu-id="43213-139">Предпочтения для модификаторов</span><span class="sxs-lookup"><span data-stu-id="43213-139">Modifier preferences</span></span>](modifier-preferences.md#net-modifier-preferences)
  - [<span data-ttu-id="43213-140">dotnet_style_require_accessibility_modifiers</span><span class="sxs-lookup"><span data-stu-id="43213-140">dotnet_style_require_accessibility_modifiers</span></span>](ide0040.md#dotnet_style_require_accessibility_modifiers)
  - [<span data-ttu-id="43213-141">csharp_preferred_modifier_order</span><span class="sxs-lookup"><span data-stu-id="43213-141">csharp_preferred_modifier_order</span></span>](ide0036.md#csharp_preferred_modifier_order)
  - [<span data-ttu-id="43213-142">visual_basic_preferred_modifier_order</span><span class="sxs-lookup"><span data-stu-id="43213-142">visual_basic_preferred_modifier_order</span></span>](ide0036.md#visual_basic_preferred_modifier_order)
  - [<span data-ttu-id="43213-143">dotnet_style_readonly_field</span><span class="sxs-lookup"><span data-stu-id="43213-143">dotnet_style_readonly_field</span></span>](ide0044.md#dotnet_style_readonly_field)
- [<span data-ttu-id="43213-144">Предпочтения относительно круглых скобок</span><span class="sxs-lookup"><span data-stu-id="43213-144">Parentheses preferences</span></span>](ide0047-ide0048.md)
  - [<span data-ttu-id="43213-145">dotnet_style_parentheses_in_arithmetic_binary_operators</span><span class="sxs-lookup"><span data-stu-id="43213-145">dotnet_style_parentheses_in_arithmetic_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_arithmetic_binary_operators)
  - [<span data-ttu-id="43213-146">dotnet_style_parentheses_in_relational_binary_operators</span><span class="sxs-lookup"><span data-stu-id="43213-146">dotnet_style_parentheses_in_relational_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_relational_binary_operators)
  - [<span data-ttu-id="43213-147">dotnet_style_parentheses_in_other_binary_operators</span><span class="sxs-lookup"><span data-stu-id="43213-147">dotnet_style_parentheses_in_other_binary_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_other_binary_operators)
  - [<span data-ttu-id="43213-148">dotnet_style_parentheses_in_other_operators</span><span class="sxs-lookup"><span data-stu-id="43213-148">dotnet_style_parentheses_in_other_operators</span></span>](ide0047-ide0048.md#dotnet_style_parentheses_in_other_operators)
- [<span data-ttu-id="43213-149">Настройки уровня выражений</span><span class="sxs-lookup"><span data-stu-id="43213-149">Expression-level preferences</span></span>](expression-level-preferences.md#net-expression-level-preferences)
  - [<span data-ttu-id="43213-150">dotnet_style_object_initializer</span><span class="sxs-lookup"><span data-stu-id="43213-150">dotnet_style_object_initializer</span></span>](ide0017.md#dotnet_style_object_initializer)
  - [<span data-ttu-id="43213-151">dotnet_style_collection_initializer</span><span class="sxs-lookup"><span data-stu-id="43213-151">dotnet_style_collection_initializer</span></span>](ide0028.md#dotnet_style_collection_initializer)
  - [<span data-ttu-id="43213-152">dotnet_style_explicit_tuple_names</span><span class="sxs-lookup"><span data-stu-id="43213-152">dotnet_style_explicit_tuple_names</span></span>](ide0033.md#dotnet_style_explicit_tuple_names)
  - [<span data-ttu-id="43213-153">dotnet_style_prefer_inferred_tuple_names</span><span class="sxs-lookup"><span data-stu-id="43213-153">dotnet_style_prefer_inferred_tuple_names</span></span>](ide0037.md#dotnet_style_prefer_inferred_tuple_names)
  - [<span data-ttu-id="43213-154">dotnet_style_prefer_inferred_anonymous_type_member_names</span><span class="sxs-lookup"><span data-stu-id="43213-154">dotnet_style_prefer_inferred_anonymous_type_member_names</span></span>](ide0037.md#dotnet_style_prefer_inferred_anonymous_type_member_names)
  - [<span data-ttu-id="43213-155">dotnet_style_prefer_auto_properties</span><span class="sxs-lookup"><span data-stu-id="43213-155">dotnet_style_prefer_auto_properties</span></span>](ide0032.md#dotnet_style_prefer_auto_properties)
  - [<span data-ttu-id="43213-156">dotnet_style_prefer_conditional_expression_over_assignment</span><span class="sxs-lookup"><span data-stu-id="43213-156">dotnet_style_prefer_conditional_expression_over_assignment</span></span>](ide0045.md#dotnet_style_prefer_conditional_expression_over_assignment)
  - [<span data-ttu-id="43213-157">dotnet_style_prefer_conditional_expression_over_return</span><span class="sxs-lookup"><span data-stu-id="43213-157">dotnet_style_prefer_conditional_expression_over_return</span></span>](ide0046.md#dotnet_style_prefer_conditional_expression_over_return)
  - [<span data-ttu-id="43213-158">dotnet_style_prefer_compound_assignment</span><span class="sxs-lookup"><span data-stu-id="43213-158">dotnet_style_prefer_compound_assignment</span></span>](ide0054-ide0074.md#dotnet_style_prefer_compound_assignment)
  - [<span data-ttu-id="43213-159">dotnet_style_prefer_simplified_interpolation</span><span class="sxs-lookup"><span data-stu-id="43213-159">dotnet_style_prefer_simplified_interpolation</span></span>](ide0071.md#dotnet_style_prefer_simplified_interpolation)
  - [<span data-ttu-id="43213-160">dotnet_style_prefer_simplified_boolean_expressions</span><span class="sxs-lookup"><span data-stu-id="43213-160">dotnet_style_prefer_simplified_boolean_expressions</span></span>](ide0075.md#dotnet_style_prefer_simplified_boolean_expressions)
  - <span data-ttu-id="43213-161">[Добавить отсутствующие варианты в оператор switch](ide0010.md). У этого правила нет параметра стиля кода.</span><span class="sxs-lookup"><span data-stu-id="43213-161">[Add missing cases to switch statement](ide0010.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="43213-162">[Преобразовать анонимный тип в кортеж](ide0050.md). У этого правила нет параметра стиля кода.</span><span class="sxs-lookup"><span data-stu-id="43213-162">[Convert anonymous type to tuple](ide0050.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="43213-163">[Использовать "System.HashCode.Combine"](ide0070.md). У этого правила нет стиля кода.</span><span class="sxs-lookup"><span data-stu-id="43213-163">[Use 'System.HashCode.Combine'](ide0070.md) - This rule has no code style option.</span></span>
  - <span data-ttu-id="43213-164">[Преобразовать "typeof" в "NameOf"](ide0082.md). У этого правила нет параметра стиля кода.</span><span class="sxs-lookup"><span data-stu-id="43213-164">[Convert 'typeof' to 'nameof'](ide0082.md) - This rule has no code style option.</span></span>
- [<span data-ttu-id="43213-165">Параметры проверки NULL</span><span class="sxs-lookup"><span data-stu-id="43213-165">Null-checking preferences</span></span>](null-checking-preferences.md#net-null-checking-preferences)
  - [<span data-ttu-id="43213-166">dotnet_style_coalesce_expression</span><span class="sxs-lookup"><span data-stu-id="43213-166">dotnet_style_coalesce_expression</span></span>](ide0029-ide0030.md#dotnet_style_coalesce_expression)
  - [<span data-ttu-id="43213-167">dotnet_style_null_propagation</span><span class="sxs-lookup"><span data-stu-id="43213-167">dotnet_style_null_propagation</span></span>](ide0031.md#dotnet_style_null_propagation)
  - [<span data-ttu-id="43213-168">dotnet_style_prefer_is_null_check_over_reference_equality_method</span><span class="sxs-lookup"><span data-stu-id="43213-168">dotnet_style_prefer_is_null_check_over_reference_equality_method</span></span>](ide0041.md#dotnet_style_prefer_is_null_check_over_reference_equality_method)
- [<span data-ttu-id="43213-169">Параметры заголовка файла</span><span class="sxs-lookup"><span data-stu-id="43213-169">File header preferences</span></span>](ide0073.md)
  - [<span data-ttu-id="43213-170">file_header_template</span><span class="sxs-lookup"><span data-stu-id="43213-170">file_header_template</span></span>](ide0073.md#file_header_template)

## <a name="c-style-rules"></a><span data-ttu-id="43213-171">Правила стиля C#</span><span class="sxs-lookup"><span data-stu-id="43213-171">C# style rules</span></span>

<span data-ttu-id="43213-172">Правила стиля в этом разделе относятся только к C#.</span><span class="sxs-lookup"><span data-stu-id="43213-172">The style rules in this section are applicable to C# language only.</span></span>

- [<span data-ttu-id="43213-173">Параметры "var"</span><span class="sxs-lookup"><span data-stu-id="43213-173">'var' preferences</span></span>](ide0007-ide0008.md)
  - [<span data-ttu-id="43213-174">csharp_style_var_for_built_in_types</span><span class="sxs-lookup"><span data-stu-id="43213-174">csharp_style_var_for_built_in_types</span></span>](ide0007-ide0008.md#csharp_style_var_for_built_in_types)
  - [<span data-ttu-id="43213-175">csharp_style_var_when_type_is_apparent</span><span class="sxs-lookup"><span data-stu-id="43213-175">csharp_style_var_when_type_is_apparent</span></span>](ide0007-ide0008.md#csharp_style_var_when_type_is_apparent)
  - [<span data-ttu-id="43213-176">csharp_style_var_elsewhere</span><span class="sxs-lookup"><span data-stu-id="43213-176">csharp_style_var_elsewhere</span></span>](ide0007-ide0008.md#csharp_style_var_elsewhere)
- [<span data-ttu-id="43213-177">Элементы, воплощающие выражение</span><span class="sxs-lookup"><span data-stu-id="43213-177">Expression-bodied members</span></span>](expression-bodied-members.md)
  - [<span data-ttu-id="43213-178">csharp_style_expression_bodied_methods</span><span class="sxs-lookup"><span data-stu-id="43213-178">csharp_style_expression_bodied_methods</span></span>](ide0022.md#csharp_style_expression_bodied_methods)
  - [<span data-ttu-id="43213-179">csharp_style_expression_bodied_constructors</span><span class="sxs-lookup"><span data-stu-id="43213-179">csharp_style_expression_bodied_constructors</span></span>](ide0021.md#csharp_style_expression_bodied_constructors)
  - [<span data-ttu-id="43213-180">csharp_style_expression_bodied_operators</span><span class="sxs-lookup"><span data-stu-id="43213-180">csharp_style_expression_bodied_operators</span></span>](ide0023-ide0024.md#csharp_style_expression_bodied_operators)
  - [<span data-ttu-id="43213-181">csharp_style_expression_bodied_properties</span><span class="sxs-lookup"><span data-stu-id="43213-181">csharp_style_expression_bodied_properties</span></span>](ide0025.md#csharp_style_expression_bodied_properties)
  - [<span data-ttu-id="43213-182">csharp_style_expression_bodied_indexers</span><span class="sxs-lookup"><span data-stu-id="43213-182">csharp_style_expression_bodied_indexers</span></span>](ide0026.md#csharp_style_expression_bodied_indexers)
  - [<span data-ttu-id="43213-183">csharp_style_expression_bodied_accessors</span><span class="sxs-lookup"><span data-stu-id="43213-183">csharp_style_expression_bodied_accessors</span></span>](ide0027.md#csharp_style_expression_bodied_accessors)
  - [<span data-ttu-id="43213-184">csharp_style_expression_bodied_lambdas</span><span class="sxs-lookup"><span data-stu-id="43213-184">csharp_style_expression_bodied_lambdas</span></span>](ide0053.md#csharp_style_expression_bodied_lambdas)
  - [<span data-ttu-id="43213-185">csharp_style_expression_bodied_local_functions</span><span class="sxs-lookup"><span data-stu-id="43213-185">csharp_style_expression_bodied_local_functions</span></span>](ide0061.md#csharp_style_expression_bodied_local_functions)
- [<span data-ttu-id="43213-186">Настройки соответствия шаблонов</span><span class="sxs-lookup"><span data-stu-id="43213-186">Pattern matching preferences</span></span>](pattern-matching-preferences.md)
  - [<span data-ttu-id="43213-187">csharp_style_pattern_matching_over_is_with_cast_check</span><span class="sxs-lookup"><span data-stu-id="43213-187">csharp_style_pattern_matching_over_is_with_cast_check</span></span>](ide0020-ide0038.md#csharp_style_pattern_matching_over_is_with_cast_check)
  - [<span data-ttu-id="43213-188">csharp_style_pattern_matching_over_as_with_null_check</span><span class="sxs-lookup"><span data-stu-id="43213-188">csharp_style_pattern_matching_over_as_with_null_check</span></span>](ide0019.md#csharp_style_pattern_matching_over_as_with_null_check)
  - [<span data-ttu-id="43213-189">csharp_style_prefer_switch_expression</span><span class="sxs-lookup"><span data-stu-id="43213-189">csharp_style_prefer_switch_expression</span></span>](ide0066.md#csharp_style_prefer_switch_expression)
  - [<span data-ttu-id="43213-190">csharp_style_prefer_pattern_matching</span><span class="sxs-lookup"><span data-stu-id="43213-190">csharp_style_prefer_pattern_matching</span></span>](ide0078.md#csharp_style_prefer_pattern_matching)
  - [<span data-ttu-id="43213-191">csharp_style_prefer_not_pattern</span><span class="sxs-lookup"><span data-stu-id="43213-191">csharp_style_prefer_not_pattern</span></span>](ide0083.md#csharp_style_prefer_not_pattern)
- [<span data-ttu-id="43213-192">Настройки уровня выражений</span><span class="sxs-lookup"><span data-stu-id="43213-192">Expression-level preferences</span></span>](expression-level-preferences.md#c-expression-level-preferences)
  - [<span data-ttu-id="43213-193">csharp_style_inlined_variable_declaration</span><span class="sxs-lookup"><span data-stu-id="43213-193">csharp_style_inlined_variable_declaration</span></span>](ide0018.md#csharp_style_inlined_variable_declaration)
  - [<span data-ttu-id="43213-194">csharp_prefer_simple_default_expression</span><span class="sxs-lookup"><span data-stu-id="43213-194">csharp_prefer_simple_default_expression</span></span>](ide0034.md#csharp_prefer_simple_default_expression)
  - [<span data-ttu-id="43213-195">csharp_style_pattern_local_over_anonymous_function</span><span class="sxs-lookup"><span data-stu-id="43213-195">csharp_style_pattern_local_over_anonymous_function</span></span>](ide0039.md#csharp_style_pattern_local_over_anonymous_function)
  - [<span data-ttu-id="43213-196">csharp_style_deconstructed_variable_declaration</span><span class="sxs-lookup"><span data-stu-id="43213-196">csharp_style_deconstructed_variable_declaration</span></span>](ide0042.md#csharp_style_deconstructed_variable_declaration)
  - [<span data-ttu-id="43213-197">csharp_style_prefer_index_operator</span><span class="sxs-lookup"><span data-stu-id="43213-197">csharp_style_prefer_index_operator</span></span>](ide0056.md#csharp_style_prefer_index_operator)
  - [<span data-ttu-id="43213-198">csharp_style_prefer_range_operator</span><span class="sxs-lookup"><span data-stu-id="43213-198">csharp_style_prefer_range_operator</span></span>](ide0057.md#csharp_style_prefer_range_operator)
  - [<span data-ttu-id="43213-199">csharp_style_implicit_object_creation_when_type_is_apparent</span><span class="sxs-lookup"><span data-stu-id="43213-199">csharp_style_implicit_object_creation_when_type_is_apparent</span></span>](ide0090.md#csharp_style_implicit_object_creation_when_type_is_apparent)
  - <span data-ttu-id="43213-200">[Добавить отсутствующие варианты в выражение switch](ide0072.md). У этого правила нет параметра стиля кода.</span><span class="sxs-lookup"><span data-stu-id="43213-200">[Add missing cases to switch expression](ide0072.md) - This rule has no code style option.</span></span>
- [<span data-ttu-id="43213-201">Настройки проверки Null</span><span class="sxs-lookup"><span data-stu-id="43213-201">"Null" checking preferences</span></span>](null-checking-preferences.md#c-null-checking-preferences)
  - [<span data-ttu-id="43213-202">csharp_style_throw_expression</span><span class="sxs-lookup"><span data-stu-id="43213-202">csharp_style_throw_expression</span></span>](ide0016.md#csharp_style_throw_expression)
  - [<span data-ttu-id="43213-203">csharp_style_conditional_delegate_call</span><span class="sxs-lookup"><span data-stu-id="43213-203">csharp_style_conditional_delegate_call</span></span>](ide1005.md#csharp_style_conditional_delegate_call)
- [<span data-ttu-id="43213-204">Настройки блока кода</span><span class="sxs-lookup"><span data-stu-id="43213-204">Code block preferences</span></span>](code-block-preferences.md)
  - [<span data-ttu-id="43213-205">csharp_prefer_braces</span><span class="sxs-lookup"><span data-stu-id="43213-205">csharp_prefer_braces</span></span>](ide0011.md#csharp_prefer_braces)
  - [<span data-ttu-id="43213-206">csharp_prefer_simple_using_statement</span><span class="sxs-lookup"><span data-stu-id="43213-206">csharp_prefer_simple_using_statement</span></span>](ide0063.md#csharp_prefer_simple_using_statement)
- [<span data-ttu-id="43213-207">Параметры директивы using</span><span class="sxs-lookup"><span data-stu-id="43213-207">'using' directive preferences</span></span>](ide0065.md)
  - [<span data-ttu-id="43213-208">csharp_using_directive_placement</span><span class="sxs-lookup"><span data-stu-id="43213-208">csharp_using_directive_placement</span></span>](ide0065.md#csharp_using_directive_placement)
- [<span data-ttu-id="43213-209">Предпочтения для модификаторов</span><span class="sxs-lookup"><span data-stu-id="43213-209">Modifier preferences</span></span>](modifier-preferences.md#c-modifier-preferences)
  - [<span data-ttu-id="43213-210">csharp_prefer_static_local_function</span><span class="sxs-lookup"><span data-stu-id="43213-210">csharp_prefer_static_local_function</span></span>](ide0062.md#csharp_prefer_static_local_function)
  - <span data-ttu-id="43213-211">[Сделать поля структуры доступными для записи](ide0064.md). У этого правила нет параметра стиля кода.</span><span class="sxs-lookup"><span data-stu-id="43213-211">[Make struct fields writable](ide0064.md) - This rule has no code style option.</span></span>

## <a name="visual-basic-style-rules"></a><span data-ttu-id="43213-212">Правила стиля Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43213-212">Visual Basic style rules</span></span>

<span data-ttu-id="43213-213">Правила стиля в этом разделе относятся только к языку Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="43213-213">The style rules in this section are applicable to Visual Basic language only.</span></span>

- [<span data-ttu-id="43213-214">Настройки соответствия шаблонов</span><span class="sxs-lookup"><span data-stu-id="43213-214">Pattern matching preferences</span></span>](pattern-matching-preferences.md)
  - [<span data-ttu-id="43213-215">visual_basic_style_prefer_isnot_expression</span><span class="sxs-lookup"><span data-stu-id="43213-215">visual_basic_style_prefer_isnot_expression</span></span>](ide0084.md#visual_basic_style_prefer_isnot_expression)

## <a name="see-also"></a><span data-ttu-id="43213-216">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="43213-216">See also</span></span>

- [<span data-ttu-id="43213-217">Правила, касающиеся ненужного кода</span><span class="sxs-lookup"><span data-stu-id="43213-217">Unnecessary code rules</span></span>](unnecessary-code-rules.md)
- [<span data-ttu-id="43213-218">Правила форматирования</span><span class="sxs-lookup"><span data-stu-id="43213-218">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="43213-219">Правила именования</span><span class="sxs-lookup"><span data-stu-id="43213-219">Naming rules</span></span>](naming-rules.md)
- [<span data-ttu-id="43213-220">Справочник по правилам стиля кода для .NET</span><span class="sxs-lookup"><span data-stu-id="43213-220">.NET code style rules reference</span></span>](index.md)
