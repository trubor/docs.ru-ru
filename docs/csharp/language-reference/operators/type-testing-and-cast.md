---
title: Операторы проверки типа и выражения приведения — справочник по C#
description: Сведения об операторах C#, которые можно использовать для проверки типа результата выражения и преобразования его в другой тип, если потребуется.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
- as
- typeof
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: f47074fda20c1bc2eda75184dd26c9de1c0e3701
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075320"
---
# <a name="type-testing-operators-and-cast-expression-c-reference"></a><span data-ttu-id="5bce0-103">Операторы проверки типа и выражения приведения (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="5bce0-103">Type-testing operators and cast expression (C# reference)</span></span>

<span data-ttu-id="5bce0-104">Чтобы выполнить проверку или преобразование типов, можно использовать следующие операторы и выражения:</span><span class="sxs-lookup"><span data-stu-id="5bce0-104">You can use the following operators and expressions to perform type checking or type conversion:</span></span>

- <span data-ttu-id="5bce0-105">[оператор is](#is-operator) проверяет, совместим ли тип среды выполнения для определенного выражения с указанным типом;</span><span class="sxs-lookup"><span data-stu-id="5bce0-105">[is operator](#is-operator): to check if the runtime type of an expression is compatible with a given type</span></span>
- <span data-ttu-id="5bce0-106">[оператор as](#as-operator) явным образом преобразует выражение в указанный тип, если тип среды выполнения совместим с этим типом;</span><span class="sxs-lookup"><span data-stu-id="5bce0-106">[as operator](#as-operator): to explicitly convert an expression to a given type if its runtime type is compatible with that type</span></span>
- <span data-ttu-id="5bce0-107">[выражение приведения](#cast-expression) выполняет явное преобразование;</span><span class="sxs-lookup"><span data-stu-id="5bce0-107">[cast expression](#cast-expression): to perform an explicit conversion</span></span>
- <span data-ttu-id="5bce0-108">[оператор typeof](#typeof-operator) получает экземпляр <xref:System.Type?displayProperty=nameWithType> указанного типа.</span><span class="sxs-lookup"><span data-stu-id="5bce0-108">[typeof operator](#typeof-operator): to obtain the <xref:System.Type?displayProperty=nameWithType> instance for a type</span></span>

## <a name="is-operator"></a><span data-ttu-id="5bce0-109">Оператор is</span><span class="sxs-lookup"><span data-stu-id="5bce0-109">is operator</span></span>

<span data-ttu-id="5bce0-110">Оператор `is` проверяет, совместим ли тип среды выполнения для результата определенного выражения с указанным типом.</span><span class="sxs-lookup"><span data-stu-id="5bce0-110">The `is` operator checks if the runtime type of an expression result is compatible with a given type.</span></span> <span data-ttu-id="5bce0-111">Начиная с версии C# 7.0, оператор `is` также проверяет соответствие результата выражения указанному шаблону.</span><span class="sxs-lookup"><span data-stu-id="5bce0-111">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span>

<span data-ttu-id="5bce0-112">Выражение с оператором проверки типа `is` имеет следующий вид:</span><span class="sxs-lookup"><span data-stu-id="5bce0-112">The expression with the type-testing `is` operator has the following form</span></span>

```csharp
E is T
```

<span data-ttu-id="5bce0-113">где `E` представляет выражение, возвращающее значение, а `T` содержит имя или параметр типа.</span><span class="sxs-lookup"><span data-stu-id="5bce0-113">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter.</span></span> <span data-ttu-id="5bce0-114">`E` не может использоваться как анонимный метод или лямбда-выражение.</span><span class="sxs-lookup"><span data-stu-id="5bce0-114">`E` cannot be an anonymous method or a lambda expression.</span></span>

<span data-ttu-id="5bce0-115">Выражение `E is T` возвращает значение `true`, если результат выражения `E` отличен от NULL и может быть преобразован в тип `T` путем преобразования ссылки, упаковки-преобразования или распаковки-преобразования. В противном случае он возвращает `false`.</span><span class="sxs-lookup"><span data-stu-id="5bce0-115">The `E is T` expression returns `true` if the result of `E` is non-null and can be converted to type `T` by a reference conversion, a boxing conversion, or an unboxing conversion; otherwise, it returns `false`.</span></span> <span data-ttu-id="5bce0-116">Оператор `is` не учитывает заданные пользователем преобразования.</span><span class="sxs-lookup"><span data-stu-id="5bce0-116">The `is` operator doesn't consider user-defined conversions.</span></span>

<span data-ttu-id="5bce0-117">В следующем примере показано, что оператор `is` возвращает `true`, если тип среды выполнения для результата выражения является производным от указанного типа, то есть между этими типами существует преобразование ссылки:</span><span class="sxs-lookup"><span data-stu-id="5bce0-117">The following example demonstrates that the `is` operator returns `true` if the runtime type of an expression result derives from a given type, that is, there exists a reference conversion between types:</span></span>

[!code-csharp[is with reference conversion](snippets/shared/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

<span data-ttu-id="5bce0-118">В следующем примере показано, что оператор `is` учитывает упаковку-преобразование и распаковку-преобразование, но не учитывает [числовые преобразования](../builtin-types/numeric-conversions.md):</span><span class="sxs-lookup"><span data-stu-id="5bce0-118">The next example shows that the `is` operator takes into account boxing and unboxing conversions but doesn't consider [numeric conversions](../builtin-types/numeric-conversions.md):</span></span>

[!code-csharp-interactive[is with int](snippets/shared/TypeTestingAndConversionOperators.cs#IsWithInt)]

<span data-ttu-id="5bce0-119">Дополнительные сведения о преобразованиях в C# см. в главе [о преобразованиях](~/_csharplang/spec/conversions.md) в [спецификации по языку C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5bce0-119">For information about C# conversions, see the [Conversions](~/_csharplang/spec/conversions.md) chapter of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

### <a name="type-testing-with-pattern-matching"></a><span data-ttu-id="5bce0-120">Тестирование типов с сопоставлением шаблонов</span><span class="sxs-lookup"><span data-stu-id="5bce0-120">Type testing with pattern matching</span></span>

<span data-ttu-id="5bce0-121">Начиная с версии C# 7.0, оператор `is` также проверяет соответствие результата выражения указанному шаблону.</span><span class="sxs-lookup"><span data-stu-id="5bce0-121">Beginning with C# 7.0, the `is` operator also tests an expression result against a pattern.</span></span> <span data-ttu-id="5bce0-122">В следующем примере показано, как использовать [шаблон объявления](patterns.md#declaration-and-type-patterns) для проверки типа выражения в среде выполнения:</span><span class="sxs-lookup"><span data-stu-id="5bce0-122">The following example shows how to use a [declaration pattern](patterns.md#declaration-and-type-patterns) to check the runtime type of an expression:</span></span>

[!code-csharp-interactive[is with declaration pattern](snippets/shared/TypeTestingAndConversionOperators.cs#IsDeclarationPattern)]

<span data-ttu-id="5bce0-123">Дополнительные сведения о поддерживаемых шаблонах см. в разделе [Шаблоны](patterns.md).</span><span class="sxs-lookup"><span data-stu-id="5bce0-123">For information about the supported patterns, see [Patterns](patterns.md).</span></span>

## <a name="as-operator"></a><span data-ttu-id="5bce0-124">Оператор as</span><span class="sxs-lookup"><span data-stu-id="5bce0-124">as operator</span></span>

<span data-ttu-id="5bce0-125">Оператор `as` явным образом преобразует результат выражения в указанный ссылочный или поддерживающий значения NULL тип.</span><span class="sxs-lookup"><span data-stu-id="5bce0-125">The `as` operator explicitly converts the result of an expression to a given reference or nullable value type.</span></span> <span data-ttu-id="5bce0-126">Если такое преобразование невозможно, оператор `as` возвращает значение `null`.</span><span class="sxs-lookup"><span data-stu-id="5bce0-126">If the conversion is not possible, the `as` operator returns `null`.</span></span> <span data-ttu-id="5bce0-127">В отличие от [выражения приведения](#cast-expression), оператор `as` никогда не создает исключение.</span><span class="sxs-lookup"><span data-stu-id="5bce0-127">Unlike a [cast expression](#cast-expression), the `as` operator never throws an exception.</span></span>

<span data-ttu-id="5bce0-128">Выражение имеет такой формат:</span><span class="sxs-lookup"><span data-stu-id="5bce0-128">The expression of the form</span></span>

```csharp
E as T
```

<span data-ttu-id="5bce0-129">где `E` представляет выражение, возвращающее значение, а `T` содержит имя или параметр типа. Результат такого выражения аналогичен результату этого:</span><span class="sxs-lookup"><span data-stu-id="5bce0-129">where `E` is an expression that returns a value and `T` is the name of a type or a type parameter, produces the same result as</span></span>

```csharp
E is T ? (T)(E) : (T)null
```

<span data-ttu-id="5bce0-130">за исключением того, что `E` вычисляется только один раз.</span><span class="sxs-lookup"><span data-stu-id="5bce0-130">except that `E` is only evaluated once.</span></span>

<span data-ttu-id="5bce0-131">Оператор `as` рассматривает только преобразование ссылки, допускающие значение NULL преобразования, упаковку-преобразование и распаковку-преобразование.</span><span class="sxs-lookup"><span data-stu-id="5bce0-131">The `as` operator considers only reference, nullable, boxing, and unboxing conversions.</span></span> <span data-ttu-id="5bce0-132">Нельзя использовать оператор `as` для определенного пользователем преобразования.</span><span class="sxs-lookup"><span data-stu-id="5bce0-132">You cannot use the `as` operator to perform a user-defined conversion.</span></span> <span data-ttu-id="5bce0-133">Для этого используйте [выражение приведения](#cast-expression).</span><span class="sxs-lookup"><span data-stu-id="5bce0-133">To do that, use a [cast expression](#cast-expression).</span></span>

<span data-ttu-id="5bce0-134">В следующем примере иллюстрируется использование оператора `as`.</span><span class="sxs-lookup"><span data-stu-id="5bce0-134">The following example demonstrates the usage of the `as` operator:</span></span>

[!code-csharp-interactive[as operator](snippets/shared/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> <span data-ttu-id="5bce0-135">Как показано в примере выше, нужно сравнить результат выражения `as` со значением `null`, чтобы проверить, успешно ли выполнено преобразование.</span><span class="sxs-lookup"><span data-stu-id="5bce0-135">As the preceding example shows, you need to compare the result of the `as` expression with `null` to check if the conversion is successful.</span></span> <span data-ttu-id="5bce0-136">Начиная с версии C# 7.0, вы можете использовать [оператор is](#type-testing-with-pattern-matching) как для проверки успешного выполнения преобразования, так и для сохранения результата в переменной, если преобразование выполнено успешно.</span><span class="sxs-lookup"><span data-stu-id="5bce0-136">Beginning with C# 7.0, you can use the [is operator](#type-testing-with-pattern-matching) both to test if the conversion succeeds and, if it succeeds, assign its result to a new variable.</span></span>

## <a name="cast-expression"></a><span data-ttu-id="5bce0-137">Выражение приведения</span><span class="sxs-lookup"><span data-stu-id="5bce0-137">Cast expression</span></span>

<span data-ttu-id="5bce0-138">Выражение приведения в формате `(T)E` выполняет явное преобразование значения выражения `E` в тип `T`.</span><span class="sxs-lookup"><span data-stu-id="5bce0-138">A cast expression of the form `(T)E` performs an explicit conversion of the result of expression `E` to type `T`.</span></span> <span data-ttu-id="5bce0-139">Если явного преобразования из типа `E` в тип `T` не существует, возникает ошибка времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="5bce0-139">If no explicit conversion exists from the type of `E` to type `T`, a compile-time error occurs.</span></span> <span data-ttu-id="5bce0-140">Во время выполнения явное преобразование может завершиться сбоем, и выражение приведения может вызвать исключение.</span><span class="sxs-lookup"><span data-stu-id="5bce0-140">At run time, an explicit conversion might not succeed and a cast expression might throw an exception.</span></span>

<span data-ttu-id="5bce0-141">Приведенный ниже пример демонстрирует явное числовое преобразование и преобразование ссылки:</span><span class="sxs-lookup"><span data-stu-id="5bce0-141">The following example demonstrates explicit numeric and reference conversions:</span></span>

[!code-csharp-interactive[cast expression](snippets/shared/TypeTestingAndConversionOperators.cs#Cast)]

<span data-ttu-id="5bce0-142">Сведения о поддерживаемых явных преобразованиях см. в разделе [о явных преобразованиях](~/_csharplang/spec/conversions.md#explicit-conversions) в [спецификации по языку C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5bce0-142">For information about supported explicit conversions, see the [Explicit conversions](~/_csharplang/spec/conversions.md#explicit-conversions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span> <span data-ttu-id="5bce0-143">Сведения о том, как определять пользовательские операторы явного или неявного преобразования, см. в разделе [Операторы пользовательского преобразования](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="5bce0-143">For information about how to define a custom explicit or implicit type conversion, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="5bce0-144">Другие данные об использовании ()</span><span class="sxs-lookup"><span data-stu-id="5bce0-144">Other usages of ()</span></span>

<span data-ttu-id="5bce0-145">Используйте скобки, чтобы [вызвать метод или делегат](member-access-operators.md#invocation-expression-).</span><span class="sxs-lookup"><span data-stu-id="5bce0-145">You also use parentheses to [call a method or invoke a delegate](member-access-operators.md#invocation-expression-).</span></span>

<span data-ttu-id="5bce0-146">Кроме того, с помощью круглых скобок можно настраивать порядок выполнения операций в выражении.</span><span class="sxs-lookup"><span data-stu-id="5bce0-146">Other use of parentheses is to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="5bce0-147">Дополнительные сведения см. в разделе [Операторы C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="5bce0-147">For more information, see [C# operators](index.md).</span></span>

## <a name="typeof-operator"></a><span data-ttu-id="5bce0-148">typeof - оператор</span><span class="sxs-lookup"><span data-stu-id="5bce0-148">typeof operator</span></span>

<span data-ttu-id="5bce0-149">Оператор `typeof` получает экземпляр <xref:System.Type?displayProperty=nameWithType> для указанного типа.</span><span class="sxs-lookup"><span data-stu-id="5bce0-149">The `typeof` operator obtains the <xref:System.Type?displayProperty=nameWithType> instance for a type.</span></span> <span data-ttu-id="5bce0-150">Оператор `typeof` принимает в качестве аргумента имя типа или параметр типа, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="5bce0-150">The argument to the `typeof` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[typeof operator](snippets/shared/TypeTestingAndConversionOperators.cs#TypeOf)]

<span data-ttu-id="5bce0-151">Кроме того, оператор `typeof` можно использовать с несвязанными универсальными типами.</span><span class="sxs-lookup"><span data-stu-id="5bce0-151">You can also use the `typeof` operator with unbound generic types.</span></span> <span data-ttu-id="5bce0-152">В имени несвязанного универсального типа должно содержаться правильное количество запятых, то есть на одну меньше, чем число параметров этого типа.</span><span class="sxs-lookup"><span data-stu-id="5bce0-152">The name of an unbound generic type must contain the appropriate number of commas, which is one less than the number of type parameters.</span></span> <span data-ttu-id="5bce0-153">В следующем примере показано использование оператора `typeof` с несвязанным универсальным типом:</span><span class="sxs-lookup"><span data-stu-id="5bce0-153">The following example shows the usage of the `typeof` operator with an unbound generic type:</span></span>

[!code-csharp-interactive[typeof unbound generic](snippets/shared/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

<span data-ttu-id="5bce0-154">Оператор `typeof` не может принимать выражения в качестве аргументов.</span><span class="sxs-lookup"><span data-stu-id="5bce0-154">An expression cannot be an argument of the `typeof` operator.</span></span> <span data-ttu-id="5bce0-155">Чтобы получить экземпляр <xref:System.Type?displayProperty=nameWithType> для типа среды выполнения результата выражения, используйте метод <xref:System.Object.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5bce0-155">To get the <xref:System.Type?displayProperty=nameWithType> instance for the runtime type of an expression result, use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method.</span></span>

### <a name="type-testing-with-the-typeof-operator"></a><span data-ttu-id="5bce0-156">Тестирование типов с оператором `typeof`</span><span class="sxs-lookup"><span data-stu-id="5bce0-156">Type testing with the `typeof` operator</span></span>

<span data-ttu-id="5bce0-157">Используйте оператор `typeof` для проверки, совместим ли тип среды выполнения для определенного выражения с указанным типом.</span><span class="sxs-lookup"><span data-stu-id="5bce0-157">Use the `typeof` operator to check if the runtime type of the expression result exactly matches a given type.</span></span> <span data-ttu-id="5bce0-158">В следующем примере показано различие между проверкой типов с помощью оператора `typeof` и [оператора is](#is-operator):</span><span class="sxs-lookup"><span data-stu-id="5bce0-158">The following example demonstrates the difference between type checking performed with the `typeof` operator and the [is operator](#is-operator):</span></span>

[!code-csharp[typeof vs is](snippets/shared/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a><span data-ttu-id="5bce0-159">Возможность перегрузки оператора</span><span class="sxs-lookup"><span data-stu-id="5bce0-159">Operator overloadability</span></span>

<span data-ttu-id="5bce0-160">Операторы `is`, `as` и `typeof` перегрузить нельзя.</span><span class="sxs-lookup"><span data-stu-id="5bce0-160">The `is`, `as`, and `typeof` operators cannot be overloaded.</span></span>

<span data-ttu-id="5bce0-161">Определяемый пользователем тип нельзя использовать для перегрузки оператора `()`, но на его основе можно определить пользовательское преобразование типа и выполнить его с помощью выражения приведения.</span><span class="sxs-lookup"><span data-stu-id="5bce0-161">A user-defined type cannot overload the `()` operator, but can define custom type conversions that can be performed by a cast expression.</span></span> <span data-ttu-id="5bce0-162">Дополнительные сведения см. в разделе [Операторы пользовательского преобразования](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="5bce0-162">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5bce0-163">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="5bce0-163">C# language specification</span></span>

<span data-ttu-id="5bce0-164">Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="5bce0-164">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="5bce0-165">Оператор is</span><span class="sxs-lookup"><span data-stu-id="5bce0-165">The is operator</span></span>](~/_csharplang/spec/expressions.md#the-is-operator)
- [<span data-ttu-id="5bce0-166">Оператор as</span><span class="sxs-lookup"><span data-stu-id="5bce0-166">The as operator</span></span>](~/_csharplang/spec/expressions.md#the-as-operator)
- [<span data-ttu-id="5bce0-167">Выражения приведения</span><span class="sxs-lookup"><span data-stu-id="5bce0-167">Cast expressions</span></span>](~/_csharplang/spec/expressions.md#cast-expressions)
- [<span data-ttu-id="5bce0-168">Оператор typeof</span><span class="sxs-lookup"><span data-stu-id="5bce0-168">The typeof operator</span></span>](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a><span data-ttu-id="5bce0-169">См. также</span><span class="sxs-lookup"><span data-stu-id="5bce0-169">See also</span></span>

- [<span data-ttu-id="5bce0-170">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="5bce0-170">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5bce0-171">Операторы и выражения C#</span><span class="sxs-lookup"><span data-stu-id="5bce0-171">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="5bce0-172">Практическое руководство. Безопасное приведение с помощью сопоставления шаблонов, а также операторов is и as</span><span class="sxs-lookup"><span data-stu-id="5bce0-172">How to safely cast by using pattern matching and the is and as operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="5bce0-173">Универсальные шаблоны в .NET</span><span class="sxs-lookup"><span data-stu-id="5bce0-173">Generics in .NET</span></span>](../../../standard/generics/index.md)
