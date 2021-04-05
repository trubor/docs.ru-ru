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
# <a name="naming-rules"></a><span data-ttu-id="c6c30-103">Правила именования</span><span class="sxs-lookup"><span data-stu-id="c6c30-103">Naming rules</span></span>

<span data-ttu-id="c6c30-104">В файле `.editorconfig` можно определить **правила именования**, которые определяют и принудительно применяют требования к именам для таких элементов кода в языке программирования .NET, как классы, свойства и методы.</span><span class="sxs-lookup"><span data-stu-id="c6c30-104">In your `.editorconfig` file, you can define **naming rules** that specify and enforce how .NET programming language code elements&mdash;such as classes, properties, and methods&mdash;should be named.</span></span> <span data-ttu-id="c6c30-105">Например, вы можете потребовать использовать только прописные буквы для открытых элементов или префикс `_` для закрытых полей.</span><span class="sxs-lookup"><span data-stu-id="c6c30-105">For example, you can specify that public members must be capitalized, or that private fields must begin with `_`.</span></span>

<span data-ttu-id="c6c30-106">Правило именования включает три следующих компонента:</span><span class="sxs-lookup"><span data-stu-id="c6c30-106">A naming rule has three components:</span></span>

* <span data-ttu-id="c6c30-107">**Группа символов**, к которой применяется это правило, например открытые элементы или закрытые поля.</span><span class="sxs-lookup"><span data-stu-id="c6c30-107">The **symbol group** that the rule applies to, for example, public members or private fields.</span></span>
* <span data-ttu-id="c6c30-108">**Стиль именования**, связываемый с этим правилом, например обязательное использование прописных букв или использование символа подчеркивания в качестве первого символа имени.</span><span class="sxs-lookup"><span data-stu-id="c6c30-108">The **naming style** to associate with the rule, for example, that the name must be capitalized or start with an underscore.</span></span>
* <span data-ttu-id="c6c30-109">Уровень серьезности для применения соглашения.</span><span class="sxs-lookup"><span data-stu-id="c6c30-109">The severity for enforcing the convention.</span></span>

<span data-ttu-id="c6c30-110">Во-первых, необходимо указать группу символов и стиль именования, а также присвоить заголовок каждому из них.</span><span class="sxs-lookup"><span data-stu-id="c6c30-110">First, you must specify the symbol group and naming style and give each of them a title.</span></span> <span data-ttu-id="c6c30-111">Затем укажите правило именования, которое связывает их.</span><span class="sxs-lookup"><span data-stu-id="c6c30-111">Then you specify the naming rule, which links everything together.</span></span>

## <a name="general-syntax"></a><span data-ttu-id="c6c30-112">Общий синтаксис</span><span class="sxs-lookup"><span data-stu-id="c6c30-112">General syntax</span></span>

<span data-ttu-id="c6c30-113">Чтобы определить правило именования, группу символов или стиль именования, задайте одно или несколько свойств с помощью следующего синтаксиса:</span><span class="sxs-lookup"><span data-stu-id="c6c30-113">To define a naming rule, symbol group, or naming style, set one or more properties using the following syntax:</span></span>

```ini
<kind>.<title>.<propertyName> = <propertyValue>
```

<span data-ttu-id="c6c30-114">Каждое свойство может быть задано только один раз, но некоторые параметры допускают несколько значений, разделенных запятыми.</span><span class="sxs-lookup"><span data-stu-id="c6c30-114">Each property should only be set once, but some settings allow multiple, comma-separated values.</span></span>

<span data-ttu-id="c6c30-115">Порядок свойств не имеет значения.</span><span class="sxs-lookup"><span data-stu-id="c6c30-115">The order of the properties is not important.</span></span>

### \<kind>

<span data-ttu-id="c6c30-116">**\<kind>** определяет, какие элементы определяются (правило именования, группа символов или стиль именования), и может принимать следующие значения:</span><span class="sxs-lookup"><span data-stu-id="c6c30-116">**\<kind>** specifies which kind of element is being defined&mdash;naming rule, symbol group, or naming style&mdash;and must be one of the following:</span></span>

| <span data-ttu-id="c6c30-117">Для чего задается свойство</span><span class="sxs-lookup"><span data-stu-id="c6c30-117">To set a property for</span></span> | <span data-ttu-id="c6c30-118">Используйте значение \<kind></span><span class="sxs-lookup"><span data-stu-id="c6c30-118">Use the \<kind> value</span></span> | <span data-ttu-id="c6c30-119">Пример</span><span class="sxs-lookup"><span data-stu-id="c6c30-119">Example</span></span> |
| --- | --- | -- |
| <span data-ttu-id="c6c30-120">Правило именования</span><span class="sxs-lookup"><span data-stu-id="c6c30-120">Naming rule</span></span> | `dotnet_naming_rule` | `dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion` |
| <span data-ttu-id="c6c30-121">Группа символов</span><span class="sxs-lookup"><span data-stu-id="c6c30-121">Symbol group</span></span> | `dotnet_naming_symbols` | `dotnet_naming_symbols.interface.applicable_kinds = interface` |
| <span data-ttu-id="c6c30-122">Стиль именования</span><span class="sxs-lookup"><span data-stu-id="c6c30-122">Naming style</span></span> | `dotnet_naming_style` | `dotnet_naming_style.pascal_case.capitalization = pascal_case` |

<span data-ttu-id="c6c30-123">Каждый тип определения (для [правила именования](#naming-rule-properties), [группы символов](#symbol-group-properties) или [стиля именования](#naming-style-properties)) поддерживает свой набор свойств, которые описаны в следующих разделах.</span><span class="sxs-lookup"><span data-stu-id="c6c30-123">Each type of definition&mdash;[naming rule](#naming-rule-properties), [symbol group](#symbol-group-properties), or [naming style](#naming-style-properties)&mdash;has its own supported properties, as described in the following sections.</span></span>

### \<title>

<span data-ttu-id="c6c30-124">**\<title>** содержит выбранное вами описательное имя, которое объединяет несколько параметров свойств в одно определение.</span><span class="sxs-lookup"><span data-stu-id="c6c30-124">**\<title>** is a descriptive name you choose that associates multiple property settings into a single definition.</span></span> <span data-ttu-id="c6c30-125">Например, следующие свойства создают два определения группы символов (`interface` и `types`) и устанавливают для каждого из них два свойства.</span><span class="sxs-lookup"><span data-stu-id="c6c30-125">For example, the following properties produce two symbol group definitions, `interface` and `types`, each of which has two properties set on it.</span></span>

```ini
dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum, delegate
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
```

## <a name="naming-rule-properties"></a><span data-ttu-id="c6c30-126">Свойства правила именования</span><span class="sxs-lookup"><span data-stu-id="c6c30-126">Naming rule properties</span></span>

<span data-ttu-id="c6c30-127">Чтобы правило вступило в силу, должны быть указаны все свойства правила именования.</span><span class="sxs-lookup"><span data-stu-id="c6c30-127">All naming rule properties are required for a rule to take effect.</span></span>

| <span data-ttu-id="c6c30-128">Свойство</span><span class="sxs-lookup"><span data-stu-id="c6c30-128">Property</span></span> | <span data-ttu-id="c6c30-129">Описание</span><span class="sxs-lookup"><span data-stu-id="c6c30-129">Description</span></span> |
| -- | -- |
| `symbols` | <span data-ttu-id="c6c30-130">Заголовок группы символов, к символам которой будет применено правило именования</span><span class="sxs-lookup"><span data-stu-id="c6c30-130">The title of a symbol group; the naming rule will be applied to the symbols in this group</span></span> |
| `style` | <span data-ttu-id="c6c30-131">Заголовок стиля именования, который должен быть связан с этим правилом</span><span class="sxs-lookup"><span data-stu-id="c6c30-131">The title of the naming style which should be associated with this rule</span></span> |
| `severity` |  <span data-ttu-id="c6c30-132">Задает серьезность, с которой будет применяться это правило именования.</span><span class="sxs-lookup"><span data-stu-id="c6c30-132">Sets the severity with which to enforce the naming rule.</span></span> <span data-ttu-id="c6c30-133">Задает для сопоставленного значения один из доступных [уровней серьезности](../configuration-options.md#severity-level)<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c6c30-133">Set the associated value to one of the available [severity levels](../configuration-options.md#severity-level).<sup>1</sup></span></span> |

<span data-ttu-id="c6c30-134">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="c6c30-134">**Notes:**</span></span>

1. <span data-ttu-id="c6c30-135">Спецификация серьезности в правиле именования учитывается только в интегрированных средах разработки, таких как Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c6c30-135">Severity specification within a naming rule is only respected inside development IDEs, such as Visual Studio.</span></span> <span data-ttu-id="c6c30-136">Компиляторы C# или VB не понимают этот параметр и не учитывают его при сборке.</span><span class="sxs-lookup"><span data-stu-id="c6c30-136">This setting is not understood by the C# or VB compilers, hence not respected during build.</span></span> <span data-ttu-id="c6c30-137">Чтобы применить правила стиля именования к сборке, уровень серьезности следует задать с помощью [конфигурации серьезности в правиле кода](#rule-id-ide1006-naming-rule-violation).</span><span class="sxs-lookup"><span data-stu-id="c6c30-137">To enforce naming style rules on build, you should instead set the severity by using [code rule severity configuration](#rule-id-ide1006-naming-rule-violation).</span></span> <span data-ttu-id="c6c30-138">См. дополнительные сведения на [сайте GitHub](https://github.com/dotnet/roslyn/issues/44201).</span><span class="sxs-lookup"><span data-stu-id="c6c30-138">For more information, see this [GitHub issue](https://github.com/dotnet/roslyn/issues/44201).</span></span>

## <a name="symbol-group-properties"></a><span data-ttu-id="c6c30-139">Свойства группы символов</span><span class="sxs-lookup"><span data-stu-id="c6c30-139">Symbol group properties</span></span>

<span data-ttu-id="c6c30-140">Для групп символов можно задать следующие свойства, которые ограничивают набор включаемых в группу символов.</span><span class="sxs-lookup"><span data-stu-id="c6c30-140">You can set the following properties for symbol groups, to limit which symbols are included in the group.</span></span> <span data-ttu-id="c6c30-141">Чтобы указать для одного свойства несколько значений, разделите их запятыми.</span><span class="sxs-lookup"><span data-stu-id="c6c30-141">To specify multiple values for a single property, separate the values with a comma.</span></span>

| <span data-ttu-id="c6c30-142">Свойство</span><span class="sxs-lookup"><span data-stu-id="c6c30-142">Property</span></span> | <span data-ttu-id="c6c30-143">Описание</span><span class="sxs-lookup"><span data-stu-id="c6c30-143">Description</span></span> | <span data-ttu-id="c6c30-144">Допустимые значения</span><span class="sxs-lookup"><span data-stu-id="c6c30-144">Allowed values</span></span> | <span data-ttu-id="c6c30-145">Обязательно</span><span class="sxs-lookup"><span data-stu-id="c6c30-145">Required</span></span> |
| -- | -- | -- | -- |
| `applicable_kinds` | <span data-ttu-id="c6c30-146">Типы символов в группе <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c6c30-146">Kinds of symbols in the group <sup>1</sup></span></span> | <span data-ttu-id="c6c30-147">`*` (используйте это значение, чтобы указать все символы)</span><span class="sxs-lookup"><span data-stu-id="c6c30-147">`*` (use this value to specify all symbols)</span></span><br/>`namespace`<br/>`class`<br/>`struct`<br/>`interface`<br/>`enum`<br/>`property`<br/>`method`<br/>`field`<br/>`event`<br/>`delegate`<br/>`parameter`<br/>`type_parameter`<br/>`local`<br/>`local_function` | <span data-ttu-id="c6c30-148">Да</span><span class="sxs-lookup"><span data-stu-id="c6c30-148">Yes</span></span> |
| `applicable_accessibilities` | <span data-ttu-id="c6c30-149">Уровни доступности для символов в группе</span><span class="sxs-lookup"><span data-stu-id="c6c30-149">Accessibility levels of the symbols in the group</span></span> | <span data-ttu-id="c6c30-150">`*` (используйте это значение, чтобы указать все уровни доступа)</span><span class="sxs-lookup"><span data-stu-id="c6c30-150">`*` (use this value to specify all accessibility levels)</span></span><br/>`public`<br/><span data-ttu-id="c6c30-151">`internal` либо `friend`</span><span class="sxs-lookup"><span data-stu-id="c6c30-151">`internal` or `friend`</span></span><br/>`private`<br/>`protected`<br/><span data-ttu-id="c6c30-152">`protected_internal` или `protected_friend`</span><span class="sxs-lookup"><span data-stu-id="c6c30-152">`protected_internal` or `protected_friend`</span></span><br/>`private_protected`<br/><span data-ttu-id="c6c30-153">`local` (для символов, определенных в методе)</span><span class="sxs-lookup"><span data-stu-id="c6c30-153">`local` (for symbols defined within a method)</span></span> | <span data-ttu-id="c6c30-154">Да</span><span class="sxs-lookup"><span data-stu-id="c6c30-154">Yes</span></span> |
| `required_modifiers` | <span data-ttu-id="c6c30-155">Соответствует только тем символам, у которых есть _все_ указанные модификаторы <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="c6c30-155">Only match symbols with _all_ the specified modifiers <sup>2</sup></span></span> | <span data-ttu-id="c6c30-156">`abstract` либо `must_inherit`</span><span class="sxs-lookup"><span data-stu-id="c6c30-156">`abstract` or `must_inherit`</span></span><br/>`async`<br/>`const`<br/>`readonly`<br/><span data-ttu-id="c6c30-157">`static` или `shared` <sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="c6c30-157">`static` or `shared` <sup>3</sup></span></span> | <span data-ttu-id="c6c30-158">Нет</span><span class="sxs-lookup"><span data-stu-id="c6c30-158">No</span></span> |

<span data-ttu-id="c6c30-159">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="c6c30-159">**Notes:**</span></span>

1. <span data-ttu-id="c6c30-160">Элементы кортежа в настоящее время поддерживаются только в `applicable_kinds`.</span><span class="sxs-lookup"><span data-stu-id="c6c30-160">Tuple members aren't currently supported in `applicable_kinds`.</span></span>
2. <span data-ttu-id="c6c30-161">Группа символов сопоставляет _все_ модификаторы в свойстве `required_modifiers`.</span><span class="sxs-lookup"><span data-stu-id="c6c30-161">The symbol group matches _all_ the modifiers in the `required_modifiers` property.</span></span>  <span data-ttu-id="c6c30-162">Если вы опустите это свойство, для сопоставления не требуются конкретные модификаторы.</span><span class="sxs-lookup"><span data-stu-id="c6c30-162">If you omit this property, no specific modifiers are required for a match.</span></span> <span data-ttu-id="c6c30-163">Это означает, что модификаторы символов не оказывают влияния на применение этого правила.</span><span class="sxs-lookup"><span data-stu-id="c6c30-163">This means a symbol's modifiers have no effect on whether or not this rule is applied.</span></span>
3. <span data-ttu-id="c6c30-164">Если группа имеет значение `static` или `shared` в свойстве `required_modifiers`, в нее будут включены также символы `const`, так как они неявно являются `static`/`Shared`.</span><span class="sxs-lookup"><span data-stu-id="c6c30-164">If your group has `static` or `shared` in the `required_modifiers` property, the group will also include `const` symbols because they are implicitly `static`/`Shared`.</span></span> <span data-ttu-id="c6c30-165">Но если вы не хотите применять правило именования `static` к символам `const`, вы можете создать новое правило именования для группы символов `const`.</span><span class="sxs-lookup"><span data-stu-id="c6c30-165">However, if you don't want the `static` naming rule to apply to `const` symbols, you can create a new naming rule with a symbol group of `const`.</span></span>

## <a name="naming-style-properties"></a><span data-ttu-id="c6c30-166">Свойства стиля именования</span><span class="sxs-lookup"><span data-stu-id="c6c30-166">Naming style properties</span></span>

<span data-ttu-id="c6c30-167">Стиль именования определяет соглашения, которые будут применяться к правилу.</span><span class="sxs-lookup"><span data-stu-id="c6c30-167">A naming style defines the conventions you want to enforce with the rule.</span></span> <span data-ttu-id="c6c30-168">Например:</span><span class="sxs-lookup"><span data-stu-id="c6c30-168">For example:</span></span>

* <span data-ttu-id="c6c30-169">Использование прописных букв `PascalCase`</span><span class="sxs-lookup"><span data-stu-id="c6c30-169">Capitalize with `PascalCase`</span></span>
* <span data-ttu-id="c6c30-170">Начинается с `m_`</span><span class="sxs-lookup"><span data-stu-id="c6c30-170">Starts with `m_`</span></span>
* <span data-ttu-id="c6c30-171">Заканчивается на `_g`</span><span class="sxs-lookup"><span data-stu-id="c6c30-171">Ends with `_g`</span></span>
* <span data-ttu-id="c6c30-172">Разделение слов с помощью `__`</span><span class="sxs-lookup"><span data-stu-id="c6c30-172">Separate words with `__`</span></span>

<span data-ttu-id="c6c30-173">Для стиля именования можно задать следующие свойства:</span><span class="sxs-lookup"><span data-stu-id="c6c30-173">You can set the following properties for a naming style:</span></span>

| <span data-ttu-id="c6c30-174">Свойство</span><span class="sxs-lookup"><span data-stu-id="c6c30-174">Property</span></span> | <span data-ttu-id="c6c30-175">Описание</span><span class="sxs-lookup"><span data-stu-id="c6c30-175">Description</span></span> | <span data-ttu-id="c6c30-176">Допустимые значения</span><span class="sxs-lookup"><span data-stu-id="c6c30-176">Allowed values</span></span> | <span data-ttu-id="c6c30-177">Обязательно</span><span class="sxs-lookup"><span data-stu-id="c6c30-177">Required</span></span> |
| -- | -- | -- | -- |
| `capitalization` | <span data-ttu-id="c6c30-178">Стиль применения прописных букв для слов в пределах символа</span><span class="sxs-lookup"><span data-stu-id="c6c30-178">Capitalization style for words within the symbol</span></span> | `pascal_case`<br/>`camel_case`<br/>`first_word_upper`<br/>`all_upper`<br/>`all_lower` | <span data-ttu-id="c6c30-179">Да<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="c6c30-179">Yes<sup>1</sup></span></span> |
| `required_prefix` | <span data-ttu-id="c6c30-180">Должно начинаться с этих символов</span><span class="sxs-lookup"><span data-stu-id="c6c30-180">Must begin with these characters</span></span> | | <span data-ttu-id="c6c30-181">Нет</span><span class="sxs-lookup"><span data-stu-id="c6c30-181">No</span></span> |
| `required_suffix` | <span data-ttu-id="c6c30-182">Должно заканчиваться этими символами</span><span class="sxs-lookup"><span data-stu-id="c6c30-182">Must end with these characters</span></span> | | <span data-ttu-id="c6c30-183">Нет</span><span class="sxs-lookup"><span data-stu-id="c6c30-183">No</span></span> |
| `word_separator` | <span data-ttu-id="c6c30-184">Слова внутри символа должны разделяться этим символом</span><span class="sxs-lookup"><span data-stu-id="c6c30-184">Words within the symbol need to be separated with this character</span></span> | | <span data-ttu-id="c6c30-185">Нет</span><span class="sxs-lookup"><span data-stu-id="c6c30-185">No</span></span> |

<span data-ttu-id="c6c30-186">**Примечания.**</span><span class="sxs-lookup"><span data-stu-id="c6c30-186">**Notes:**</span></span>

1. <span data-ttu-id="c6c30-187">Указать регистр букв для стиля именования обязательно, в противном случае ваш стиль может игнорироваться.</span><span class="sxs-lookup"><span data-stu-id="c6c30-187">You must specify a capitalization style as part of your naming style, otherwise your naming style might be ignored.</span></span>

## <a name="rule-order"></a><span data-ttu-id="c6c30-188">Порядок правил</span><span class="sxs-lookup"><span data-stu-id="c6c30-188">Rule order</span></span>

<span data-ttu-id="c6c30-189">Порядок определения правил в файле EditorConfig не имеет значения.</span><span class="sxs-lookup"><span data-stu-id="c6c30-189">The order in which naming rules are defined in an EditorConfig file doesn't matter.</span></span> <span data-ttu-id="c6c30-190">Все правила именования автоматически упорядочиваются в соответствии с определениями самих правил.</span><span class="sxs-lookup"><span data-stu-id="c6c30-190">The naming rules are automatically ordered according to the definition of the rules themselves.</span></span> <span data-ttu-id="c6c30-191">[Расширение языковой службы EditorConfig](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) может анализировать файл EditorConfig и сообщать о случаях, когда порядок правил в файле отличается от того, который будет использоваться компилятором во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="c6c30-191">The [EditorConfig Language Service extension](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) can analyze an EditorConfig file and report cases where the rule ordering in the file is different to what the compiler will use at run time.</span></span>

> [!NOTE]
>
> <span data-ttu-id="c6c30-192">Если вы используете более раннюю версию Visual Studio, чем Visual Studio 2019 версии 16.2, правила именования в файле EditorConfig должны быть упорядочены от более конкретных к более общим.</span><span class="sxs-lookup"><span data-stu-id="c6c30-192">If you're using a version of Visual Studio earlier than Visual Studio 2019 version 16.2, naming rules should be ordered from most-specific to least-specific in the EditorConfig file.</span></span> <span data-ttu-id="c6c30-193">Применяться будет только первое обнаруженное правило.</span><span class="sxs-lookup"><span data-stu-id="c6c30-193">The first rule encountered that can be applied is the only rule that is applied.</span></span> <span data-ttu-id="c6c30-194">Но при наличии множества *свойств* правил с одним и тем же именем приоритет будет иметь последнее обнаруженное свойство с таким именем.</span><span class="sxs-lookup"><span data-stu-id="c6c30-194">However, if there are multiple rule *properties* with the same name, the most recently found property with that name takes precedence.</span></span> <span data-ttu-id="c6c30-195">См. подробнее об [иерархии файлов и приоритетности](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span><span class="sxs-lookup"><span data-stu-id="c6c30-195">For more information, see [File hierarchy and precedence](/visualstudio/ide/create-portable-custom-editor-options#file-hierarchy-and-precedence).</span></span>

## <a name="default-naming-styles"></a><span data-ttu-id="c6c30-196">Стили именования по умолчанию</span><span class="sxs-lookup"><span data-stu-id="c6c30-196">Default naming styles</span></span>

<span data-ttu-id="c6c30-197">Если вы не укажете никаких пользовательских правил именования, применяются следующие стили по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="c6c30-197">If you don't specify any custom naming rules, the following default styles are used:</span></span>

- <span data-ttu-id="c6c30-198">Для классов, структур, перечислений, свойств и событий со специальными параметрами `public`, `private`, `internal`, `protected` или `protected_internal` по умолчанию используется стиль именования Pascal.</span><span class="sxs-lookup"><span data-stu-id="c6c30-198">For classes, structs, enumerations, properties, and events with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case.</span></span>

- <span data-ttu-id="c6c30-199">Для интерфейсов со специальными параметрами `public`, `private`, `internal`, `protected` или `protected_internal` по умолчанию используется стиль именования Pascal с обязательным префиксом **I**.</span><span class="sxs-lookup"><span data-stu-id="c6c30-199">For interfaces with `public`, `private`, `internal`, `protected`, or `protected_internal` accessibility, the default naming style is Pascal case with a required prefix of **I**.</span></span>

## <a name="code-rule-id-ide1006-naming-rule-violation"></a><a name="rule-id-ide1006-naming-rule-violation"></a><span data-ttu-id="c6c30-200">Идентификатор правила кода: `IDE1006 (Naming rule violation)`</span><span class="sxs-lookup"><span data-stu-id="c6c30-200">Code Rule ID: `IDE1006 (Naming rule violation)`</span></span>

<span data-ttu-id="c6c30-201">Все параметры именования имеют идентификатор правила `IDE1006` и заголовок `Naming rule violation`.</span><span class="sxs-lookup"><span data-stu-id="c6c30-201">All naming options have rule ID `IDE1006` and title `Naming rule violation`.</span></span> <span data-ttu-id="c6c30-202">Серьезность для нарушений именования можно настроить глобально в файле EditorConfig, используя следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="c6c30-202">You can configure the severity of naming violations globally in an EditorConfig file with the following syntax:</span></span>

```ini
dotnet_diagnostic.IDE1006.severity = <severity value>
```

<span data-ttu-id="c6c30-203">Серьезность должна иметь значение `warning` или `error`, чтобы [принудительно применяться при сборке](../overview.md#code-style-analysis).</span><span class="sxs-lookup"><span data-stu-id="c6c30-203">The severity value must be `warning` or `error` to be [enforced on build](../overview.md#code-style-analysis).</span></span> <span data-ttu-id="c6c30-204">Все возможные значения серьезности перечислены на странице [об уровнях серьезности](../configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="c6c30-204">For all possible severity values, see [severity level](../configuration-options.md#severity-level).</span></span>

## <a name="example"></a><span data-ttu-id="c6c30-205">Пример</span><span class="sxs-lookup"><span data-stu-id="c6c30-205">Example</span></span>

<span data-ttu-id="c6c30-206">Ниже представлен файл *EDITORCONFIG* с соглашением об именовании, в котором указано, что общедоступные свойства, методы, поля, события и делегаты должны начинаться с прописной буквы.</span><span class="sxs-lookup"><span data-stu-id="c6c30-206">The following *.editorconfig* file contains a naming convention that specifies that public properties, methods, fields, events, and delegates must be capitalized.</span></span> <span data-ttu-id="c6c30-207">Обратите внимание, что это соглашение об именовании указывает несколько типов символов, к которым применяется правило, через запятую.</span><span class="sxs-lookup"><span data-stu-id="c6c30-207">Notice that this naming convention specifies multiple kinds of symbol to apply the rule to, using a comma to separate the values.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c6c30-208">См. также</span><span class="sxs-lookup"><span data-stu-id="c6c30-208">See also</span></span>

- [<span data-ttu-id="c6c30-209">Правила языка</span><span class="sxs-lookup"><span data-stu-id="c6c30-209">Language rules</span></span>](language-rules.md)
- [<span data-ttu-id="c6c30-210">Правила форматирования</span><span class="sxs-lookup"><span data-stu-id="c6c30-210">Formatting rules</span></span>](formatting-rules.md)
- [<span data-ttu-id="c6c30-211">Правила именования Roslyn</span><span class="sxs-lookup"><span data-stu-id="c6c30-211">Roslyn naming rules</span></span>](https://github.com/dotnet/roslyn/blob/main/.editorconfig#L63)
- [<span data-ttu-id="c6c30-212">Справочник по правилам стиля кода для .NET</span><span class="sxs-lookup"><span data-stu-id="c6c30-212">.NET code style rules reference</span></span>](index.md)
