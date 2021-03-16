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
# <a name="formatting-rules"></a>Правила форматирования

Правила форматирования влияют на то, как размещаются отступы, пробелы и новые строки вокруг конструкций языка программирования .NET. Эти правила делятся на следующие категории:

- [Правила форматирования .NET](#net-formatting-rules) в равной мере применяются к C# и Visual Basic. Имена параметров EditorConfig для этих правил начинаются с префикса `dotnet_`.
- [Правила форматирования C#](#c-formatting-rules) применяются только для языка C#. Имена параметров EditorConfig для этих правил начинаются с префикса `csharp_`.

## <a name="rule-id-ide0055-fix-formatting"></a>Идентификатор правила: IDE0055 (исправление форматирования)

Все параметры форматирования имеют идентификатор `IDE0055` и заголовок `Fix formatting`. Задайте серьезность нарушения правил форматирования в файле EditorConfig, используя следующую строку конфигурации.

```ini
dotnet_diagnostic.IDE0055.severity = <severity value>
```

Серьезность должна иметь значение `warning` или `error`, чтобы [принудительно применяться при сборке](../overview.md#code-style-analysis). Все возможные значения серьезности перечислены на странице [об уровнях серьезности](../configuration-options.md#severity-level).

## <a name="option-format"></a>Формат параметра

Параметры для правил форматирования можно указывать в файле EditorConfig в следующем формате:

`rule_name = value`

Для большинства правил вы указываете значение `true` (предпочитать этот стиль) или `value` (не предпочитать этот стиль) для `false`. Для нескольких правил указываются другие значения, например `flush_left` или `before_and_after`, которые описывают порядок применения этих правил. Уровень серьезности указывать не нужно.

## <a name="net-formatting-rules"></a>Правила форматирования .NET

Правила форматирования в этом разделе в равной мере применяются к C# и Visual Basic.

- [Управление директивами using](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Оптимизация директив Using

Эти правила форматирования относятся к сортировке и отображению директив `using` и инструкций `Imports`.

Пример файла *EDITORCONFIG*:

```ini
# .NET formatting rules
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a>dotnet\_sort\_system\_directives_first

|Свойство.|Значение|
|-|-|
| **Имя параметра** | dotnet_sort_system_directives_first |
| **Применимые языки** | C# и Visual Basic |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — сортировать директивы `System.*` `using` в алфавитном порядке, располагая их перед всеми остальными директивами using.<br /><br />`false` — не размещать директивы `System.*` `using` перед другими директивами `using`. |

Примеры кода:

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

#### <a name="dotnet_separate_import_directive_groups"></a>dotnet\_separate\_import\_directive\_groups

|Свойство.|Значение|
|-|-|
| **Имя параметра** | dotnet_separate_import_directive_groups |
| **Применимые языки** | C# и Visual Basic |
| **Представленные версии** | Visual Studio 2017 версии 15.5 |
| **Значения параметра** | `true` — поместить пустую строку между группами директив `using`.<br /><br />`false` — не помещать пустую строку между группами директив `using`. |

Примеры кода:

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

## <a name="c-formatting-rules"></a>Правила форматирования C#

Правила форматирования в этом разделе относятся только к коду C#.

- [Параметры перевода строки](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [Параметры отступа](#indentation-options)
  - csharp_indent_case_contents
  - csharp_indent_switch_labels
  - csharp_indent_labels
  - csharp_indent_block_contents
  - csharp_indent_braces
  - csharp_indent_case_contents_when_block
- [Параметры интервалов](#spacing-options)
  - csharp_space_after_cast
  - csharp_space_after_keywords_in_control_flow_statements
  - csharp_space_between_parentheses
  - csharp_space_before_colon_in_inheritance_clause
  - csharp_space_after_colon_in_inheritance_clause
  - csharp_space_around_binary_operators
  - csharp_space_between_method_declaration_parameter_list_parentheses
  - csharp_space_between_method_declaration_empty_parameter_list_parentheses
  - csharp_space_between_method_declaration_name_and_open_parenthesis
  - csharp_space_between_method_call_parameter_list_parentheses
  - csharp_space_between_method_call_empty_parameter_list_parentheses
  - csharp_space_between_method_call_name_and_opening_parenthesis
  - csharp_space_after_comma
  - csharp_space_before_comma
  - csharp_space_after_dot
  - csharp_space_before_dot
  - csharp_space_after_semicolon_in_for_statement
  - csharp_space_before_semicolon_in_for_statement
  - csharp_space_around_declaration_statements
  - csharp_space_before_open_square_brackets
  - csharp_space_between_empty_square_brackets
  - csharp_space_between_square_brackets
- [Параметры переноса](#wrap-options)
  - csharp_preserve_single_line_statements
  - csharp_preserve_single_line_blocks
- [Параметры директивы using](#using-directive-options)
  - csharp_using_directive_placement

### <a name="new-line-options"></a>Параметры новой строки

Эти правила форматирования относятся использованию новых строк для форматирования кода.

Пример файла *EDITORCONFIG*:

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

#### <a name="csharp_new_line_before_open_brace"></a>csharp\_new\_line\_before\_open_brace

Это правило определяет, следует ли располагать открывающую фигурную скобку `{` одной строке с предшествующим кодом или на новой строке. Для этого правила укажите **all**, **none** либо один или несколько элементов кода, таких как **methods** или **properties**, для которых следует применять это правило. Если вы указываете несколько элементов кода, разделяйте их запятыми (,).

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_new_line_before_open_brace |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `all` — требовать, чтобы фигурные скобки для всех выражений размещались в новой строке (стиль Олмана).<br /><br />`none` — требовать, чтобы фигурные скобки для всех выражений размещались в строке выражения (стиль Кернигана и Ритчи).<br /><br />`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` — требовать, чтобы фигурные скобки для указанного элемента кода размещались в новой строке (стиль Олмана). |

Примеры кода:

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

#### <a name="csharp_new_line_before_else"></a>csharp\_new\_line\_before_else

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_new_line_before_else |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — размещать инструкции `else` в новой строке.<br /><br />`false` — размещать инструкции `else` в той же строке. |

Примеры кода:

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

#### <a name="csharp_new_line_before_catch"></a>csharp\_new\_line\_before_catch

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_new_line_before_catch |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — размещать инструкции `catch` в новой строке.<br /><br />`false` — размещать инструкции `catch` в той же строке. |

Примеры кода:

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

#### <a name="csharp_new_line_before_finally"></a>csharp\_new\_line\_before_finally

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_new_line_before_finally |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — требовать, чтобы инструкции `finally` размещались в новой строке после закрывающей фигурной скобки.<br /><br />`false` — требовать, чтобы инструкции `finally` размещались в той же строке после закрывающей фигурной скобки. |

Примеры кода:

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

#### <a name="csharp_new_line_before_members_in_object_initializers"></a>csharp\_new\_line\_before\_members\_in\_object_initializers

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_new_line_before_members_in_object_initializers |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — требовать, чтобы элементы инициализаторов объектов размещались в разных строках.<br /><br />`false` — требовать, чтобы элементы инициализаторов объектов размещались в той же строке. |

Примеры кода:

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

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a>csharp\_new\_line\_before\_members\_in\_anonymous_types

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_new_line_before_members_in_anonymous_types |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — требовать, чтобы элементы анонимных типов размещались в разных строках.<br /><br />`false` — требовать, чтобы элементы анонимных типов размещались в той же строке. |

Примеры кода:

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

#### <a name="csharp_new_line_between_query_expression_clauses"></a>csharp_new_line_between_query_expression_clauses

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_new_line_between_query_expression_clauses |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — требовать, чтобы элементы в предложениях выражений запросов размещались в отдельных строках.<br /><br />`false` — требовать, чтобы элементы в предложениях выражений запросов размещались в той же строке. |

Примеры кода:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a>Параметры отступа

Эти правила форматирования относятся к использованию отступа для форматирования кода.

Пример файла *EDITORCONFIG*:

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

#### <a name="csharp_indent_case_contents"></a>csharp\_indent\_case_contents

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_indent_case_contents |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — отступ в конструкции `switch` case<br /><br />`false` — не использовать отступ в конструкции `switch` case |

- Когда для этого правила задано значение **true**, i.
- Когда для этого правила задано значение **false**, d.

Примеры кода:

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

#### <a name="csharp_indent_switch_labels"></a>csharp\_indent\_switch_labels

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_indent_switch_labels |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — отступ для меток `switch`.<br /><br />`false` — не использовать отступ для меток `switch`. |

Примеры кода:

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

#### <a name="csharp_indent_labels"></a>csharp\_indent_labels

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_indent_labels |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `flush_left` — метки размещаются в крайнем левом столбце.<br /><br />`one_less_than_current` — метки размещаются на предыдущей позиции отступа относительно текущего контекста.<br /><br />`no_change` — метки размещаются на той же позиции отступа, что и текущий контекст. |

Примеры кода:

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

#### <a name="csharp_indent_block_contents"></a>csharp_indent_block_contents

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_indent_block_contents |
| **Применимые языки** | C# |
| **Значения параметра** | `true` - <br /><br />`false` -  |

Примеры кода:

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

#### <a name="csharp_indent_braces"></a>csharp_indent_braces

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_indent_braces |
| **Применимые языки** | C# |
| **Значения параметра** | `true` - <br /><br />`false` -  |

Примеры кода:

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

#### <a name="csharp_indent_case_contents_when_block"></a>csharp_indent_case_contents_when_block

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_indent_case_contents_when_block |
| **Применимые языки** | C# |
| **Значения параметра** | `true` - <br /><br />`false` -  |

Примеры кода:

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

### <a name="spacing-options"></a>Параметры интервалов

Эти правила форматирования относятся к использованию пробелов для форматирования кода.

Пример файла *EDITORCONFIG*:

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

#### <a name="csharp_space_after_cast"></a>csharp\_space\_after_cast

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_after_cast |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — разместить пробел между типом и значением в приведении<br /><br />`false` — удалить пробел между типом и значением в приведении |

Примеры кода:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a>csharp_space_after_keywords_in_control_flow_statements

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_after_keywords_in_control_flow_statements |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — поместить пробел после ключевого слова в операторе потока управления, например цикле `for`<br /><br />`false` — удалить пробел после ключевого слова в операторе потока управления, например цикле `for` |

Примеры кода:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a>csharp_space_between_parentheses

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_between_parentheses |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `control_flow_statements` — добавлять пробел между скобками для операторов потока управления.<br /><br />`expressions` — добавлять пробел между скобками для выражений.<br /><br />`type_casts` — размещать пробел между скобками в приведениях типов. |

Если пропустить это правило или использовать значение, отличное от `control_flow_statements`, `expressions` или `type_casts`, этот параметр не применяется.

Примеры кода:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a>csharp\_space\_before\_colon\_in\_inheritance_clause

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_before_colon_in_inheritance_clause |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |
| **Значения параметра** | `true` — поместить пробел перед двоеточием для баз или интерфейсов в объявлении типа<br /><br />`false` — удалить пробел перед двоеточием для баз или интерфейсов в объявлении типа |

Примеры кода:

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

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a>csharp\_space\_after\_colon\_in\_inheritance_clause

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_after_colon_in_inheritance_clause |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |
| **Значения параметра** | `true` — поместить пробел после двоеточия для баз или интерфейсов в объявлении типа<br /><br />`false` — удалить пробел после двоеточия для баз или интерфейсов в объявлении типа |

Примеры кода:

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

#### <a name="csharp_space_around_binary_operators"></a>csharp\_space\_around\_binary_operators

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_around_binary_operators |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |
| **Значения параметра** | `before_and_after` — вставлять пробел до и после бинарных операторов.<br /><br />`none` — удалять пробелы до и после бинарных операторов.<br /><br />`ignore` — игнорировать пробелы вокруг бинарных операторов. |

Если пропустить это правило или использовать значение, отличное от `before_and_after`, `none` или `ignore`, этот параметр не применяется.

Примеры кода:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — размещать пробел после открывающей скобки и перед закрывающей скобкой в списке параметров объявления метода.<br /><br />`false` — удалить пробел после открывающей скобки и перед закрывающей скобкой в списке параметров объявления метода |

Примеры кода:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |
| **Значения параметра** | `true` — вставлять пробел между скобками пустого списка параметров при объявлении метода.<br /><br />`false` — удалять пробел между скобками пустого списка параметров при объявлении метода. |

Примеры кода:

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

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a>csharp_space_between_method_declaration_name_and_open_parenthesis

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_between_method_declaration_name_and_open_parenthesis |
| **Применимые языки** | C# |
| **Значения параметра** | `true` — поместить пробел между именем метода и открывающей круглой скобкой в объявлении метода<br /><br />`false` — удалить пробелы между именем метода и открывающей круглой скобкой в объявлении метода |

Примеры кода:

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_between_method_call_parameter_list_parentheses |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — размещать пробел после открывающей скобки и перед закрывающей скобкой в вызове метода.<br /><br />`false` — удалять пробел после открывающей скобки и перед закрывающей скобкой в вызове метода |

Примеры кода:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |
| **Значения параметра** | `true` — вставлять пробел между скобками в пустом списке аргументов.<br /><br />`false` — удалять пробел между скобками в пустом списке аргументов. |

Примеры кода:

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

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |
| **Значения параметра** | `true` — вставлять пробел между именем вызываемого метода и открывающей скобкой.<br /><br />`false` — удалять пробел между именем вызываемого метода и открывающей скобкой. |

Примеры кода:

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

#### <a name="csharp_space_after_comma"></a>csharp_space_after_comma

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_after_comma |
| **Применимые языки** | C# |
| **Значения параметра** | `true` — вставлять пробел после запятой.<br /><br />`false` — удалять пробел после запятой. |

Примеры кода:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a>csharp_space_before_comma

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_before_comma |
| **Применимые языки** | C# |
| **Значения параметра** | `true` — вставлять пробел перед запятой<br /><br />`false` — удалять пробел перед запятой |

Примеры кода:

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a>csharp_space_after_dot

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_after_dot |
| **Применимые языки** | C# |
| **Значения параметра** | `true` — вставлять пробел после точки.<br /><br />`false` — удалять пробел после точки. |

Примеры кода:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a>csharp_space_before_dot

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_before_dot |
| **Применимые языки** | C# |
| **Значения параметра** | `true` — вставлять пробел перед точкой <br /><br />`false` — удалять пробел перед точкой |

Примеры кода:

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a>csharp_space_after_semicolon_in_for_statement

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_after_semicolon_in_for_statement |
| **Применимые языки** | C# |
| **Значения параметра** | `true` — вставлять пробел после каждой точки с запятой в операторах `for`<br /><br />`false` — удалять пробел после каждой точки с запятой в операторах `for` |

Примеры кода:

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

#### <a name="csharp_space_before_semicolon_in_for_statement"></a>csharp_space_before_semicolon_in_for_statement

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_before_semicolon_in_for_statement |
| **Применимые языки** | C# |
| **Значения параметра** | `true` — вставлять пробел перед каждой точкой с запятой в операторах `for` <br /><br />`false` — удалять пробел перед каждой точкой с запятой в операторах `for` |

Примеры кода:

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a>csharp_space_around_declaration_statements

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_around_declaration_statements |
| **Применимые языки** | C# |
| **Значения параметра** | `ignore` — не удалять лишние пробелы в операторах объявления<br /><br />`false` — удалять лишние пробелы в операторах объявления |

Примеры кода:

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a>csharp_space_before_open_square_brackets

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_before_open_square_brackets |
| **Применимые языки** | C# |
| **Значения параметра** | `true` — вставлять пробел перед открывающей квадратной скобкой `[` <br /><br />`false` — удалять пробел перед открывающей квадратной скобкой `[` |

Примеры кода:

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a>csharp_space_between_empty_square_brackets

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_between_empty_square_brackets |
| **Применимые языки** | C# |
| **Значения параметра** | `true` — вставлять пробел перед пустыми квадратными скобками `[ ]` <br /><br />`false` — удалять пробел перед пустыми квадратными скобками `[]` |

Примеры кода:

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a>csharp_space_between_square_brackets

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_space_between_square_brackets |
| **Применимые языки** | C# |
| **Значения параметра** | `true` — вставлять пробел в непустых квадратных скобках `[ 0 ]` <br /><br />`false` — удалять пробел в непустых квадратных скобках `[0]` |

Примеры кода:

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a>Параметры переноса

Эти правила форматирования определяют размещение операторов и блоков кода в одной или разных строках.

Пример файла *EDITORCONFIG*:

```ini
# CSharp formatting rules:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a>csharp_preserve_single_line_statements

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_preserve_single_line_statements |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — оставлять выражения и объявления элемента в одной строке.<br /><br />`false` — оставлять выражения и объявления элемента в разных строках. |

Примеры кода:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a>csharp_preserve_single_line_blocks

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_preserve_single_line_blocks |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения параметра** | `true` — оставлять блок кода в одной строке.<br /><br />`false` — оставлять блок кода в разных строках. |

Примеры кода:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

### <a name="using-directive-options"></a>Параметры директивы using

Это правило форматирования относится к использованию директив using, размещаемых внутри и вне пространства имен.

Пример файла *EDITORCONFIG*:

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a>csharp_using_directive_placement

|Свойство.|Значение|
|-|-|
| **Имя параметра** | csharp_using_directive_placement |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2019 версии 16.1 |
| **Значения параметра** | `outside_namespace` — размещать директивы using вне пространства имен<br /><br />`inside_namespace` — размещать директивы using внутри пространства имен |

Примеры кода:

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

## <a name="see-also"></a>См. также

- [Правила языка](language-rules.md)
- [Правила именования](naming-rules.md)
- [Справочник по правилам стиля кода для .NET](index.md)
