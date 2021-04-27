---
title: Шаблоны — справочник по C#
description: Сведения о шаблонах, поддерживаемых выражениями и операторами сопоставления шаблонов C# — справочник по C#
ms.date: 04/05/2021
f1_keywords:
- and_CSharpKeyword
- or_CSharpKeyword
- not_CSharpKeyword
helpviewer_keywords:
- pattern matching [C#]
- and keyword [C#]
- or keyword [C#]
- not keyword [C#]
ms.openlocfilehash: cb3517516b09e21483985b04977313617a3a26fe
ms.sourcegitcommit: 02cc87f02c46e603ea5925de95af746b7ab46a35
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/25/2021
ms.locfileid: "107954722"
---
# <a name="patterns-c-reference"></a><span data-ttu-id="31685-103">Шаблоны (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="31685-103">Patterns (C# reference)</span></span>

<span data-ttu-id="31685-104">Возможность использовать сопоставление шаблонов впервые появилась в C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="31685-104">C# introduced pattern matching in C# 7.0.</span></span> <span data-ttu-id="31685-105">С тех пор в каждой новой основной версии C# возможности сопоставления шаблонов расширяются.</span><span class="sxs-lookup"><span data-stu-id="31685-105">Since then, each major C# version extends pattern matching capabilities.</span></span> <span data-ttu-id="31685-106">Сопоставление шаблонов поддерживают следующие выражения и операторы C#:</span><span class="sxs-lookup"><span data-stu-id="31685-106">The following C# expressions and statements support pattern matching:</span></span>

- [<span data-ttu-id="31685-107">Выражение `is`</span><span class="sxs-lookup"><span data-stu-id="31685-107">`is` expression</span></span>](is.md)
- <span data-ttu-id="31685-108">[Оператор](../keywords/switch.md) `switch`</span><span class="sxs-lookup"><span data-stu-id="31685-108">`switch` [statement](../keywords/switch.md)</span></span>
- <span data-ttu-id="31685-109">[Выражение](switch-expression.md) `switch` (появилось в C# 8.0)</span><span class="sxs-lookup"><span data-stu-id="31685-109">`switch` [expression](switch-expression.md) (introduced in C# 8.0)</span></span>

<span data-ttu-id="31685-110">В этих конструкциях можно сравнить входное выражение с любым из следующих шаблонов:</span><span class="sxs-lookup"><span data-stu-id="31685-110">In those constructs, you can match an input expression against any of the following patterns:</span></span>

- <span data-ttu-id="31685-111">[Шаблон объявления](#declaration-and-type-patterns): для проверки типа выражения в среде выполнения и, в случае равенства, присвоения объявленной переменной результата этого выражения.</span><span class="sxs-lookup"><span data-stu-id="31685-111">[Declaration pattern](#declaration-and-type-patterns): to check the runtime type of an expression and, if a match succeeds, assign an expression result to a declared variable.</span></span> <span data-ttu-id="31685-112">Впервые появился в C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="31685-112">Introduced in C# 7.0.</span></span>
- <span data-ttu-id="31685-113">[Шаблон типа](#declaration-and-type-patterns): для проверки типа выражения в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="31685-113">[Type pattern](#declaration-and-type-patterns): to check the runtime type of an expression.</span></span> <span data-ttu-id="31685-114">Впервые появился в C# 9.0.</span><span class="sxs-lookup"><span data-stu-id="31685-114">Introduced in C# 9.0.</span></span>
- <span data-ttu-id="31685-115">[Шаблон константы](#constant-pattern): для проверки того, равен ли результат выражения указанной константе.</span><span class="sxs-lookup"><span data-stu-id="31685-115">[Constant pattern](#constant-pattern): to test if an expression result equals a specified constant.</span></span> <span data-ttu-id="31685-116">Впервые появился в C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="31685-116">Introduced in C# 7.0.</span></span>
- <span data-ttu-id="31685-117">[Реляционные шаблоны](#relational-patterns): для сравнения результата выражения с заданной константой.</span><span class="sxs-lookup"><span data-stu-id="31685-117">[Relational patterns](#relational-patterns): to compare an expression result with a specified constant.</span></span> <span data-ttu-id="31685-118">Впервые появился в C# 9.0.</span><span class="sxs-lookup"><span data-stu-id="31685-118">Introduced in C# 9.0.</span></span>
- <span data-ttu-id="31685-119">[Логические шаблоны](#logical-patterns): для проверки того, соответствует ли выражение логической комбинации шаблонов.</span><span class="sxs-lookup"><span data-stu-id="31685-119">[Logical patterns](#logical-patterns): to test if an expression matches a logical combination of patterns.</span></span> <span data-ttu-id="31685-120">Впервые появился в C# 9.0.</span><span class="sxs-lookup"><span data-stu-id="31685-120">Introduced in C# 9.0.</span></span>
- <span data-ttu-id="31685-121">[Шаблон свойства](#property-pattern): для проверки того, соответствуют ли свойства или поля выражения вложенным шаблонам.</span><span class="sxs-lookup"><span data-stu-id="31685-121">[Property pattern](#property-pattern): to test if an expression's properties or fields match nested patterns.</span></span> <span data-ttu-id="31685-122">Впервые появился в C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="31685-122">Introduced in C# 8.0.</span></span>
- <span data-ttu-id="31685-123">[Позиционный шаблон](#positional-pattern): для деконструкции результата выражения и проверки того, соответствуют ли результирующие значения вложенным шаблонам.</span><span class="sxs-lookup"><span data-stu-id="31685-123">[Positional pattern](#positional-pattern): to deconstruct an expression result and test if the resulting values match nested patterns.</span></span> <span data-ttu-id="31685-124">Впервые появился в C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="31685-124">Introduced in C# 8.0.</span></span>
- <span data-ttu-id="31685-125">[Шаблон](#var-pattern) `var`: для сравнения любых выражений и присваивания результата сравнения объявленной переменной.</span><span class="sxs-lookup"><span data-stu-id="31685-125">[`var` pattern](#var-pattern): to match any expression and assign its result to a declared variable.</span></span> <span data-ttu-id="31685-126">Впервые появился в C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="31685-126">Introduced in C# 7.0.</span></span>
- <span data-ttu-id="31685-127">[Шаблон пустой переменной](#discard-pattern): для сравнения любых выражений.</span><span class="sxs-lookup"><span data-stu-id="31685-127">[Discard pattern](#discard-pattern): to match any expression.</span></span> <span data-ttu-id="31685-128">Впервые появился в C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="31685-128">Introduced in C# 8.0.</span></span>

<span data-ttu-id="31685-129">[Логические шаблоны](#logical-patterns), [шаблоны свойств](#property-pattern) и [позиционные шаблоны](#positional-pattern) являются *рекурсивными* шаблонами.</span><span class="sxs-lookup"><span data-stu-id="31685-129">[Logical](#logical-patterns), [property](#property-pattern), and [positional](#positional-pattern) patterns are *recursive* patterns.</span></span> <span data-ttu-id="31685-130">То есть, они могут содержать *вложенные* шаблоны.</span><span class="sxs-lookup"><span data-stu-id="31685-130">That is, they can contain *nested* patterns.</span></span>

<span data-ttu-id="31685-131">Пример использования этих шаблонов для создания управляемого данными алгоритма можно посмотреть в разделе [Учебник: использование сопоставления шаблонов для создания управляемых типами и управляемых данными алгоритмов](../../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="31685-131">For the example of how to use those patterns to build a data-driven algorithm, see [Tutorial: Use pattern matching to build type-driven and data-driven algorithms](../../tutorials/pattern-matching.md).</span></span>

## <a name="declaration-and-type-patterns"></a><span data-ttu-id="31685-132">Шаблоны объявления и шаблоны типов</span><span class="sxs-lookup"><span data-stu-id="31685-132">Declaration and type patterns</span></span>

<span data-ttu-id="31685-133">Шаблоны объявления и шаблоны типов используются для проверки того, совместим ли с указанным типом тип определенного выражения в среде выполнения.</span><span class="sxs-lookup"><span data-stu-id="31685-133">You use declaration and type patterns to check if the runtime type of an expression is compatible with a given type.</span></span> <span data-ttu-id="31685-134">С помощью шаблона объявления можно также объявить новую локальную переменную.</span><span class="sxs-lookup"><span data-stu-id="31685-134">With a declaration pattern, you can also declare a new local variable.</span></span> <span data-ttu-id="31685-135">Если шаблон объявления соответствует выражению, этой переменной присваивается результат преобразованного выражения, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-135">When a declaration pattern matches an expression, that variable is assigned a converted expression result, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="BasicExample":::

<span data-ttu-id="31685-136">Начиная с C# 7.0, *шаблон объявления* с типом `T` соответствует выражению в том случае, если результат выражения имеет значение, отличное от NULL, и выполняется любое из следующих условий:</span><span class="sxs-lookup"><span data-stu-id="31685-136">Beginning with C# 7.0, a *declaration pattern* with type `T` matches an expression when an expression result is non-null and any of the following conditions are true:</span></span>

- <span data-ttu-id="31685-137">Тип результата выражения в среде выполнения — `T`.</span><span class="sxs-lookup"><span data-stu-id="31685-137">The runtime type of an expression result is `T`.</span></span>

- <span data-ttu-id="31685-138">Тип результата выражения в среде выполнения является производным от типа `T` или реализует интерфейс `T` или существует другое [неявное преобразования ссылок](~/_csharplang/spec/conversions.md#implicit-reference-conversions) из него в `T`.</span><span class="sxs-lookup"><span data-stu-id="31685-138">The runtime type of an expression result derives from type `T` or implements interface `T` or another [implicit reference conversion](~/_csharplang/spec/conversions.md#implicit-reference-conversions) exists from it to `T`.</span></span> <span data-ttu-id="31685-139">В следующем примере показаны два случая, когда данное условие истинно:</span><span class="sxs-lookup"><span data-stu-id="31685-139">The following example demonstrates two cases when this condition is true:</span></span>

  :::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="ReferenceConversion":::

  <span data-ttu-id="31685-140">В предыдущем примере при первом вызове метода `GetSourceLabel` первый шаблон соответствует значению аргумента, так как тип этого аргумента (`int[]`) в среде выполнения является производным от типа <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="31685-140">In the preceding example, at the first call to the `GetSourceLabel` method, the first pattern matches an argument value because the argument's runtime type `int[]` derives from the <xref:System.Array> type.</span></span> <span data-ttu-id="31685-141">При втором вызове метода `GetSourceLabel` тип аргумента в среде выполнения (<xref:System.Collections.Generic.List%601>) не является производным от типа <xref:System.Array>, но реализует интерфейс <xref:System.Collections.Generic.ICollection%601>.</span><span class="sxs-lookup"><span data-stu-id="31685-141">At the second call to the `GetSourceLabel` method, the argument's runtime type <xref:System.Collections.Generic.List%601> doesn't derive from the <xref:System.Array> type but implements the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

- <span data-ttu-id="31685-142">Тип результата выражения в среде выполнения является [типом, допускающим значение NULL](../builtin-types/nullable-value-types.md), и имеющим базовый тип `T`.</span><span class="sxs-lookup"><span data-stu-id="31685-142">The runtime type of an expression result is a [nullable value type](../builtin-types/nullable-value-types.md) with the underlying type `T`.</span></span>

- <span data-ttu-id="31685-143">Существует [упаковка-преобразование](../../programming-guide/types/boxing-and-unboxing.md#boxing) или [распаковка-преобразование](../../programming-guide/types/boxing-and-unboxing.md#unboxing) из типа результата выражения в среде выполнения в тип `T`.</span><span class="sxs-lookup"><span data-stu-id="31685-143">A [boxing](../../programming-guide/types/boxing-and-unboxing.md#boxing) or [unboxing](../../programming-guide/types/boxing-and-unboxing.md#unboxing) conversion exists from the runtime type of an expression result to type `T`.</span></span>

<span data-ttu-id="31685-144">В следующем примере показаны два последних условия:</span><span class="sxs-lookup"><span data-stu-id="31685-144">The following example demonstrates the last two conditions:</span></span>

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="NullableAndUnboxing":::

<span data-ttu-id="31685-145">Если требуется проверить только тип выражения, можно вместо имени переменной использовать пустую переменную `_`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-145">If you want to check only the type of an expression, you can use a discard `_` in place of a variable's name, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="DiscardVariable":::

<span data-ttu-id="31685-146">Начиная с C# 9.0, для этой цели можно использовать *шаблон типа*, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-146">Beginning with C# 9.0, for that purpose you can use a *type pattern*, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/DeclarationAndTypePatterns.cs" id="TypePattern":::

<span data-ttu-id="31685-147">Как и шаблон объявления, шаблон типа соответствует выражению, если результат выражения не равен NULL, а его тип в среде выполнения удовлетворяет любому из указанных выше условий.</span><span class="sxs-lookup"><span data-stu-id="31685-147">Like a declaration pattern, a type pattern matches an expression when an expression result is non-null and its runtime type satisfies any of the conditions listed above.</span></span>

<span data-ttu-id="31685-148">Дополнительные сведения см. в разделах [Шаблон объявления](~/_csharplang/proposals/csharp-8.0/patterns.md#declaration-pattern) и [Шаблон типа](~/_csharplang/proposals/csharp-9.0/patterns3.md#type-patterns) в примечаниях к предлагаемой функции.</span><span class="sxs-lookup"><span data-stu-id="31685-148">For more information, see the [Declaration pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#declaration-pattern) and [Type pattern](~/_csharplang/proposals/csharp-9.0/patterns3.md#type-patterns) sections of the feature proposal notes.</span></span>

## <a name="constant-pattern"></a><span data-ttu-id="31685-149">Шаблон константы</span><span class="sxs-lookup"><span data-stu-id="31685-149">Constant pattern</span></span>

<span data-ttu-id="31685-150">Начиная с C# 7.0, вы можете использовать *шаблон константы* для проверки того, равен ли результат выражения заданной константе, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-150">Beginning with C# 7.0, you use a *constant pattern* to test if an expression result equals a specified constant, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="BasicExample":::

<span data-ttu-id="31685-151">В шаблоне константы можно использовать любое константное выражение, например:</span><span class="sxs-lookup"><span data-stu-id="31685-151">In a constant pattern, you can use any constant expression, such as:</span></span>

- <span data-ttu-id="31685-152">[целочисленный](../builtin-types/integral-numeric-types.md) литерал или литерал [с плавающей точкой](../builtin-types/floating-point-numeric-types.md);</span><span class="sxs-lookup"><span data-stu-id="31685-152">an [integer](../builtin-types/integral-numeric-types.md) or [floating-point](../builtin-types/floating-point-numeric-types.md) numerical literal</span></span>
- <span data-ttu-id="31685-153">[символьный](../builtin-types/char.md) или [строковый](../builtin-types/reference-types.md#the-string-type) литерал;</span><span class="sxs-lookup"><span data-stu-id="31685-153">a [char](../builtin-types/char.md) or a [string](../builtin-types/reference-types.md#the-string-type) literal</span></span>
- <span data-ttu-id="31685-154">логическое значение `true` или `false`;</span><span class="sxs-lookup"><span data-stu-id="31685-154">a Boolean value `true` or `false`</span></span>
- <span data-ttu-id="31685-155">значение типа [enum](../builtin-types/enum.md);</span><span class="sxs-lookup"><span data-stu-id="31685-155">an [enum](../builtin-types/enum.md) value</span></span>
- <span data-ttu-id="31685-156">имя объявленного поля с модификатором [const](../keywords/const.md) или локального элемента.</span><span class="sxs-lookup"><span data-stu-id="31685-156">the name of a declared [const](../keywords/const.md) field or local</span></span>
- `null`

<span data-ttu-id="31685-157">Используйте шаблон константы для проверки на `null`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-157">Use a constant pattern to check for `null`, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="NullCheck":::

<span data-ttu-id="31685-158">Компилятор гарантирует, что при вычислении выражения `x is null` не будет вызван перегруженный пользователем оператор равенства `==`.</span><span class="sxs-lookup"><span data-stu-id="31685-158">The compiler guarantees that no user-overloaded equality operator `==` is invoked when expression `x is null` is evaluated.</span></span>

<span data-ttu-id="31685-159">Начиная с C# 9.0, вы можете использовать шаблон константы `null` с [отрицанием](#logical-patterns) для проверки неравенства значению NULL, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-159">Beginning with C# 9.0, you can use a [negated](#logical-patterns) `null` constant pattern to check for non-null, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/ConstantPattern.cs" id="NonNullCheck":::

<span data-ttu-id="31685-160">Дополнительные сведения см. в разделе [Шаблон константы](~/_csharplang/proposals/csharp-8.0/patterns.md#constant-pattern) в примечании к предлагаемой функции.</span><span class="sxs-lookup"><span data-stu-id="31685-160">For more information, see the [Constant pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#constant-pattern) section of the feature proposal note.</span></span>

## <a name="relational-patterns"></a><span data-ttu-id="31685-161">Реляционные шаблоны</span><span class="sxs-lookup"><span data-stu-id="31685-161">Relational patterns</span></span>

<span data-ttu-id="31685-162">Начиная с C# 9.0, вы можете использовать *реляционный шаблон* для сравнения результата выражения с константой, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-162">Beginning with C# 9.0, you use a *relational pattern* to compare an expression result with a constant, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/RelationalPatterns.cs" id="BasicExample":::

<span data-ttu-id="31685-163">В реляционном шаблоне можно использовать любые [операторы отношений](comparison-operators.md) — `<`, `>`, `<=`, `>=`.</span><span class="sxs-lookup"><span data-stu-id="31685-163">In a relational pattern, you can use any of the [relational operators](comparison-operators.md) `<`, `>`, `<=`, or `>=`.</span></span> <span data-ttu-id="31685-164">Правая часть реляционного шаблона должна быть константным выражением.</span><span class="sxs-lookup"><span data-stu-id="31685-164">The right-hand part of a relational pattern must be a constant expression.</span></span> <span data-ttu-id="31685-165">Константное выражение может быть [целым числом](../builtin-types/integral-numeric-types.md), [числом с плавающей точкой](../builtin-types/floating-point-numeric-types.md), [символом](../builtin-types/char.md) или иметь тип [enum](../builtin-types/enum.md).</span><span class="sxs-lookup"><span data-stu-id="31685-165">The constant expression can be of an [integer](../builtin-types/integral-numeric-types.md), [floating-point](../builtin-types/floating-point-numeric-types.md), [char](../builtin-types/char.md), or [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="31685-166">Чтобы проверить, находится ли результат выражения в определенном диапазоне, сопоставьте его с [шаблоном конъюнкции](#logical-patterns) (`and`), как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-166">To check if an expression result is in a certain range, match it against a [conjunctive `and` pattern](#logical-patterns), as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/RelationalPatterns.cs" id="WithCombinators":::

<span data-ttu-id="31685-167">Если результат выражения — `null` или его не удается преобразовать в тип константы с помощью преобразования, допускающего значение NULL, или распаковки-преобразования, то реляционный шаблон не соответствует выражению.</span><span class="sxs-lookup"><span data-stu-id="31685-167">If an expression result is `null` or fails to convert to the type of a constant by a nullable or unboxing conversion, a relational pattern doesn't match an expression.</span></span>

<span data-ttu-id="31685-168">Дополнительные сведения см. в разделе [Реляционные шаблоны](~/_csharplang/proposals/csharp-9.0/patterns3.md#relational-patterns) в примечании к предлагаемой функции.</span><span class="sxs-lookup"><span data-stu-id="31685-168">For more information, see the [Relational patterns](~/_csharplang/proposals/csharp-9.0/patterns3.md#relational-patterns) section of the feature proposal note.</span></span>

## <a name="logical-patterns"></a><span data-ttu-id="31685-169">Логические шаблоны</span><span class="sxs-lookup"><span data-stu-id="31685-169">Logical patterns</span></span>

<span data-ttu-id="31685-170">Начиная с C# 9.0, вы можете использовать блоки объединения `not`, `and` и `or` для создания следующих *логических шаблонов*:</span><span class="sxs-lookup"><span data-stu-id="31685-170">Beginning with C# 9.0, you use the `not`, `and`, and `or` pattern combinators to create the following *logical patterns*:</span></span>

- <span data-ttu-id="31685-171">*Шаблон отрицания* `not`, который соответствует выражению, если шаблон с отрицанием не соответствует выражению.</span><span class="sxs-lookup"><span data-stu-id="31685-171">*Negation* `not` pattern that matches an expression when the negated pattern doesn't match the expression.</span></span> <span data-ttu-id="31685-172">В следующем примере показано, как можно инвертировать [шаблон константы](#constant-pattern) `null`, чтобы проверить, имеет ли выражение значение, отличное от NULL:</span><span class="sxs-lookup"><span data-stu-id="31685-172">The following example shows how you can negate a [constant](#constant-pattern) `null` pattern to check if an expression is non-null:</span></span>

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="NotPattern":::

- <span data-ttu-id="31685-173">*Шаблон конъюнкции* `and`, который соответствует выражению, если оба шаблона соответствуют этому выражению.</span><span class="sxs-lookup"><span data-stu-id="31685-173">*Conjunctive* `and` pattern that matches an expression when both patterns match the expression.</span></span> <span data-ttu-id="31685-174">В следующем примере показано, как можно объединить [реляционные шаблоны](#relational-patterns), чтобы проверить, находится ли значение в определенном диапазоне:</span><span class="sxs-lookup"><span data-stu-id="31685-174">The following example shows how you can combine [relational patterns](#relational-patterns) to check if a value is in a certain range:</span></span>

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="AndPattern":::

- <span data-ttu-id="31685-175">*Шаблон дизъюнкции* `or`, который соответствует выражению, если любой из шаблонов соответствует данному выражению, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-175">*Disjunctive* `or` pattern that matches an expression when either of patterns matches the expression, as the following example shows:</span></span>

  :::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="OrPattern":::

<span data-ttu-id="31685-176">Как показано в предыдущем примере, блоки объединения в шаблоне можно использовать многократно.</span><span class="sxs-lookup"><span data-stu-id="31685-176">As the preceding example shows, you can repeatedly use the pattern combinators in a pattern.</span></span>

<span data-ttu-id="31685-177">Блок объединения шаблонов `and` имеет более высокий приоритет, чем `or`.</span><span class="sxs-lookup"><span data-stu-id="31685-177">The `and` pattern combinator has higher precedence than `or`.</span></span> <span data-ttu-id="31685-178">Чтобы явно задать приоритет, используйте круглые скобки, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-178">To explicitly specify the precedence, use parentheses, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="WithParentheses":::

> [!NOTE]
> <span data-ttu-id="31685-179">Порядок проверки шаблонов не определен.</span><span class="sxs-lookup"><span data-stu-id="31685-179">The order in which patterns are checked is undefined.</span></span> <span data-ttu-id="31685-180">Во время выполнения можно сначала проверить правые вложенные шаблоны шаблонов `or` и `and`.</span><span class="sxs-lookup"><span data-stu-id="31685-180">At run time, the right-hand nested patterns of `or` and `and` patterns can be checked first.</span></span>

<span data-ttu-id="31685-181">Дополнительные сведения см. в разделе [Блоки объединения шаблонов](~/_csharplang/proposals/csharp-9.0/patterns3.md#pattern-combinators) в примечании к предлагаемой функции.</span><span class="sxs-lookup"><span data-stu-id="31685-181">For more information, see the [Pattern combinators](~/_csharplang/proposals/csharp-9.0/patterns3.md#pattern-combinators) section of the feature proposal note.</span></span>

## <a name="property-pattern"></a><span data-ttu-id="31685-182">Шаблон свойства</span><span class="sxs-lookup"><span data-stu-id="31685-182">Property pattern</span></span>

<span data-ttu-id="31685-183">Начиная с C# 8.0, вы можете использовать *шаблон свойства* для сопоставления свойств или полей выражения с вложенными шаблонами, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-183">Beginning with C# 8.0, you use a *property pattern* to match an expression's properties or fields against nested patterns, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="BasicExample":::

<span data-ttu-id="31685-184">Шаблон свойства соответствует выражению, если результат выражения не равен NULL, а каждый вложенный шаблон соответствует соответствующему свойству или полю результата выражения.</span><span class="sxs-lookup"><span data-stu-id="31685-184">A property pattern matches an expression when an expression result is non-null and every nested pattern matches the corresponding property or field of the expression result.</span></span>

<span data-ttu-id="31685-185">Вы также можете добавить в шаблон свойства проверку типа среды выполнения и объявление переменной, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-185">You can also add a runtime type check and a variable declaration to a property pattern, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="WithTypeCheck":::

<span data-ttu-id="31685-186">Шаблон свойства является рекурсивным шаблоном.</span><span class="sxs-lookup"><span data-stu-id="31685-186">A property pattern is a recursive pattern.</span></span> <span data-ttu-id="31685-187">Это значит, что любой шаблон можно использовать как вложенный шаблон.</span><span class="sxs-lookup"><span data-stu-id="31685-187">That is, you can use any pattern as a nested pattern.</span></span> <span data-ttu-id="31685-188">Используйте шаблон свойства для сопоставления элементов данных с вложенными шаблонами, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-188">Use a property pattern to match parts of data against nested patterns, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PropertyPattern.cs" id="RecursivePropertyPattern":::

<span data-ttu-id="31685-189">В предыдущем примере используются две возможности, доступные в C# 9.0 и более поздних версиях языка: [блок объединения шаблонов](#logical-patterns) `or`и [типы записей](../builtin-types/record.md).</span><span class="sxs-lookup"><span data-stu-id="31685-189">The preceding example uses two features available in C# 9.0 and later: `or` [pattern combinator](#logical-patterns) and [record types](../builtin-types/record.md).</span></span>

<span data-ttu-id="31685-190">Дополнительные сведения см. в разделе [Шаблон свойства ](~/_csharplang/proposals/csharp-8.0/patterns.md#property-pattern) в примечании к предлагаемой функции.</span><span class="sxs-lookup"><span data-stu-id="31685-190">For more information, see the [Property pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#property-pattern) section of the feature proposal note.</span></span>

## <a name="positional-pattern"></a><span data-ttu-id="31685-191">Позиционный шаблон</span><span class="sxs-lookup"><span data-stu-id="31685-191">Positional pattern</span></span>

<span data-ttu-id="31685-192">Начиная с C# 8.0, вы можете использовать *позиционный шаблон* для деконструкции результата выражения и сравнения результирующих значений с соответствующими вложенными шаблонами, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-192">Beginning with C# 8.0, you use a *positional pattern* to deconstruct an expression result and match the resulting values against the corresponding nested patterns, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="BasicExample":::

<span data-ttu-id="31685-193">В предыдущем примере тип выражения содержит метод [Deconstruct](../../deconstruct.md), используемый для деконструкции результата выражения.</span><span class="sxs-lookup"><span data-stu-id="31685-193">At the preceding example, the type of an expression contains the [Deconstruct](../../deconstruct.md) method, which is used to deconstruct an expression result.</span></span> <span data-ttu-id="31685-194">Можно также сопоставлять выражения [кортежных типов](../builtin-types/value-tuples.md) с позиционными шаблонами.</span><span class="sxs-lookup"><span data-stu-id="31685-194">You can also match expressions of [tuple types](../builtin-types/value-tuples.md) against positional patterns.</span></span> <span data-ttu-id="31685-195">Таким образом можно сопоставить несколько входных значений с различными шаблонами, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-195">In that way, you can match multiple inputs against various patterns, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="MatchTuple":::

<span data-ttu-id="31685-196">В предыдущем примере используются [реляционные](#relational-patterns) и [логические](#logical-patterns) шаблоны, доступные в C# 9.0 и более поздних версиях языка.</span><span class="sxs-lookup"><span data-stu-id="31685-196">The preceding example uses [relational](#relational-patterns) and [logical](#logical-patterns) patterns, which are available in C# 9.0 and later.</span></span>

<span data-ttu-id="31685-197">В позиционном шаблоне можно использовать имена элементов кортежа и параметры метода `Deconstruct`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-197">You can use the names of tuple elements and `Deconstruct` parameters in a positional pattern, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="UseIdentifiers":::

<span data-ttu-id="31685-198">Можно также расширить позиционный шаблон одним из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="31685-198">You can also extend a positional pattern in any of the following ways:</span></span>

- <span data-ttu-id="31685-199">Добавьте проверку типа среды выполнения и объявление переменной, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-199">Add a runtime type check and a variable declaration, as the following example shows:</span></span>

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="WithTypeCheck":::

  <span data-ttu-id="31685-200">В предыдущем примере используются [позиционные записи](../builtin-types/record.md#positional-syntax-for-property-definition), которые неявно обеспечивают выполнение метода `Deconstruct`.</span><span class="sxs-lookup"><span data-stu-id="31685-200">The preceding example uses [positional records](../builtin-types/record.md#positional-syntax-for-property-definition) that implicitly provide the `Deconstruct` method.</span></span>

- <span data-ttu-id="31685-201">Используйте [шаблон свойства](#property-pattern) в позиционном шаблоне, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-201">Use a [property pattern](#property-pattern) within a positional pattern, as the following example shows:</span></span>

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="WithPropertyPattern":::

- <span data-ttu-id="31685-202">Можно объединить два предыдущих варианта, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-202">Combine two preceding usages, as the following example shows:</span></span>

  :::code language="csharp" source="snippets/patterns/PositionalPattern.cs" id="CompletePositionalPattern":::

<span data-ttu-id="31685-203">Позиционный шаблон является рекурсивным шаблоном.</span><span class="sxs-lookup"><span data-stu-id="31685-203">A positional pattern is a recursive pattern.</span></span> <span data-ttu-id="31685-204">Это значит, что любой шаблон можно использовать как вложенный шаблон.</span><span class="sxs-lookup"><span data-stu-id="31685-204">That is, you can use any pattern as a nested pattern.</span></span>

<span data-ttu-id="31685-205">Дополнительные сведения см. в разделе [Позиционный шаблон](~/_csharplang/proposals/csharp-8.0/patterns.md#positional-pattern) в примечании к предлагаемой функции.</span><span class="sxs-lookup"><span data-stu-id="31685-205">For more information, see the [Positional pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#positional-pattern) section of the feature proposal note.</span></span>

## <a name="var-pattern"></a><span data-ttu-id="31685-206">Шаблон `var`</span><span class="sxs-lookup"><span data-stu-id="31685-206">`var` pattern</span></span>

<span data-ttu-id="31685-207">Начиная с C# 7.0, *шаблон* `var` можно использовать для сопоставления любого выражения, включая `null`, и присвоения результата сопоставления новой локальной переменной, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-207">Beginning with C# 7.0, you use a *`var` pattern* to match any expression, including `null`, and assign its result to a new local variable, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/VarPattern.cs" id="KeepInterimResult":::

<span data-ttu-id="31685-208">Шаблон `var` полезно использовать, если в логическом выражении вам требуется временная переменная для хранения результатов промежуточных вычислений.</span><span class="sxs-lookup"><span data-stu-id="31685-208">A `var` pattern is useful when you need a temporary variable within a Boolean expression to hold the result of intermediate calculations.</span></span> <span data-ttu-id="31685-209">Шаблон `var` также можно использовать, если требуется реализовать дополнительные проверки в условиях регистра `when` выражения или оператора `switch`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-209">You can also use a `var` pattern when you need to perform additional checks in `when` case guards of a `switch` expression or statement, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/VarPattern.cs" id="WithCaseGuards":::

<span data-ttu-id="31685-210">В предыдущем примере шаблон `var (x, y)` эквивалентен [позиционному шаблону ](#positional-pattern) `(var x, var y)`.</span><span class="sxs-lookup"><span data-stu-id="31685-210">In the preceding example, pattern `var (x, y)` is equivalent to a [positional pattern](#positional-pattern) `(var x, var y)`.</span></span>

<span data-ttu-id="31685-211">В шаблоне `var` тип объявленной переменной равен установленному во время компиляции типу выражения, сопоставляемого с данным шаблоном.</span><span class="sxs-lookup"><span data-stu-id="31685-211">In a `var` pattern, the type of a declared variable is the compile-time type of the expression that is matched against the pattern.</span></span>

<span data-ttu-id="31685-212">Дополнительные сведения см. в разделе [Шаблон var](~/_csharplang/proposals/csharp-8.0/patterns.md#var-pattern) в примечании к предлагаемой функции.</span><span class="sxs-lookup"><span data-stu-id="31685-212">For more information, see the [Var pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#var-pattern) section of the feature proposal note.</span></span>

## <a name="discard-pattern"></a><span data-ttu-id="31685-213">Шаблон пустой переменной</span><span class="sxs-lookup"><span data-stu-id="31685-213">Discard pattern</span></span>

<span data-ttu-id="31685-214">Начиная с C# 8.0, *шаблон пустой переменной* `_` используется для сопоставления любых выражений, включая `null`, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-214">Beginning with C# 8.0, you use a *discard pattern* `_` to match any expression, including `null`, as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/DiscardPattern.cs" id="BasicExample":::

<span data-ttu-id="31685-215">В предыдущем примере шаблон пустой переменной используется для обработки значения `null` и любых целочисленных значений, которые не соответствуют имеющимся членам перечисления <xref:System.DayOfWeek>.</span><span class="sxs-lookup"><span data-stu-id="31685-215">In the preceding example, a discard pattern is used to handle `null` and any integer value that doesn't have the corresponding member of the <xref:System.DayOfWeek> enumeration.</span></span> <span data-ttu-id="31685-216">Благодаря этому гарантируется, что выражение `switch` в приведенном примере сможет обработать все возможные входные значения.</span><span class="sxs-lookup"><span data-stu-id="31685-216">That guarantees that a `switch` expression in the example handles all possible input values.</span></span> <span data-ttu-id="31685-217">Если в выражении `switch` не используется шаблон пустой переменной и при этом ни один из шаблонов выражения не соответствует входным данным, среда выполнения [генерирует исключение](switch-expression.md#non-exhaustive-switch-expressions).</span><span class="sxs-lookup"><span data-stu-id="31685-217">If you don't use a discard pattern in a `switch` expression and none of the expression's patterns matches an input, the runtime [throws an exception](switch-expression.md#non-exhaustive-switch-expressions).</span></span> <span data-ttu-id="31685-218">Если выражение `switch` не обрабатывает все возможные входные значения, компилятор генерирует предупреждение.</span><span class="sxs-lookup"><span data-stu-id="31685-218">The compiler generates a warning if a `switch` expression doesn't handle all possible input values.</span></span>

<span data-ttu-id="31685-219">Шаблон пустой переменной не может быть шаблоном в выражении `is` или операторе `switch`.</span><span class="sxs-lookup"><span data-stu-id="31685-219">A discard pattern cannot be a pattern in an `is` expression or a `switch` statement.</span></span> <span data-ttu-id="31685-220">В этих случаях для сопоставления выражений используйте [шаблон](#var-pattern) `var` с пустой переменной: `var _`.</span><span class="sxs-lookup"><span data-stu-id="31685-220">In those cases, to match any expression, use a [`var` pattern](#var-pattern) with a discard: `var _`.</span></span>

<span data-ttu-id="31685-221">Дополнительные сведения см. в разделе [Шаблон пустой переменной](~/_csharplang/proposals/csharp-8.0/patterns.md#discard-pattern) в примечании к предлагаемой функции.</span><span class="sxs-lookup"><span data-stu-id="31685-221">For more information, see the [Discard pattern](~/_csharplang/proposals/csharp-8.0/patterns.md#discard-pattern) section of the feature proposal note.</span></span>

## <a name="parenthesized-pattern"></a><span data-ttu-id="31685-222">Шаблон в круглых скобках</span><span class="sxs-lookup"><span data-stu-id="31685-222">Parenthesized pattern</span></span>

<span data-ttu-id="31685-223">Начиная с C# 9.0, вы можете использовать круглые скобки вокруг любого шаблона.</span><span class="sxs-lookup"><span data-stu-id="31685-223">Beginning with C# 9.0, you can put parentheses around any pattern.</span></span> <span data-ttu-id="31685-224">Как правило, это делается для того, чтобы подчеркнуть или изменить приоритет [логических шаблонов](#logical-patterns), как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="31685-224">Typically, you do that to emphasize or change the precedence in [logical patterns](#logical-patterns), as the following example shows:</span></span>

:::code language="csharp" source="snippets/patterns/LogicalPatterns.cs" id="ChangedPrecedence":::

## <a name="c-language-specification"></a><span data-ttu-id="31685-225">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="31685-225">C# language specification</span></span>

<span data-ttu-id="31685-226">Дополнительные сведения см. в следующих примечаниях к предлагаемой функции.</span><span class="sxs-lookup"><span data-stu-id="31685-226">For more information, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="31685-227">Сопоставление шаблонов в C# 7.0</span><span class="sxs-lookup"><span data-stu-id="31685-227">Pattern matching for C# 7.0</span></span>](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [<span data-ttu-id="31685-228">Рекурсивное сопоставление шаблонов (впервые представлено в C# 8.0)</span><span class="sxs-lookup"><span data-stu-id="31685-228">Recursive pattern matching (introduced in C# 8.0)</span></span>](~/_csharplang/proposals/csharp-8.0/patterns.md)
- [<span data-ttu-id="31685-229">Изменения в сопоставлении шаблонов в C# 9.0</span><span class="sxs-lookup"><span data-stu-id="31685-229">Pattern-matching changes for C# 9.0</span></span>](~/_csharplang/proposals/csharp-9.0/patterns3.md)

## <a name="see-also"></a><span data-ttu-id="31685-230">См. также</span><span class="sxs-lookup"><span data-stu-id="31685-230">See also</span></span>

- [<span data-ttu-id="31685-231">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="31685-231">C# reference</span></span>](../index.md)
- [<span data-ttu-id="31685-232">Операторы и выражения C#</span><span class="sxs-lookup"><span data-stu-id="31685-232">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="31685-233">Учебник. Использование сопоставления шаблонов для создания управляемых типами и управляемых данными алгоритмов</span><span class="sxs-lookup"><span data-stu-id="31685-233">Tutorial: Use pattern matching to build type-driven and data-driven algorithms</span></span>](../../tutorials/pattern-matching.md)
