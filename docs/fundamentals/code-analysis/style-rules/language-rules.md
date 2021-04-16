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
# <a name="language-rules"></a>Правила языка

Правила языка для стиля кода влияют на использование различных конструкций языков программирования .NET, например модификаторов и круглых скобок. Эти правила делятся на следующие категории:

- [Правила стиля .NET](#net-style-rules) в равной мере применяются к C# и Visual Basic. Имена параметров EditorConfig для этих правил начинаются с префикса `dotnet_style_`.
- [Правила стиля C#](#c-style-rules) применяются только для языка C#. Имена параметров EditorConfig для этих правил начинаются с префикса `csharp_style_`.
- [Правила стиля Visual Basic](#visual-basic-style-rules) применяются только для языка Visual Basic. Имена параметров EditorConfig для этих правил начинаются с префикса `visual_basic_style_`.

## <a name="option-format"></a>Формат параметра

Параметры для правил языка можно указывать в файле EditorConfig в следующем формате:

`option_name = value` (Visual Studio 2019 версии 16.9, предварительная версия 2 и более поздние версии)

или

`option_name = value:severity`

- **Значение**

  Для каждого правила языка укажите значение, которое определяет условия выбора соответствующего стиля. Многие правила принимают значение `true` (предпочитать этот стиль) или `false` (не предпочитать этот стиль). Другие правила принимают значения `when_on_single_line` или `never`.

- **Уровень серьезности** (необязательно в Visual Studio 2019 версии 16.9, предварительная версия 2 и более поздние версии)

  Вторая часть правила определяет [уровень серьезности](../configuration-options.md#severity-level) правила. Если параметр уровня серьезности задан таким образом, он учитывается только в таких средах IDE, как Visual Studio. Он *не* учитывается во время сборки.

  Чтобы применить правила стиля кода во время сборки, задайте уровень серьезности с помощью синтаксиса конфигурации серьезности на основе идентификатора правила для анализаторов. Синтаксис имеет вид `dotnet_diagnostic.<rule ID>.severity = <severity>`, например `dotnet_diagnostic.IDE0040.severity = silent`. Дополнительные сведения см. в разделе об [уровне серьезности](../configuration-options.md#severity-level).

> [!TIP]
>
> Начиная с Visual Studio 2019 версии 16.3, в меню [Быстрые действия](/visualstudio/ide/quick-actions) можно настроить правила стиля кода после нарушения стиля. Дополнительные сведения см. в разделе [Автоматическая настройка стилей кода в Visual Studio](/visualstudio/ide/editorconfig-language-conventions#automatically-configure-code-styles-in-visual-studio).

## <a name="net-style-rules"></a>Правила стиля .NET

Правила стилей в этом разделе относятся как к C#, так и к Visual Basic.

- [Квалификаторы "this." и "Me."](ide0003-ide0009.md)
  - [dotnet_style_qualification_for_field](ide0003-ide0009.md#dotnet_style_qualification_for_field)
  - [dotnet_style_qualification_for_property](ide0003-ide0009.md#dotnet_style_qualification_for_property)
  - [dotnet_style_qualification_for_method](ide0003-ide0009.md#dotnet_style_qualification_for_method)
  - [dotnet_style_qualification_for_event](ide0003-ide0009.md#dotnet_style_qualification_for_event)
- [Ключевые слова языка вместо имен типов .NET Framework для ссылок на типы](ide0049.md)
  - [dotnet_style_predefined_type_for_locals_parameters_members](ide0049.md#dotnet_style_predefined_type_for_locals_parameters_members)
  - [dotnet_style_predefined_type_for_member_access](ide0049.md#dotnet_style_predefined_type_for_member_access)
- [Предпочтения для модификаторов](modifier-preferences.md#net-modifier-preferences)
  - [dotnet_style_require_accessibility_modifiers](ide0040.md#dotnet_style_require_accessibility_modifiers)
  - [csharp_preferred_modifier_order](ide0036.md#csharp_preferred_modifier_order)
  - [visual_basic_preferred_modifier_order](ide0036.md#visual_basic_preferred_modifier_order)
  - [dotnet_style_readonly_field](ide0044.md#dotnet_style_readonly_field)
- [Предпочтения относительно круглых скобок](ide0047-ide0048.md)
  - [dotnet_style_parentheses_in_arithmetic_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_arithmetic_binary_operators)
  - [dotnet_style_parentheses_in_relational_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_relational_binary_operators)
  - [dotnet_style_parentheses_in_other_binary_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_other_binary_operators)
  - [dotnet_style_parentheses_in_other_operators](ide0047-ide0048.md#dotnet_style_parentheses_in_other_operators)
- [Настройки уровня выражений](expression-level-preferences.md#net-expression-level-preferences)
  - [dotnet_style_object_initializer](ide0017.md#dotnet_style_object_initializer)
  - [dotnet_style_collection_initializer](ide0028.md#dotnet_style_collection_initializer)
  - [dotnet_style_explicit_tuple_names](ide0033.md#dotnet_style_explicit_tuple_names)
  - [dotnet_style_prefer_inferred_tuple_names](ide0037.md#dotnet_style_prefer_inferred_tuple_names)
  - [dotnet_style_prefer_inferred_anonymous_type_member_names](ide0037.md#dotnet_style_prefer_inferred_anonymous_type_member_names)
  - [dotnet_style_prefer_auto_properties](ide0032.md#dotnet_style_prefer_auto_properties)
  - [dotnet_style_prefer_conditional_expression_over_assignment](ide0045.md#dotnet_style_prefer_conditional_expression_over_assignment)
  - [dotnet_style_prefer_conditional_expression_over_return](ide0046.md#dotnet_style_prefer_conditional_expression_over_return)
  - [dotnet_style_prefer_compound_assignment](ide0054-ide0074.md#dotnet_style_prefer_compound_assignment)
  - [dotnet_style_prefer_simplified_interpolation](ide0071.md#dotnet_style_prefer_simplified_interpolation)
  - [dotnet_style_prefer_simplified_boolean_expressions](ide0075.md#dotnet_style_prefer_simplified_boolean_expressions)
  - [Добавить отсутствующие варианты в оператор switch](ide0010.md). У этого правила нет параметра стиля кода.
  - [Преобразовать анонимный тип в кортеж](ide0050.md). У этого правила нет параметра стиля кода.
  - [Использовать "System.HashCode.Combine"](ide0070.md). У этого правила нет стиля кода.
  - [Преобразовать "typeof" в "NameOf"](ide0082.md). У этого правила нет параметра стиля кода.
- [Параметры проверки NULL](null-checking-preferences.md#net-null-checking-preferences)
  - [dotnet_style_coalesce_expression](ide0029-ide0030.md#dotnet_style_coalesce_expression)
  - [dotnet_style_null_propagation](ide0031.md#dotnet_style_null_propagation)
  - [dotnet_style_prefer_is_null_check_over_reference_equality_method](ide0041.md#dotnet_style_prefer_is_null_check_over_reference_equality_method)
- [Параметры заголовка файла](ide0073.md)
  - [file_header_template](ide0073.md#file_header_template)

## <a name="c-style-rules"></a>Правила стиля C#

Правила стиля в этом разделе относятся только к C#.

- [Параметры "var"](ide0007-ide0008.md)
  - [csharp_style_var_for_built_in_types](ide0007-ide0008.md#csharp_style_var_for_built_in_types)
  - [csharp_style_var_when_type_is_apparent](ide0007-ide0008.md#csharp_style_var_when_type_is_apparent)
  - [csharp_style_var_elsewhere](ide0007-ide0008.md#csharp_style_var_elsewhere)
- [Элементы, воплощающие выражение](expression-bodied-members.md)
  - [csharp_style_expression_bodied_methods](ide0022.md#csharp_style_expression_bodied_methods)
  - [csharp_style_expression_bodied_constructors](ide0021.md#csharp_style_expression_bodied_constructors)
  - [csharp_style_expression_bodied_operators](ide0023-ide0024.md#csharp_style_expression_bodied_operators)
  - [csharp_style_expression_bodied_properties](ide0025.md#csharp_style_expression_bodied_properties)
  - [csharp_style_expression_bodied_indexers](ide0026.md#csharp_style_expression_bodied_indexers)
  - [csharp_style_expression_bodied_accessors](ide0027.md#csharp_style_expression_bodied_accessors)
  - [csharp_style_expression_bodied_lambdas](ide0053.md#csharp_style_expression_bodied_lambdas)
  - [csharp_style_expression_bodied_local_functions](ide0061.md#csharp_style_expression_bodied_local_functions)
- [Настройки соответствия шаблонов](pattern-matching-preferences.md)
  - [csharp_style_pattern_matching_over_is_with_cast_check](ide0020-ide0038.md#csharp_style_pattern_matching_over_is_with_cast_check)
  - [csharp_style_pattern_matching_over_as_with_null_check](ide0019.md#csharp_style_pattern_matching_over_as_with_null_check)
  - [csharp_style_prefer_switch_expression](ide0066.md#csharp_style_prefer_switch_expression)
  - [csharp_style_prefer_pattern_matching](ide0078.md#csharp_style_prefer_pattern_matching)
  - [csharp_style_prefer_not_pattern](ide0083.md#csharp_style_prefer_not_pattern)
- [Настройки уровня выражений](expression-level-preferences.md#c-expression-level-preferences)
  - [csharp_style_inlined_variable_declaration](ide0018.md#csharp_style_inlined_variable_declaration)
  - [csharp_prefer_simple_default_expression](ide0034.md#csharp_prefer_simple_default_expression)
  - [csharp_style_pattern_local_over_anonymous_function](ide0039.md#csharp_style_pattern_local_over_anonymous_function)
  - [csharp_style_deconstructed_variable_declaration](ide0042.md#csharp_style_deconstructed_variable_declaration)
  - [csharp_style_prefer_index_operator](ide0056.md#csharp_style_prefer_index_operator)
  - [csharp_style_prefer_range_operator](ide0057.md#csharp_style_prefer_range_operator)
  - [csharp_style_implicit_object_creation_when_type_is_apparent](ide0090.md#csharp_style_implicit_object_creation_when_type_is_apparent)
  - [Добавить отсутствующие варианты в выражение switch](ide0072.md). У этого правила нет параметра стиля кода.
- [Настройки проверки Null](null-checking-preferences.md#c-null-checking-preferences)
  - [csharp_style_throw_expression](ide0016.md#csharp_style_throw_expression)
  - [csharp_style_conditional_delegate_call](ide1005.md#csharp_style_conditional_delegate_call)
- [Настройки блока кода](code-block-preferences.md)
  - [csharp_prefer_braces](ide0011.md#csharp_prefer_braces)
  - [csharp_prefer_simple_using_statement](ide0063.md#csharp_prefer_simple_using_statement)
- [Параметры директивы using](ide0065.md)
  - [csharp_using_directive_placement](ide0065.md#csharp_using_directive_placement)
- [Предпочтения для модификаторов](modifier-preferences.md#c-modifier-preferences)
  - [csharp_prefer_static_local_function](ide0062.md#csharp_prefer_static_local_function)
  - [Сделать поля структуры доступными для записи](ide0064.md). У этого правила нет параметра стиля кода.

## <a name="visual-basic-style-rules"></a>Правила стиля Visual Basic

Правила стиля в этом разделе относятся только к языку Visual Basic.

- [Настройки соответствия шаблонов](pattern-matching-preferences.md)
  - [visual_basic_style_prefer_isnot_expression](ide0084.md#visual_basic_style_prefer_isnot_expression)

## <a name="see-also"></a>См. также раздел

- [Правила, касающиеся ненужного кода](unnecessary-code-rules.md)
- [Правила форматирования](formatting-rules.md)
- [Правила именования](naming-rules.md)
- [Справочник по правилам стиля кода для .NET](index.md)
