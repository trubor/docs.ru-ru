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
ms.openlocfilehash: 8ce209e64ee7f9f9028c221daedef8fc6a993ef7
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96594161"
---
# <a name="naming-rules"></a><span data-ttu-id="6b563-103">Правила именования</span><span class="sxs-lookup"><span data-stu-id="6b563-103">Naming rules</span></span>

<span data-ttu-id="6b563-104">Правила именования касаются именования элементов кода языка программирования .NET, таких как классы, свойства и методы.</span><span class="sxs-lookup"><span data-stu-id="6b563-104">Naming rules concern the naming of .NET programming language code elements, such as classes, properties, and methods.</span></span> <span data-ttu-id="6b563-105">Например, можно указать, что открытые члены должны быть указаны прописными буквами или что закрытые поля должны начинаться с `_`.</span><span class="sxs-lookup"><span data-stu-id="6b563-105">For example, you can specify that public members must be capitalized or that private fields must begin with `_`.</span></span>

<span data-ttu-id="6b563-106">Правило именования состоит из трех частей:</span><span class="sxs-lookup"><span data-stu-id="6b563-106">A naming rule has three parts:</span></span>

* <span data-ttu-id="6b563-107">Группа символов, к которой он применяется.</span><span class="sxs-lookup"><span data-stu-id="6b563-107">The group of symbols it applies to.</span></span>
* <span data-ttu-id="6b563-108">Стиль именования, связываемый с правилом.</span><span class="sxs-lookup"><span data-stu-id="6b563-108">The naming style to associate with the rule.</span></span>
* <span data-ttu-id="6b563-109">Уровень серьезности для применения соглашения.</span><span class="sxs-lookup"><span data-stu-id="6b563-109">The severity for enforcing the convention.</span></span>

<span data-ttu-id="6b563-110">Правила именования определяются в файле EditorConfig.</span><span class="sxs-lookup"><span data-stu-id="6b563-110">You define naming rules in an EditorConfig file.</span></span>

## <a name="general-syntax"></a><span data-ttu-id="6b563-111">Общий синтаксис</span><span class="sxs-lookup"><span data-stu-id="6b563-111">General syntax</span></span>

<span data-ttu-id="6b563-112">Чтобы определить правило именования, группу символов или стиль именования, задайте одно или несколько свойств с помощью следующего синтаксиса:</span><span class="sxs-lookup"><span data-stu-id="6b563-112">To define a naming rule, symbol group, or naming style, set one or more properties using the following syntax:</span></span>

```ini
<prefix>.<title>.<propertyName> = <propertyValue>
```

<span data-ttu-id="6b563-113">Каждое свойство должно быть задано только один раз, но некоторые параметры допускают несколько значений, разделенных запятыми.</span><span class="sxs-lookup"><span data-stu-id="6b563-113">Each property should only be set once, but some settings allow multiple, comma-separated values.</span></span>

<span data-ttu-id="6b563-114">Порядок свойств не имеет значения.</span><span class="sxs-lookup"><span data-stu-id="6b563-114">The order of the properties is not important.</span></span>

### \<prefix>

<span data-ttu-id="6b563-115">**\<prefix>** Указывает, какой тип элемента определяется &mdash; правилом именования, группой символов или стилем именования, &mdash; и должен быть одним из следующих:</span><span class="sxs-lookup"><span data-stu-id="6b563-115">**\<prefix>** specifies which kind of element is being defined&mdash;naming rule, symbol group, or naming style&mdash;and must be one of the following:</span></span>

| <span data-ttu-id="6b563-116">Установка свойства для</span><span class="sxs-lookup"><span data-stu-id="6b563-116">To set a property for</span></span> | <span data-ttu-id="6b563-117">Использовать префикс</span><span class="sxs-lookup"><span data-stu-id="6b563-117">Use the prefix</span></span> | <span data-ttu-id="6b563-118">Пример</span><span class="sxs-lookup"><span data-stu-id="6b563-118">Example</span></span> |
| --- | --- | -- |
| <span data-ttu-id="6b563-119">Правило именования</span><span class="sxs-lookup"><span data-stu-id="6b563-119">Naming rule</span></span> | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| <span data-ttu-id="6b563-120">Группа символов</span><span class="sxs-lookup"><span data-stu-id="6b563-120">Symbol group</span></span> | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| <span data-ttu-id="6b563-121">Стиль именования</span><span class="sxs-lookup"><span data-stu-id="6b563-121">Naming style</span></span> | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

<span data-ttu-id="6b563-122">Каждый тип &mdash; [правила именования](#naming-rule-properties)определений, [группы символов](#symbol-group-properties)или [стиля именования](#naming-style-properties) &mdash; имеет собственные Поддерживаемые свойства, как описано в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="6b563-122">Each type of definition&mdash;[naming rule](#naming-rule-properties), [symbol group](#symbol-group-properties), or [naming style](#naming-style-properties)&mdash;has its own supported properties, as described in the following sections.</span></span>

### \<title>

<span data-ttu-id="6b563-123">**\<title>** описательное имя, которое связывает несколько параметров свойств с одним определением.</span><span class="sxs-lookup"><span data-stu-id="6b563-123">**\<title>** is a descriptive name you choose that associates multiple property settings into a single definition.</span></span> <span data-ttu-id="6b563-124">Например, следующие свойства создают два определения группы символов, `interface` и `types` для каждого из них установлены два свойства.</span><span class="sxs-lookup"><span data-stu-id="6b563-124">For example, the following properties produce two symbol group definitions, `interface` and `types`, each of which has two properties set on it.</span></span>

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a><span data-ttu-id="6b563-125">Свойства правила именования</span><span class="sxs-lookup"><span data-stu-id="6b563-125">Naming rule properties</span></span>

<span data-ttu-id="6b563-126">Чтобы правило вступило в силу, требуются все свойства правил именования.</span><span class="sxs-lookup"><span data-stu-id="6b563-126">All naming rule properties are required for a rule to take effect.</span></span>

| <span data-ttu-id="6b563-127">Свойство</span><span class="sxs-lookup"><span data-stu-id="6b563-127">Property</span></span> | <span data-ttu-id="6b563-128">Описание</span><span class="sxs-lookup"><span data-stu-id="6b563-128">Description</span></span> |
| -- | -- |
| `symbols` | <span data-ttu-id="6b563-129">Заголовок группы символов, определяющий символы, к которым должно применяться это правило</span><span class="sxs-lookup"><span data-stu-id="6b563-129">The title of the symbol group, defining the symbols to which this rule should be applied</span></span> |
| `style` | <span data-ttu-id="6b563-130">Заголовок стиля именования, который должен быть связан с этим правилом</span><span class="sxs-lookup"><span data-stu-id="6b563-130">The title of the naming style which should be associated with this rule</span></span> |
| `severity` |  <span data-ttu-id="6b563-131">Задает серьезность, с которой будет принудительно применяться правило именования.</span><span class="sxs-lookup"><span data-stu-id="6b563-131">Sets the severity with which to enforce the naming rule.</span></span> <span data-ttu-id="6b563-132">Задайте для связанного значения один из доступных [уровней серьезности](https://docs.microsoft.com/dotnet/fundamentals/code-analysis/configuration-options#severity-level). <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6b563-132">Set the associated value to one of the available [severity levels](https://docs.microsoft.com/dotnet/fundamentals/code-analysis/configuration-options#severity-level).<sup>1</sup></span></span> |

<span data-ttu-id="6b563-133">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="6b563-133">**Notes:**</span></span>

1. <span data-ttu-id="6b563-134">Спецификация серьезности в правиле именования учитывается только в Ideах разработки, таких как Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6b563-134">Severity specification within a naming rule is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="6b563-135">Этот параметр не понимается компиляторами C# или VB, поэтому он не учитывается во время сборки.</span><span class="sxs-lookup"><span data-stu-id="6b563-135">This setting is not understood by the C# or VB compilers, hence not respected during build.</span></span> <span data-ttu-id="6b563-136">Вместо этого для применения правил стиля именования при сборке необходимо задать уровень серьезности с помощью конфигурации серьезности на основе идентификатора правила, как описано в [этом разделе](#rule-id-ide1006-naming-rule-violation).</span><span class="sxs-lookup"><span data-stu-id="6b563-136">Instead, to enforce naming style rules on build, you should set the severity by using the rule ID-based severity configuration as explained in [this section](#rule-id-ide1006-naming-rule-violation).</span></span> <span data-ttu-id="6b563-137">См. дополнительные сведения на [сайте GitHub](https://github.com/dotnet/roslyn/issues/44201).</span><span class="sxs-lookup"><span data-stu-id="6b563-137">For more information, see this [GitHub issue](https://github.com/dotnet/roslyn/issues/44201).</span></span>

## <a name="rule-order"></a><span data-ttu-id="6b563-138">Порядок правил</span><span class="sxs-lookup"><span data-stu-id="6b563-138">Rule order</span></span>

<span data-ttu-id="6b563-139">Порядок, в котором правила именования определяются в файле EditorConfig, не имеет значения.</span><span class="sxs-lookup"><span data-stu-id="6b563-139">The order in which naming rules are defined in an EditorConfig file doesn't matter.</span></span> <span data-ttu-id="6b563-140">Правила именования автоматически упорядочиваются в соответствии с определением самих правил.</span><span class="sxs-lookup"><span data-stu-id="6b563-140">The naming rules are automatically ordered according to the definition of the rules themselves.</span></span> <span data-ttu-id="6b563-141">[Расширение языковой службы EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) может анализировать файл EditorConfig и сообщать о случаях, когда порядок правил в файле отличается от того, который будет использоваться компилятором во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="6b563-141">The [EditorConfig Language Service extension](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) can analyze an EditorConfig file and report cases where the rule ordering in the file is different to what the compiler will use at run time.</span></span>

> [!NOTE]
>
> <span data-ttu-id="6b563-142">Если вы используете более раннюю версию Visual Studio, чем Visual Studio 2019 версии 16,2, правила именования должны быть упорядочены от наиболее специфичных к наименее конкретных в файле EditorConfig.</span><span class="sxs-lookup"><span data-stu-id="6b563-142">If you're using a version of Visual Studio earlier than Visual Studio 2019 version 16.2, naming rules should be ordered from most-specific to least-specific in the EditorConfig file.</span></span> <span data-ttu-id="6b563-143">Применяться будет только первое обнаруженное правило.</span><span class="sxs-lookup"><span data-stu-id="6b563-143">The first rule encountered that can be applied is the only rule that is applied.</span></span> <span data-ttu-id="6b563-144">Но при наличии множества *свойств* правил с одним и тем же именем приоритет будет иметь последнее обнаруженное свойство с таким именем.</span><span class="sxs-lookup"><span data-stu-id="6b563-144">However, if there are multiple rule *properties* with the same name, the most recently found property with that name takes precedence.</span></span> <span data-ttu-id="6b563-145">См. подробнее об [иерархии файлов и приоритетности](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span><span class="sxs-lookup"><span data-stu-id="6b563-145">For more information, see [File hierarchy and precedence](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span></span>

## <a name="symbol-group-properties"></a><span data-ttu-id="6b563-146">Свойства группы символов</span><span class="sxs-lookup"><span data-stu-id="6b563-146">Symbol group properties</span></span>

<span data-ttu-id="6b563-147">Для групп символов можно задать следующие свойства, чтобы ограничить набор символов, включаемых в группу.</span><span class="sxs-lookup"><span data-stu-id="6b563-147">You can set the following properties for symbol groups, to limit which symbols are included in the group.</span></span> <span data-ttu-id="6b563-148">Чтобы указать несколько значений в одном параметре свойства, разделите их запятыми.</span><span class="sxs-lookup"><span data-stu-id="6b563-148">To specify multiple values in a single property setting, separate them with a comma.</span></span>

| <span data-ttu-id="6b563-149">Свойство</span><span class="sxs-lookup"><span data-stu-id="6b563-149">Property</span></span> | <span data-ttu-id="6b563-150">Описание</span><span class="sxs-lookup"><span data-stu-id="6b563-150">Description</span></span> | <span data-ttu-id="6b563-151">Допустимые значения</span><span class="sxs-lookup"><span data-stu-id="6b563-151">Allowed values</span></span> | <span data-ttu-id="6b563-152">Обязательно</span><span class="sxs-lookup"><span data-stu-id="6b563-152">Required</span></span> |
| -- | -- | -- | -- |
| `applicable_kinds` | <span data-ttu-id="6b563-153">Виды символов в группе <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6b563-153">Kinds of symbols in the group <sup>1</sup></span></span> | <span data-ttu-id="6b563-154">`*` (используйте это значение, чтобы указать все символы)</span><span class="sxs-lookup"><span data-stu-id="6b563-154">`*` (use this value to specify all symbols)</span></span><br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | <span data-ttu-id="6b563-155">Да</span><span class="sxs-lookup"><span data-stu-id="6b563-155">Yes</span></span> |
| `applicable_accessibilities` | <span data-ttu-id="6b563-156">Уровни доступности символов в группе</span><span class="sxs-lookup"><span data-stu-id="6b563-156">Accessibility levels of the symbols in the group</span></span> | <span data-ttu-id="6b563-157">`*` (используйте это значение, чтобы указать все уровни доступа)</span><span class="sxs-lookup"><span data-stu-id="6b563-157">`*` (use this value to specify all accessibility levels)</span></span><br/>`public`<br/><span data-ttu-id="6b563-158">`internal` или `friend`</span><span class="sxs-lookup"><span data-stu-id="6b563-158">`internal` or `friend`</span></span><br/>`private`<br/>`protected`<br/><span data-ttu-id="6b563-159">`protected_internal` или `protected_friend`</span><span class="sxs-lookup"><span data-stu-id="6b563-159">`protected_internal` or `protected_friend`</span></span><br/>`private_protected`<br/><span data-ttu-id="6b563-160">`local` (для символов, определенных в методе)</span><span class="sxs-lookup"><span data-stu-id="6b563-160">`local` (for symbols defined within a method)</span></span> | <span data-ttu-id="6b563-161">Да</span><span class="sxs-lookup"><span data-stu-id="6b563-161">Yes</span></span> |
| `required_modifiers` | <span data-ttu-id="6b563-162">Сопоставлять только символы со _всеми_ указанными модификаторами <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="6b563-162">Only match symbols with _all_ the specified modifiers <sup>2</sup></span></span> | <span data-ttu-id="6b563-163">`abstract` или `must_inherit`</span><span class="sxs-lookup"><span data-stu-id="6b563-163">`abstract` or `must_inherit`</span></span><br/>`async`<br/>`const`<br/>`readonly`<br/><span data-ttu-id="6b563-164">`static` или `shared` <sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="6b563-164">`static` or `shared` <sup>3</sup></span></span> | <span data-ttu-id="6b563-165">Нет</span><span class="sxs-lookup"><span data-stu-id="6b563-165">No</span></span> |

<span data-ttu-id="6b563-166">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="6b563-166">**Notes:**</span></span>

1. <span data-ttu-id="6b563-167">В настоящее время элементы кортежа не поддерживаются в `applicable_kinds` .</span><span class="sxs-lookup"><span data-stu-id="6b563-167">Tuple members aren't currently supported in `applicable_kinds`.</span></span>
2. <span data-ttu-id="6b563-168">Группа символов соответствует _всем_ модификаторам в `required_modifiers` свойстве.</span><span class="sxs-lookup"><span data-stu-id="6b563-168">The symbol group matches _all_ the modifiers in the `required_modifiers` property.</span></span>  <span data-ttu-id="6b563-169">Если опустить это свойство, для совпадения не требуются специальные модификаторы.</span><span class="sxs-lookup"><span data-stu-id="6b563-169">If you omit this property, no specific modifiers are required for a match.</span></span> <span data-ttu-id="6b563-170">Это означает, что модификаторы символов не оказывают влияния на применение этого правила.</span><span class="sxs-lookup"><span data-stu-id="6b563-170">This means a symbol's modifiers have no effect on whether or not this rule is applied.</span></span>
3. <span data-ttu-id="6b563-171">Если группа имеет `static` свойство или `shared` в `required_modifiers` свойстве, Группа также будет включать `const` символы, так как они являются неявными `static` / `Shared` .</span><span class="sxs-lookup"><span data-stu-id="6b563-171">If your group has `static` or `shared` in the `required_modifiers` property, the group will also include `const` symbols because they are implicitly `static`/`Shared`.</span></span> <span data-ttu-id="6b563-172">Однако если вы не хотите `static` применять правило именования к `const` символам, можно создать новое правило именования с группой символов `const` .</span><span class="sxs-lookup"><span data-stu-id="6b563-172">However, if you don't want the `static` naming rule to apply to `const` symbols, you can create a new naming rule with a symbol group of `const`.</span></span>

## <a name="naming-style-properties"></a><span data-ttu-id="6b563-173">Именование свойств стиля</span><span class="sxs-lookup"><span data-stu-id="6b563-173">Naming style properties</span></span>

<span data-ttu-id="6b563-174">Стиль именования определяет соглашения, которые необходимо применить к правилу.</span><span class="sxs-lookup"><span data-stu-id="6b563-174">A naming style defines the conventions you want to enforce with the rule.</span></span> <span data-ttu-id="6b563-175">Пример:</span><span class="sxs-lookup"><span data-stu-id="6b563-175">For example:</span></span>

* <span data-ttu-id="6b563-176">С прописной буквы `PascalCase`</span><span class="sxs-lookup"><span data-stu-id="6b563-176">Capitalize with `PascalCase`</span></span>
* <span data-ttu-id="6b563-177">Начинается с `m_`</span><span class="sxs-lookup"><span data-stu-id="6b563-177">Starts with `m_`</span></span>
* <span data-ttu-id="6b563-178">Заканчивается на `_g`</span><span class="sxs-lookup"><span data-stu-id="6b563-178">Ends with `_g`</span></span>
* <span data-ttu-id="6b563-179">Разделять слова с помощью `__`</span><span class="sxs-lookup"><span data-stu-id="6b563-179">Separate words with `__`</span></span>

<span data-ttu-id="6b563-180">Для стиля именования можно задать следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="6b563-180">You can set the following properties for a naming style:</span></span>

| <span data-ttu-id="6b563-181">Свойство</span><span class="sxs-lookup"><span data-stu-id="6b563-181">Property</span></span> | <span data-ttu-id="6b563-182">Описание</span><span class="sxs-lookup"><span data-stu-id="6b563-182">Description</span></span> | <span data-ttu-id="6b563-183">Допустимые значения</span><span class="sxs-lookup"><span data-stu-id="6b563-183">Allowed values</span></span> | <span data-ttu-id="6b563-184">Обязательно</span><span class="sxs-lookup"><span data-stu-id="6b563-184">Required</span></span> |
| -- | -- | -- | -- |
| `capitalization` | <span data-ttu-id="6b563-185">Стиль капитализации для слов внутри символа</span><span class="sxs-lookup"><span data-stu-id="6b563-185">Capitalization style for words within the symbol</span></span> | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | <span data-ttu-id="6b563-186">Да<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6b563-186">Yes<sup>1</sup></span></span> |
| `required_prefix` | <span data-ttu-id="6b563-187">Должно начинаться с этих символов</span><span class="sxs-lookup"><span data-stu-id="6b563-187">Must begin with these characters</span></span> | | <span data-ttu-id="6b563-188">Нет</span><span class="sxs-lookup"><span data-stu-id="6b563-188">No</span></span> |
| `required_suffix` | <span data-ttu-id="6b563-189">Должен заканчиваться этими символами</span><span class="sxs-lookup"><span data-stu-id="6b563-189">Must end with these characters</span></span> | | <span data-ttu-id="6b563-190">Нет</span><span class="sxs-lookup"><span data-stu-id="6b563-190">No</span></span> |
| `word_separator` | <span data-ttu-id="6b563-191">Слова внутри символа должны быть разделены этим символом</span><span class="sxs-lookup"><span data-stu-id="6b563-191">Words within the symbol need to be separated with this character</span></span> | | <span data-ttu-id="6b563-192">Нет</span><span class="sxs-lookup"><span data-stu-id="6b563-192">No</span></span> |

<span data-ttu-id="6b563-193">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="6b563-193">**Notes:**</span></span>

1. <span data-ttu-id="6b563-194">Указать регистр букв для стиля именования обязательно, в противном случае ваш стиль может игнорироваться.</span><span class="sxs-lookup"><span data-stu-id="6b563-194">You must specify a capitalization style as part of your naming style, otherwise your naming style might be ignored.</span></span>

## <a name="default-naming-styles"></a><span data-ttu-id="6b563-195">Стили именования по умолчанию</span><span class="sxs-lookup"><span data-stu-id="6b563-195">Default naming styles</span></span>

<span data-ttu-id="6b563-196">Если не указать никаких пользовательских правил именования, используются следующие стили по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="6b563-196">If you don't specify any custom naming rules, the following default styles are used:</span></span>

- <span data-ttu-id="6b563-197">Для классов, структур, перечислений, свойств и событий со специальными параметрами `public`, `private`, `internal`, `protected` или `protected_internal` по умолчанию используется стиль именования Pascal.</span><span class="sxs-lookup"><span data-stu-id="6b563-197">For classes, structs, enumerations, properties, and events with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case.</span></span>

- <span data-ttu-id="6b563-198">Для интерфейсов со специальными параметрами `public`, `private`, `internal`, `protected` или `protected_internal` по умолчанию используется стиль именования Pascal с обязательным префиксом **I**.</span><span class="sxs-lookup"><span data-stu-id="6b563-198">For interfaces with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case with a required prefix of **I**.</span></span>

## <a name="example"></a><span data-ttu-id="6b563-199">Пример</span><span class="sxs-lookup"><span data-stu-id="6b563-199">Example</span></span>

<span data-ttu-id="6b563-200">Ниже представлен файл *EDITORCONFIG* с соглашением об именовании, в котором указано, что общедоступные свойства, методы, поля, события и делегаты должны начинаться с прописной буквы.</span><span class="sxs-lookup"><span data-stu-id="6b563-200">The following *.editorconfig* file contains a naming convention that specifies that public properties, methods, fields, events, and delegates must be capitalized.</span></span> <span data-ttu-id="6b563-201">Обратите внимание, что это соглашение об именовании указывает несколько типов символов, к которым применяется правило, через запятую.</span><span class="sxs-lookup"><span data-stu-id="6b563-201">Notice that this naming convention specifies multiple kinds of symbol to apply the rule to, using a comma to separate the values.</span></span>

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

## <a name="rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a><span data-ttu-id="6b563-202">Идентификатор правила: "IDE1006" (нарушение правил именования)</span><span class="sxs-lookup"><span data-stu-id="6b563-202">Rule ID: "IDE1006" (Naming rule violation)</span></span>

<span data-ttu-id="6b563-203">Все параметры именования имеют идентификатор `IDE1006` и заголовок правила `Naming rule violation` .</span><span class="sxs-lookup"><span data-stu-id="6b563-203">All naming options have rule ID `IDE1006` and title `Naming rule violation`.</span></span> <span data-ttu-id="6b563-204">Серьезность нарушений именования можно настроить глобально в файле EditorConfig, используя следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="6b563-204">You can configure the severity of naming violations globally in an EditorConfig file with the following syntax:</span></span>

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

<span data-ttu-id="6b563-205">Значение серьезности должно быть `warning` или `error` [принудительно применено при сборке](../overview.md#code-style-analysis).</span><span class="sxs-lookup"><span data-stu-id="6b563-205">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="6b563-206">Все возможные значения серьезности см. в разделе [уровень серьезности](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="6b563-206">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="see-also"></a><span data-ttu-id="6b563-207">См. также</span><span class="sxs-lookup"><span data-stu-id="6b563-207">See also</span></span>

- [<span data-ttu-id="6b563-208">Правила языка</span><span class="sxs-lookup"><span data-stu-id="6b563-208">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="6b563-209">Правила форматирования</span><span class="sxs-lookup"><span data-stu-id="6b563-209">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="6b563-210">Правила именования Roslyn</span><span class="sxs-lookup"><span data-stu-id="6b563-210">Roslyn naming rules</span></span>](https://github.com/dotnet/roslyn/blob/master/.editorconfig#L63)
- [<span data-ttu-id="6b563-211">Справочник по правилам стиля кода .NET</span><span class="sxs-lookup"><span data-stu-id="6b563-211">.NET code style rules reference</span></span>](index.md)
