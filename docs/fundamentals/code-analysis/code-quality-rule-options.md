---
title: Параметры конфигурации для правил качества кода
description: Сведения о том, как указать дополнительные параметры конфигурации для правил качества кода.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: 0be0d094739893dc74e1b5c85e686594c766cbcb
ms.sourcegitcommit: 26721a2260deabb3318cc98af8619306711153cd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/24/2021
ms.locfileid: "105027877"
---
# <a name="code-quality-rule-configuration-options"></a>Параметры конфигурации для правил качества кода

Правила *качества кода* имеют дополнительные параметры конфигурации помимо [настройки серьезности](configuration-options.md#severity-level). Например, каждый анализатор качества кода можно применять только к отдельным частям базы кода. Эти параметры задаются в формате пар "ключ — значение" в том же файле [EditorConfig](https://editorconfig.org), где и уровни серьезности для правил и общие параметры редактора.

## <a name="option-scopes"></a>Области параметров

Каждый параметр уточнения можно задать для всех правил, для определенной категории (например, безопасности или проектирования) или для конкретного правила.

### <a name="all-rules"></a>Все правила

Следующий синтаксис позволяет применить параметр для *всех* правил:

|Синтаксис|Пример|
|-|-|
| dotnet_code_quality.OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Категория правил

Следующий синтаксис позволяет применить параметр для одной [*категории* правил](categories.md):

|Синтаксис|Пример|
|-|-|
| dotnet_code_quality.RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Конкретное правило

Следующий синтаксис позволяет применить параметр для *конкретного* правила:

|Синтаксис|Пример|
|-|-|
| dotnet_code_quality.RuleId.OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="options"></a>Параметры

В этом разделе приведены некоторые из доступных параметров. Полный список доступных параметров см. на странице [Analyzer Configuration ](https://github.com/dotnet/roslyn-analyzers/blob/main/docs/Analyzer%20Configuration.md)(Конфигурация анализатора).

### <a name="api_surface"></a>api_surface

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Какая часть поверхности API будет анализироваться | `public`<br/>`internal` либо `friend`<br/>`private`<br/>`all`<br/><br/>Для разделения значений используйте запятые (,) | `public` | [CA1000](quality-rules/ca1000.md) [CA1003](quality-rules/ca1003.md) [CA1008](quality-rules/ca1008.md) [CA1010](quality-rules/ca1010.md)<br/>[CA1012](quality-rules/ca1012.md) [CA1024](quality-rules/ca1024.md) [CA1027](quality-rules/ca1027.md) [CA1028](quality-rules/ca1028.md)<br/>[CA1030](quality-rules/ca1030.md) [CA1036](quality-rules/ca1036.md) [CA1040](quality-rules/ca1040.md) [CA1041](quality-rules/ca1041.md)<br/>[CA1043](quality-rules/ca1043.md) [CA1044](quality-rules/ca1044.md) [CA1051](quality-rules/ca1051.md) [CA1052](quality-rules/ca1052.md)<br/>[CA1054](quality-rules/ca1054.md) [CA1055](quality-rules/ca1055.md) [CA1056](quality-rules/ca1056.md) [CA1058](quality-rules/ca1058.md)<br/>[CA1063](quality-rules/ca1063.md) [CA1708](quality-rules/ca1708.md) [CA1710](quality-rules/ca1710.md) [CA1711](quality-rules/ca1711.md)<br/>[CA1714](quality-rules/ca1714.md) [CA1715](quality-rules/ca1715.md) [CA1716](quality-rules/ca1716.md) [CA1717](quality-rules/ca1717.md)<br/>[CA1720](quality-rules/ca1720.md) [CA1721](quality-rules/ca1721.md) [CA1725](quality-rules/ca1725.md) [CA1801](quality-rules/ca1801.md)<br/>[CA1802](quality-rules/ca1802.md) [CA1815](quality-rules/ca1815.md) [CA1819](quality-rules/ca1819.md) [CA2217](quality-rules/ca2217.md)<br/>[CA2225](quality-rules/ca2225.md) [CA2226](quality-rules/ca2226.md) [CA2231](quality-rules/ca2231.md) [CA2234](quality-rules/ca2234.md)<br/>|

### <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Нужно ли игнорировать асинхронные методы, которые не возвращают значений | `true`<br/>`false` | `false` | [CA2007](quality-rules/ca2007.md) |

> [!NOTE]
> Этот параметр именовался `skip_async_void_methods` в более ранней версии.

### <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Нужно ли исключать из правила односимвольные [параметры типа](../../csharp/programming-guide/generics/generic-type-parameters.md), как например `S` в `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](quality-rules/ca1715.md) |

> [!NOTE]
> Этот параметр именовался `allow_single_letter_type_parameters` в более ранней версии.

### <a name="output_kind"></a>output_kind

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Указывает, что нужно анализировать код в проекте, который создает сборку указанного типа | Одно или несколько полей перечисления <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>Для разделения значений используйте запятые (,) | Все типы выходных данных | [CA2007](quality-rules/ca2007.md) |

### <a name="required_modifiers"></a>required_modifiers

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Указывает обязательные модификаторы для API, которые нужно анализировать | Одно или несколько значений из приведенной ниже таблицы допустимых модификаторов<br/><br/>Для разделения значений используйте запятые (,) | Зависит от конкретного правила | [CA1802](quality-rules/ca1802.md) |

| Допустимый модификатор | Сводка |
| --- | --- |
| `none` | Нет требований к модификатору |
| `static` либо `Shared` | Должен быть объявлен как `static` (или `Shared` в Visual Basic) |
| `const` | Должен быть объявлен как `const` |
| `readonly` | Должен быть объявлен как `readonly` |
| `abstract` | Должен быть объявлен как `abstract` |
| `virtual` | Должен быть объявлен как `virtual` |
| `override` | Должен быть объявлен как `override` |
| `sealed` | Должен быть объявлен как `sealed` |
| `extern` | Должен быть объявлен как `extern` |
| `async` | Должен быть объявлен как `async` |

### <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Нужно ли пропускать анализ для параметра `this` в методах расширения | `true`<br/>`false` | `false` | [CA1062](quality-rules/ca1062.md) |

### <a name="null_check_validation_methods"></a>null_check_validation_methods

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Имена методов проверки на значение NULL, которые проверяют отсутствие значений NULL в аргументах, передаваемых в метод | Допустимые форматы имен методов (разделенные `|`):<br/> — только имя метода (включает все методы с этим именем, любого типа и в любом пространстве имен);<br/> — полные имена в [формате идентификатора документации](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format) для символа с необязательным префиксом `M:`. | Отсутствуют | [CA1062](quality-rules/ca1062.md) |

### <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Имена дополнительных методов форматирования строк | Допустимые форматы имен методов (разделенные `|`):<br/> — только имя метода (включает все методы с этим именем, любого типа и в любом пространстве имен);<br/> — полные имена в [формате идентификатора документации](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format) для символа с необязательным префиксом `M:`. | Отсутствуют | [CA2241](quality-rules/ca2241.md) |

### <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Имена типов (включая все производные типы), исключаемых из анализа | Допустимые форматы имен символов (разделенные `|`):<br/> — только имя типа (включает все типы с этим именем, любого типа и в любом пространстве имен);<br/> — полные имена в [формате идентификатора документации](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format) для символа с необязательным префиксом `T:`. | Отсутствуют | [CA1303](quality-rules/ca1303.md) |

### <a name="excluded_symbol_names"></a>excluded_symbol_names

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Имена символов, исключаемых из анализа | Допустимые форматы имен символов (разделенные `|`):<br/> — только имя символа (включает все символы с этим именем, любого типа и в любом пространстве имен);<br/> — полные имена в [формате идентификатора документации](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format) для символа. Для каждого имени символа требуется префикс вида символа, например префикс `M:` для методов, префикс `T:` для типов и префикс `N:` для пространств имен.<br/> - `.ctor` используется для конструкторов, а `.cctor` — для статических конструкторов | Отсутствуют | [CA1062](quality-rules/ca1062.md) [CA1303](quality-rules/ca1303.md) [CA2000](quality-rules/ca2000.md) [CA2100](quality-rules/ca2100.md) [CA2301](quality-rules/ca2301.md) [CA2302](quality-rules/ca2302.md)<br/>[CA2311](quality-rules/ca2311.md) [CA2312](quality-rules/ca2312.md) [CA2321](quality-rules/ca2321.md) [CA2322](quality-rules/ca2322.md) [CA2327](quality-rules/ca2327.md) [CA2328](quality-rules/ca2328.md)<br/>[CA2329](quality-rules/ca2329.md) [CA2330](quality-rules/ca2330.md) [CA3001](quality-rules/ca3001.md) [CA3002](quality-rules/ca3002.md) [CA3003](quality-rules/ca3003.md) [CA3004](quality-rules/ca3004.md)<br/>[CA3005](quality-rules/ca3005.md) [CA3006](quality-rules/ca3006.md) [CA3007](quality-rules/ca3007.md) [CA3008](quality-rules/ca3008.md) [CA3009](quality-rules/ca3009.md) [CA3010](quality-rules/ca3010.md)<br/>[CA3011](quality-rules/ca3011.md) [CA3012](quality-rules/ca3012.md) [CA5361](quality-rules/ca5361.md) CA5376 CA5377 [CA5378](quality-rules/ca5378.md)<br/>[CA5380](quality-rules/ca5380.md) [CA5381](quality-rules/ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](quality-rules/ca5389.md) CA5390 |

### <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Описание | Допустимые значения | Значение по умолчанию | Настраиваемые правила |
| - | - | - | - |
| Имена символов, запрещенных в контексте анализа | Допустимые форматы имен символов (разделенные `|`):<br/> — только имя символа (включает все символы с этим именем, любого типа и в любом пространстве имен);<br/> — полные имена в [формате идентификатора документации](/dotnet/csharp/language-reference/language-specification/documentation-comments#id-string-format) для символа. Для каждого имени символа требуется префикс вида символа, например префикс `M:` для методов, префикс `T:` для типов и префикс `N:` для пространств имен.<br/> - `.ctor` используется для конструкторов, а `.cctor` — для статических конструкторов | Отсутствуют | [CA1031](quality-rules/ca1031.md) |
