---
title: Правила именования для стиля кода
description: Сведения о правилах стиля кода в .NET для именования элементов кода.
ms.date: 09/25/2020
ms.topic: reference
author: gewarren
ms.author: gewarren
dev_langs:
- CSharp
- VB
f1_keywords:
- IDE1006
- naming rules
helpviewer_keywords:
- IDE1006
- naming code style rules [EditorConfig]
- naming rules
- EditorConfig naming conventions
ms.openlocfilehash: a61d0ca8684134207a11f79e382b6aaf843ba956
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873254"
---
# <a name="naming-rules"></a>Правила именования

В файле `.editorconfig` можно определить **правила именования**, которые определяют и принудительно применяют требования к именам для таких элементов кода в языке программирования .NET, как классы, свойства и методы. Например, вы можете потребовать использовать только прописные буквы для открытых элементов или префикс `_` для закрытых полей.

Правило именования включает три следующих компонента:

* **Группа символов**, к которой применяется это правило, например открытые элементы или закрытые поля.
* **Стиль именования**, связываемый с этим правилом, например обязательное использование прописных букв или использование символа подчеркивания в качестве первого символа имени.
* Уровень серьезности для применения соглашения.

Во-первых, необходимо указать группу символов и стиль именования, а также присвоить заголовок каждому из них. Затем укажите правило именования, которое связывает их.

## <a name="general-syntax"></a>Общий синтаксис

Чтобы определить правило именования, группу символов или стиль именования, задайте одно или несколько свойств с помощью следующего синтаксиса:

```ini
<kind>.<title>.<propertyName> = <propertyValue>
```

Каждое свойство может быть задано только один раз, но некоторые параметры допускают несколько значений, разделенных запятыми.

Порядок свойств не имеет значения.

### \<kind>

**\<kind>** определяет, какие элементы определяются (правило именования, группа символов или стиль именования), и может принимать следующие значения:

| Для чего задается свойство | Используйте значение \<kind> | Пример |
| --- | --- | -- |
| Правило именования | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| Группа символов | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| Стиль именования | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

Каждый тип определения (для [правила именования](#naming-rule-properties), [группы символов](#symbol-group-properties) или [стиля именования](#naming-style-properties)) поддерживает свой набор свойств, которые описаны в следующих разделах.

### \<title>

**\<title>** содержит выбранное вами описательное имя, которое объединяет несколько параметров свойств в одно определение. Например, следующие свойства создают два определения группы символов (`interface` и `types`) и устанавливают для каждого из них два свойства.

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a>Свойства правила именования

Чтобы правило вступило в силу, должны быть указаны все свойства правила именования.

| Свойство | Описание |
| -- | -- |
| `symbols` | Заголовок группы символов, к символам которой будет применено правило именования |
| `style` | Заголовок стиля именования, который должен быть связан с этим правилом |
| `severity` |  Задает серьезность, с которой будет применяться это правило именования. Задает для сопоставленного значения один из доступных [уровней серьезности](../configuration-options.md#severity-level)<sup>1</sup> |

**Примечания.**

1. Спецификация серьезности в правиле именования учитывается только в интегрированных средах разработки, таких как Visual Studio. Компиляторы C# или VB не понимают этот параметр и не учитывают его при сборке. Чтобы применить правила стиля именования к сборке, уровень серьезности следует задать с помощью [конфигурации серьезности в правиле кода](#rule-id-ide1006-naming-rule-violation). См. дополнительные сведения на [сайте GitHub](https://github.com/dotnet/roslyn/issues/44201).

## <a name="symbol-group-properties"></a>Свойства группы символов

Для групп символов можно задать следующие свойства, которые ограничивают набор включаемых в группу символов. Чтобы указать для одного свойства несколько значений, разделите их запятыми.

| Свойство | Описание | Допустимые значения | Обязательно |
| -- | -- | -- | -- |
| `applicable_kinds` | Типы символов в группе <sup>1</sup> | `*` (используйте это значение, чтобы указать все символы)<br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | Да |
| `applicable_accessibilities` | Уровни доступности для символов в группе | `*` (используйте это значение, чтобы указать все уровни доступа)<br/>`public`<br/>`internal` либо `friend`<br/>`private`<br/>`protected`<br/>`protected_internal` или `protected_friend`<br/>`private_protected`<br/>`local` (для символов, определенных в методе) | Да |
| `required_modifiers` | Соответствует только тем символам, у которых есть _все_ указанные модификаторы <sup>2</sup> | `abstract` либо `must_inherit`<br/>`async`<br/>`const`<br/>`readonly`<br/>`static` или `shared` <sup>3</sup> | Нет |

**Примечания.**

1. Элементы кортежа в настоящее время поддерживаются только в `applicable_kinds`.
2. Группа символов сопоставляет _все_ модификаторы в свойстве `required_modifiers`.  Если вы опустите это свойство, для сопоставления не требуются конкретные модификаторы. Это означает, что модификаторы символов не оказывают влияния на применение этого правила.
3. Если группа имеет значение `static` или `shared` в свойстве `required_modifiers`, в нее будут включены также символы `const`, так как они неявно являются `static`/`Shared`. Но если вы не хотите применять правило именования `static` к символам `const`, вы можете создать новое правило именования для группы символов `const`.

## <a name="naming-style-properties"></a>Свойства стиля именования

Стиль именования определяет соглашения, которые будут применяться к правилу. Например:

* Использование прописных букв `PascalCase`
* Начинается с `m_`
* Заканчивается на `_g`
* Разделение слов с помощью `__`

Для стиля именования можно задать следующие свойства:

| Свойство | Описание | Допустимые значения | Обязательно |
| -- | -- | -- | -- |
| `capitalization` | Стиль применения прописных букв для слов в пределах символа | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | Да<sup>1</sup> |
| `required_prefix` | Должно начинаться с этих символов | | Нет |
| `required_suffix` | Должно заканчиваться этими символами | | Нет |
| `word_separator` | Слова внутри символа должны разделяться этим символом | | Нет |

**Примечания.**

1. Указать регистр букв для стиля именования обязательно, в противном случае ваш стиль может игнорироваться.

## <a name="rule-order"></a>Порядок правил

Порядок определения правил в файле EditorConfig не имеет значения. Все правила именования автоматически упорядочиваются в соответствии с определениями самих правил. [Расширение языковой службы EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) может анализировать файл EditorConfig и сообщать о случаях, когда порядок правил в файле отличается от того, который будет использоваться компилятором во время выполнения.

> [!NOTE]
>
> Если вы используете более раннюю версию Visual Studio, чем Visual Studio 2019 версии 16.2, правила именования в файле EditorConfig должны быть упорядочены от более конкретных к более общим. Применяться будет только первое обнаруженное правило. Но при наличии множества *свойств* правил с одним и тем же именем приоритет будет иметь последнее обнаруженное свойство с таким именем. См. подробнее об [иерархии файлов и приоритетности](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).

## <a name="default-naming-styles"></a>Стили именования по умолчанию

Если вы не укажете никаких пользовательских правил именования, применяются следующие стили по умолчанию:

- Для классов, структур, перечислений, свойств и событий со специальными параметрами `public`, `private`, `internal`, `protected` или `protected_internal` по умолчанию используется стиль именования Pascal.

- Для интерфейсов со специальными параметрами `public`, `private`, `internal`, `protected` или `protected_internal` по умолчанию используется стиль именования Pascal с обязательным префиксом **I**.

## <a name="code-rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a>Идентификатор правила кода: `IDE1006 (Naming rule violation)`

Все параметры именования имеют идентификатор правила `IDE1006` и заголовок `Naming rule violation`. Серьезность для нарушений именования можно настроить глобально в файле EditorConfig, используя следующий синтаксис:

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

Серьезность должна иметь значение `warning` или `error`, чтобы [принудительно применяться при сборке](../overview.md#code-style-analysis). Все возможные значения серьезности перечислены на странице [об уровнях серьезности](../configuration-options.md#severity-level).

## <a name="example"></a>Пример

Ниже представлен файл *EDITORCONFIG* с соглашением об именовании, в котором указано, что общедоступные свойства, методы, поля, события и делегаты должны начинаться с прописной буквы. Обратите внимание, что это соглашение об именовании указывает несколько типов символов, к которым применяется правило, через запятую.

```ini
[*.{cs,vb}]

# Defining the 'public_symbols' symbol group
dotnet_naming_symbols.public_symbols.applicable_kinds           = property,method,field,event,delegate
dotnet_naming_symbols.public_symbols.applicable_accessibilities = public
dotnet_naming_symbols.public_symbols.required_modifiers         = readonly

# Defining the `first_word_upper_case_style` naming style
dotnet_naming_style.first_word_upper_case_style.capitalization = first_word_upper

# Defining the `public_members_must_be_capitalized` naming rule, by setting the symbol group to the 'public symbols' symbol group,
dotnet_naming_rule.public_members_must_be_capitalized.symbols   = public_symbols
# setting the naming style to the `first_word_upper_case_style` naming style,
dotnet_naming_rule.public_members_must_be_capitalized.style    = first_word_upper_case_style
# and setting the severity.
dotnet_naming_rule.public_members_must_be_capitalized.severity = suggestion
```

## <a name="see-also"></a>См. также

- [Правила языка](language-rules.md)
- [Правила форматирования](formatting-rules.md)
- [Правила именования Roslyn](https://github.com/dotnet/roslyn/blob/main/.editorconfig#L63)
- [Справочник по правилам стиля кода для .NET](index.md)
