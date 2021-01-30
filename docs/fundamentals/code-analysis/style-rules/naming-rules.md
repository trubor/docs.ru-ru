---
title: Правила именования стилей кода
description: Сведения о правилах стиля кода .NET для именования элементов кода.
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
ms.openlocfilehash: 1fce275204b729b4d23729ca432e06a5a249620d
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065139"
---
# <a name="naming-rules"></a><span data-ttu-id="43011-103">Правила именования</span><span class="sxs-lookup"><span data-stu-id="43011-103">Naming rules</span></span>

<span data-ttu-id="43011-104">В `.editorconfig` файле можно определить **правила именования** , определяющие, каким образом элементы кода языка программирования .NET &mdash; , такие как классы, свойства и методы, &mdash; должны называться.</span><span class="sxs-lookup"><span data-stu-id="43011-104">In your `.editorconfig` file, you can define **naming rules** for how .NET programming language code elements&mdash;such as classes, properties, and methods&mdash;should be named.</span></span> <span data-ttu-id="43011-105">Например, можно указать, что открытые члены должны иметь прописные буквы или что закрытые поля должны начинаться с `_` .</span><span class="sxs-lookup"><span data-stu-id="43011-105">For example, you can specify that public members must be capitalized, or that private fields must begin with `_`.</span></span>

<span data-ttu-id="43011-106">Правило именования имеет три компонента:</span><span class="sxs-lookup"><span data-stu-id="43011-106">A naming rule has three components:</span></span>

* <span data-ttu-id="43011-107">**Группа символов** группа &mdash; символов, к которой применяется правило.</span><span class="sxs-lookup"><span data-stu-id="43011-107">The **symbol group**&mdash;the group of symbols the rule applies to.</span></span>
* <span data-ttu-id="43011-108">**Стиль именования** , связываемый с правилом.</span><span class="sxs-lookup"><span data-stu-id="43011-108">The **naming style** to associate with the rule.</span></span>
* <span data-ttu-id="43011-109">Уровень серьезности для применения соглашения.</span><span class="sxs-lookup"><span data-stu-id="43011-109">The severity for enforcing the convention.</span></span>

## <a name="general-syntax"></a><span data-ttu-id="43011-110">Общий синтаксис</span><span class="sxs-lookup"><span data-stu-id="43011-110">General syntax</span></span>

<span data-ttu-id="43011-111">Чтобы определить правило именования, группу символов или стиль именования, задайте одно или несколько свойств с помощью следующего синтаксиса:</span><span class="sxs-lookup"><span data-stu-id="43011-111">To define a naming rule, symbol group, or naming style, set one or more properties using the following syntax:</span></span>

```ini
<kind>.<title>.<propertyName> = <propertyValue>
```

<span data-ttu-id="43011-112">Каждое свойство должно быть задано только один раз, но некоторые параметры допускают несколько значений, разделенных запятыми.</span><span class="sxs-lookup"><span data-stu-id="43011-112">Each property should only be set once, but some settings allow multiple, comma-separated values.</span></span>

<span data-ttu-id="43011-113">Порядок свойств не имеет значения.</span><span class="sxs-lookup"><span data-stu-id="43011-113">The order of the properties is not important.</span></span>

### \<kind>

<span data-ttu-id="43011-114">**\<kind>** Указывает, какой тип элемента определяется &mdash; правилом именования, группой символов или стилем именования, &mdash; и должен быть одним из следующих:</span><span class="sxs-lookup"><span data-stu-id="43011-114">**\<kind>** specifies which kind of element is being defined&mdash;naming rule, symbol group, or naming style&mdash;and must be one of the following:</span></span>

| <span data-ttu-id="43011-115">Установка свойства для</span><span class="sxs-lookup"><span data-stu-id="43011-115">To set a property for</span></span> | <span data-ttu-id="43011-116">Использовать \<kind> значение</span><span class="sxs-lookup"><span data-stu-id="43011-116">Use the \<kind> value</span></span> | <span data-ttu-id="43011-117">Пример</span><span class="sxs-lookup"><span data-stu-id="43011-117">Example</span></span> |
| --- | --- | -- |
| <span data-ttu-id="43011-118">Правило именования</span><span class="sxs-lookup"><span data-stu-id="43011-118">Naming rule</span></span> | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| <span data-ttu-id="43011-119">Группа символов</span><span class="sxs-lookup"><span data-stu-id="43011-119">Symbol group</span></span> | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| <span data-ttu-id="43011-120">Стиль именования</span><span class="sxs-lookup"><span data-stu-id="43011-120">Naming style</span></span> | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

<span data-ttu-id="43011-121">Каждый тип &mdash; [правила именования](#naming-rule-properties)определений, [группы символов](#symbol-group-properties)или [стиля именования](#naming-style-properties) &mdash; имеет собственные Поддерживаемые свойства, как описано в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="43011-121">Each type of definition&mdash;[naming rule](#naming-rule-properties), [symbol group](#symbol-group-properties), or [naming style](#naming-style-properties)&mdash;has its own supported properties, as described in the following sections.</span></span>

### \<title>

<span data-ttu-id="43011-122">**\<title>** описательное имя, которое связывает несколько параметров свойств с одним определением.</span><span class="sxs-lookup"><span data-stu-id="43011-122">**\<title>** is a descriptive name you choose that associates multiple property settings into a single definition.</span></span> <span data-ttu-id="43011-123">Например, следующие свойства создают два определения группы символов, `interface` и `types` для каждого из них установлены два свойства.</span><span class="sxs-lookup"><span data-stu-id="43011-123">For example, the following properties produce two symbol group definitions, `interface` and `types`, each of which has two properties set on it.</span></span>

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a><span data-ttu-id="43011-124">Свойства правила именования</span><span class="sxs-lookup"><span data-stu-id="43011-124">Naming rule properties</span></span>

<span data-ttu-id="43011-125">Чтобы правило вступило в силу, требуются все свойства правил именования.</span><span class="sxs-lookup"><span data-stu-id="43011-125">All naming rule properties are required for a rule to take effect.</span></span>

| <span data-ttu-id="43011-126">Свойство</span><span class="sxs-lookup"><span data-stu-id="43011-126">Property</span></span> | <span data-ttu-id="43011-127">Описание</span><span class="sxs-lookup"><span data-stu-id="43011-127">Description</span></span> |
| -- | -- |
| `symbols` | <span data-ttu-id="43011-128">Заголовок группы символов; правило именования будет применено к символам в этой группе</span><span class="sxs-lookup"><span data-stu-id="43011-128">The title of a symbol group; the naming rule will be applied to the symbols in this group</span></span> |
| `style` | <span data-ttu-id="43011-129">Заголовок стиля именования, который должен быть связан с этим правилом</span><span class="sxs-lookup"><span data-stu-id="43011-129">The title of the naming style which should be associated with this rule</span></span> |
| `severity` |  <span data-ttu-id="43011-130">Задает серьезность, с которой будет принудительно применяться правило именования.</span><span class="sxs-lookup"><span data-stu-id="43011-130">Sets the severity with which to enforce the naming rule.</span></span> <span data-ttu-id="43011-131">Задайте для связанного значения один из доступных [уровней серьезности](../configuration-options.md#severity-level). <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="43011-131">Set the associated value to one of the available [severity levels](../configuration-options.md#severity-level).<sup>1</sup></span></span> |

<span data-ttu-id="43011-132">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="43011-132">**Notes:**</span></span>

1. <span data-ttu-id="43011-133">Спецификация серьезности в правиле именования учитывается только в Ideах разработки, таких как Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="43011-133">Severity specification within a naming rule is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="43011-134">Этот параметр не понимается компиляторами C# или VB, поэтому он не учитывается во время сборки.</span><span class="sxs-lookup"><span data-stu-id="43011-134">This setting is not understood by the C# or VB compilers, hence not respected during build.</span></span> <span data-ttu-id="43011-135">Чтобы применить правила стиля именования к сборке, следует задать уровень серьезности с помощью [конфигурации серьезности правила кода](#rule-id-ide1006-naming-rule-violation).</span><span class="sxs-lookup"><span data-stu-id="43011-135">To enforce naming style rules on build, you should instead set the severity by using [code rule severity configuration](#rule-id-ide1006-naming-rule-violation).</span></span> <span data-ttu-id="43011-136">См. дополнительные сведения на [сайте GitHub](https://github.com/dotnet/roslyn/issues/44201).</span><span class="sxs-lookup"><span data-stu-id="43011-136">For more information, see this [GitHub issue](https://github.com/dotnet/roslyn/issues/44201).</span></span>

## <a name="symbol-group-properties"></a><span data-ttu-id="43011-137">Свойства группы символов</span><span class="sxs-lookup"><span data-stu-id="43011-137">Symbol group properties</span></span>

<span data-ttu-id="43011-138">Для групп символов можно задать следующие свойства, чтобы ограничить набор символов, включаемых в группу.</span><span class="sxs-lookup"><span data-stu-id="43011-138">You can set the following properties for symbol groups, to limit which symbols are included in the group.</span></span> <span data-ttu-id="43011-139">Чтобы указать несколько значений для одного свойства, разделяйте значения запятой.</span><span class="sxs-lookup"><span data-stu-id="43011-139">To specify multiple values for a single property, separate the values with a comma.</span></span>

| <span data-ttu-id="43011-140">Свойство</span><span class="sxs-lookup"><span data-stu-id="43011-140">Property</span></span> | <span data-ttu-id="43011-141">Описание</span><span class="sxs-lookup"><span data-stu-id="43011-141">Description</span></span> | <span data-ttu-id="43011-142">Допустимые значения</span><span class="sxs-lookup"><span data-stu-id="43011-142">Allowed values</span></span> | <span data-ttu-id="43011-143">Обязательно</span><span class="sxs-lookup"><span data-stu-id="43011-143">Required</span></span> |
| -- | -- | -- | -- |
| `applicable_kinds` | <span data-ttu-id="43011-144">Виды символов в группе <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="43011-144">Kinds of symbols in the group <sup>1</sup></span></span> | <span data-ttu-id="43011-145">`*` (используйте это значение, чтобы указать все символы)</span><span class="sxs-lookup"><span data-stu-id="43011-145">`*` (use this value to specify all symbols)</span></span><br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | <span data-ttu-id="43011-146">Да</span><span class="sxs-lookup"><span data-stu-id="43011-146">Yes</span></span> |
| `applicable_accessibilities` | <span data-ttu-id="43011-147">Уровни доступности символов в группе</span><span class="sxs-lookup"><span data-stu-id="43011-147">Accessibility levels of the symbols in the group</span></span> | <span data-ttu-id="43011-148">`*` (используйте это значение, чтобы указать все уровни доступа)</span><span class="sxs-lookup"><span data-stu-id="43011-148">`*` (use this value to specify all accessibility levels)</span></span><br/>`public`<br/><span data-ttu-id="43011-149">`internal` или `friend`</span><span class="sxs-lookup"><span data-stu-id="43011-149">`internal` or `friend`</span></span><br/>`private`<br/>`protected`<br/><span data-ttu-id="43011-150">`protected_internal` или `protected_friend`</span><span class="sxs-lookup"><span data-stu-id="43011-150">`protected_internal` or `protected_friend`</span></span><br/>`private_protected`<br/><span data-ttu-id="43011-151">`local` (для символов, определенных в методе)</span><span class="sxs-lookup"><span data-stu-id="43011-151">`local` (for symbols defined within a method)</span></span> | <span data-ttu-id="43011-152">Да</span><span class="sxs-lookup"><span data-stu-id="43011-152">Yes</span></span> |
| `required_modifiers` | <span data-ttu-id="43011-153">Сопоставлять только символы со _всеми_ указанными модификаторами <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="43011-153">Only match symbols with _all_ the specified modifiers <sup>2</sup></span></span> | <span data-ttu-id="43011-154">`abstract` или `must_inherit`</span><span class="sxs-lookup"><span data-stu-id="43011-154">`abstract` or `must_inherit`</span></span><br/>`async`<br/>`const`<br/>`readonly`<br/><span data-ttu-id="43011-155">`static` или `shared` <sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="43011-155">`static` or `shared` <sup>3</sup></span></span> | <span data-ttu-id="43011-156">Нет</span><span class="sxs-lookup"><span data-stu-id="43011-156">No</span></span> |

<span data-ttu-id="43011-157">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="43011-157">**Notes:**</span></span>

1. <span data-ttu-id="43011-158">В настоящее время элементы кортежа не поддерживаются в `applicable_kinds` .</span><span class="sxs-lookup"><span data-stu-id="43011-158">Tuple members aren't currently supported in `applicable_kinds`.</span></span>
2. <span data-ttu-id="43011-159">Группа символов соответствует _всем_ модификаторам в `required_modifiers` свойстве.</span><span class="sxs-lookup"><span data-stu-id="43011-159">The symbol group matches _all_ the modifiers in the `required_modifiers` property.</span></span>  <span data-ttu-id="43011-160">Если опустить это свойство, для совпадения не требуются специальные модификаторы.</span><span class="sxs-lookup"><span data-stu-id="43011-160">If you omit this property, no specific modifiers are required for a match.</span></span> <span data-ttu-id="43011-161">Это означает, что модификаторы символов не оказывают влияния на применение этого правила.</span><span class="sxs-lookup"><span data-stu-id="43011-161">This means a symbol's modifiers have no effect on whether or not this rule is applied.</span></span>
3. <span data-ttu-id="43011-162">Если группа имеет `static` свойство или `shared` в `required_modifiers` свойстве, Группа также будет включать `const` символы, так как они являются неявными `static` / `Shared` .</span><span class="sxs-lookup"><span data-stu-id="43011-162">If your group has `static` or `shared` in the `required_modifiers` property, the group will also include `const` symbols because they are implicitly `static`/`Shared`.</span></span> <span data-ttu-id="43011-163">Однако если вы не хотите `static` применять правило именования к `const` символам, можно создать новое правило именования с группой символов `const` .</span><span class="sxs-lookup"><span data-stu-id="43011-163">However, if you don't want the `static` naming rule to apply to `const` symbols, you can create a new naming rule with a symbol group of `const`.</span></span>

## <a name="naming-style-properties"></a><span data-ttu-id="43011-164">Именование свойств стиля</span><span class="sxs-lookup"><span data-stu-id="43011-164">Naming style properties</span></span>

<span data-ttu-id="43011-165">Стиль именования определяет соглашения, которые необходимо применить к правилу.</span><span class="sxs-lookup"><span data-stu-id="43011-165">A naming style defines the conventions you want to enforce with the rule.</span></span> <span data-ttu-id="43011-166">Например:</span><span class="sxs-lookup"><span data-stu-id="43011-166">For example:</span></span>

* <span data-ttu-id="43011-167">С прописной буквы `PascalCase`</span><span class="sxs-lookup"><span data-stu-id="43011-167">Capitalize with `PascalCase`</span></span>
* <span data-ttu-id="43011-168">Начинается с `m_`</span><span class="sxs-lookup"><span data-stu-id="43011-168">Starts with `m_`</span></span>
* <span data-ttu-id="43011-169">Заканчивается на `_g`</span><span class="sxs-lookup"><span data-stu-id="43011-169">Ends with `_g`</span></span>
* <span data-ttu-id="43011-170">Разделять слова с помощью `__`</span><span class="sxs-lookup"><span data-stu-id="43011-170">Separate words with `__`</span></span>

<span data-ttu-id="43011-171">Для стиля именования можно задать следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="43011-171">You can set the following properties for a naming style:</span></span>

| <span data-ttu-id="43011-172">Свойство</span><span class="sxs-lookup"><span data-stu-id="43011-172">Property</span></span> | <span data-ttu-id="43011-173">Описание</span><span class="sxs-lookup"><span data-stu-id="43011-173">Description</span></span> | <span data-ttu-id="43011-174">Допустимые значения</span><span class="sxs-lookup"><span data-stu-id="43011-174">Allowed values</span></span> | <span data-ttu-id="43011-175">Обязательно</span><span class="sxs-lookup"><span data-stu-id="43011-175">Required</span></span> |
| -- | -- | -- | -- |
| `capitalization` | <span data-ttu-id="43011-176">Стиль капитализации для слов внутри символа</span><span class="sxs-lookup"><span data-stu-id="43011-176">Capitalization style for words within the symbol</span></span> | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | <span data-ttu-id="43011-177">Да<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="43011-177">Yes<sup>1</sup></span></span> |
| `required_prefix` | <span data-ttu-id="43011-178">Должно начинаться с этих символов</span><span class="sxs-lookup"><span data-stu-id="43011-178">Must begin with these characters</span></span> | | <span data-ttu-id="43011-179">Нет</span><span class="sxs-lookup"><span data-stu-id="43011-179">No</span></span> |
| `required_suffix` | <span data-ttu-id="43011-180">Должен заканчиваться этими символами</span><span class="sxs-lookup"><span data-stu-id="43011-180">Must end with these characters</span></span> | | <span data-ttu-id="43011-181">Нет</span><span class="sxs-lookup"><span data-stu-id="43011-181">No</span></span> |
| `word_separator` | <span data-ttu-id="43011-182">Слова внутри символа должны быть разделены этим символом</span><span class="sxs-lookup"><span data-stu-id="43011-182">Words within the symbol need to be separated with this character</span></span> | | <span data-ttu-id="43011-183">Нет</span><span class="sxs-lookup"><span data-stu-id="43011-183">No</span></span> |

<span data-ttu-id="43011-184">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="43011-184">**Notes:**</span></span>

1. <span data-ttu-id="43011-185">Указать регистр букв для стиля именования обязательно, в противном случае ваш стиль может игнорироваться.</span><span class="sxs-lookup"><span data-stu-id="43011-185">You must specify a capitalization style as part of your naming style, otherwise your naming style might be ignored.</span></span>

## <a name="rule-order"></a><span data-ttu-id="43011-186">Порядок правил</span><span class="sxs-lookup"><span data-stu-id="43011-186">Rule order</span></span>

<span data-ttu-id="43011-187">Порядок, в котором правила именования определяются в файле EditorConfig, не имеет значения.</span><span class="sxs-lookup"><span data-stu-id="43011-187">The order in which naming rules are defined in an EditorConfig file doesn't matter.</span></span> <span data-ttu-id="43011-188">Правила именования автоматически упорядочиваются в соответствии с определением самих правил.</span><span class="sxs-lookup"><span data-stu-id="43011-188">The naming rules are automatically ordered according to the definition of the rules themselves.</span></span> <span data-ttu-id="43011-189">[Расширение языковой службы EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) может анализировать файл EditorConfig и сообщать о случаях, когда порядок правил в файле отличается от того, который будет использоваться компилятором во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="43011-189">The [EditorConfig Language Service extension](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) can analyze an EditorConfig file and report cases where the rule ordering in the file is different to what the compiler will use at run time.</span></span>

> [!NOTE]
>
> <span data-ttu-id="43011-190">Если вы используете более раннюю версию Visual Studio, чем Visual Studio 2019 версии 16,2, правила именования должны быть упорядочены от наиболее специфичных к наименее конкретных в файле EditorConfig.</span><span class="sxs-lookup"><span data-stu-id="43011-190">If you're using a version of Visual Studio earlier than Visual Studio 2019 version 16.2, naming rules should be ordered from most-specific to least-specific in the EditorConfig file.</span></span> <span data-ttu-id="43011-191">Применяться будет только первое обнаруженное правило.</span><span class="sxs-lookup"><span data-stu-id="43011-191">The first rule encountered that can be applied is the only rule that is applied.</span></span> <span data-ttu-id="43011-192">Но при наличии множества *свойств* правил с одним и тем же именем приоритет будет иметь последнее обнаруженное свойство с таким именем.</span><span class="sxs-lookup"><span data-stu-id="43011-192">However, if there are multiple rule *properties* with the same name, the most recently found property with that name takes precedence.</span></span> <span data-ttu-id="43011-193">См. подробнее об [иерархии файлов и приоритетности](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span><span class="sxs-lookup"><span data-stu-id="43011-193">For more information, see [File hierarchy and precedence](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span></span>

## <a name="default-naming-styles"></a><span data-ttu-id="43011-194">Стили именования по умолчанию</span><span class="sxs-lookup"><span data-stu-id="43011-194">Default naming styles</span></span>

<span data-ttu-id="43011-195">Если не указать никаких пользовательских правил именования, используются следующие стили по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="43011-195">If you don't specify any custom naming rules, the following default styles are used:</span></span>

- <span data-ttu-id="43011-196">Для классов, структур, перечислений, свойств и событий со специальными параметрами `public`, `private`, `internal`, `protected` или `protected_internal` по умолчанию используется стиль именования Pascal.</span><span class="sxs-lookup"><span data-stu-id="43011-196">For classes, structs, enumerations, properties, and events with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case.</span></span>

- <span data-ttu-id="43011-197">Для интерфейсов со специальными параметрами `public`, `private`, `internal`, `protected` или `protected_internal` по умолчанию используется стиль именования Pascal с обязательным префиксом **I**.</span><span class="sxs-lookup"><span data-stu-id="43011-197">For interfaces with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case with a required prefix of **I**.</span></span>

## <a name="code-rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a><span data-ttu-id="43011-198">Идентификатор правила кода: `IDE1006 (Naming rule violation)`</span><span class="sxs-lookup"><span data-stu-id="43011-198">Code Rule ID: `IDE1006 (Naming rule violation)`</span></span>

<span data-ttu-id="43011-199">Все параметры именования имеют идентификатор `IDE1006` и заголовок правила `Naming rule violation` .</span><span class="sxs-lookup"><span data-stu-id="43011-199">All naming options have rule ID `IDE1006` and title `Naming rule violation`.</span></span> <span data-ttu-id="43011-200">Серьезность нарушений именования можно настроить глобально в файле EditorConfig, используя следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="43011-200">You can configure the severity of naming violations globally in an EditorConfig file with the following syntax:</span></span>

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

<span data-ttu-id="43011-201">Значение серьезности должно быть `warning` или `error` [принудительно применено при сборке](../overview.md#code-style-analysis).</span><span class="sxs-lookup"><span data-stu-id="43011-201">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="43011-202">Все возможные значения серьезности см. в разделе [уровень серьезности](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="43011-202">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="example"></a><span data-ttu-id="43011-203">Пример</span><span class="sxs-lookup"><span data-stu-id="43011-203">Example</span></span>

<span data-ttu-id="43011-204">Ниже представлен файл *EDITORCONFIG* с соглашением об именовании, в котором указано, что общедоступные свойства, методы, поля, события и делегаты должны начинаться с прописной буквы.</span><span class="sxs-lookup"><span data-stu-id="43011-204">The following *.editorconfig* file contains a naming convention that specifies that public properties, methods, fields, events, and delegates must be capitalized.</span></span> <span data-ttu-id="43011-205">Обратите внимание, что это соглашение об именовании указывает несколько типов символов, к которым применяется правило, через запятую.</span><span class="sxs-lookup"><span data-stu-id="43011-205">Notice that this naming convention specifies multiple kinds of symbol to apply the rule to, using a comma to separate the values.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="43011-206">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="43011-206">See also</span></span>

- [<span data-ttu-id="43011-207">Правила языка</span><span class="sxs-lookup"><span data-stu-id="43011-207">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="43011-208">Правила форматирования</span><span class="sxs-lookup"><span data-stu-id="43011-208">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="43011-209">Правила именования Roslyn</span><span class="sxs-lookup"><span data-stu-id="43011-209">Roslyn naming rules</span></span>](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [<span data-ttu-id="43011-210">Справочник по правилам стиля кода .NET</span><span class="sxs-lookup"><span data-stu-id="43011-210">.NET code style rules reference</span></span>](index.md)
