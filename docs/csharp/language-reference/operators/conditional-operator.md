---
description: Оператор ?:. Справочник по C#
title: Оператор ?:. Справочник по C#
ms.date: 09/17/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 84a740f3afeca94a706b4120b8cd8f191f49a048
ms.sourcegitcommit: bbc724b72fb6c978905ac715e4033efa291f84dc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107369573"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3ef08-103">Оператор ?: (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="3ef08-103">?: operator (C# reference)</span></span>

<span data-ttu-id="3ef08-104">Условный оператор `?:`, также называемый тернарным, вычисляет логическое выражение и в зависимости от полученного значения `true` или `false` возвращает результат одного из двух соответствующих выражений, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="3ef08-104">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`, as the following example shows:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="snippets/shared/ConditionalOperator.cs" id="BasicExample":::

<span data-ttu-id="3ef08-105">Как показано в предыдущем примере, синтаксис условного оператора выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="3ef08-105">As the preceding example shows, the syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="3ef08-106">Выражение `condition` должно принимать значение `true` или `false`.</span><span class="sxs-lookup"><span data-stu-id="3ef08-106">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="3ef08-107">Если `condition` принимает значение `true`, вычисляется выражение `consequent`, а результат становится результатом операции.</span><span class="sxs-lookup"><span data-stu-id="3ef08-107">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="3ef08-108">Если `condition` принимает значение `false`, вычисляется выражение `alternative`, а результат становится результатом операции.</span><span class="sxs-lookup"><span data-stu-id="3ef08-108">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="3ef08-109">Вычисляется только выражение `consequent` или `alternative`.</span><span class="sxs-lookup"><span data-stu-id="3ef08-109">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="3ef08-110">Начиная с C# 9.0 условные выражения имеют целевой тип.</span><span class="sxs-lookup"><span data-stu-id="3ef08-110">Beginning with C# 9.0, conditional expressions are target-typed.</span></span> <span data-ttu-id="3ef08-111">Это значит, что если известен целевой тип условного выражения, типы `consequent` и `alternative` должны быть неявно преобразованы в целевой тип, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="3ef08-111">That is, if a target type of a conditional expression is known, the types of `consequent` and `alternative` must be implicitly convertible to the target type, as the following example shows:</span></span>

[!code-csharp[target-typed conditional](snippets/shared/ConditionalOperator.cs#TargetTyped)]

<span data-ttu-id="3ef08-112">Если целевой тип условного выражения неизвестен (например, при использовании ключевого слова [`var`](../keywords/var.md)) или используются C# 8.0 и более ранние версии, типы `consequent` и `alternative` должны быть одинаковыми, либо должно поддерживаться неявное преобразование из одного типа в другой:</span><span class="sxs-lookup"><span data-stu-id="3ef08-112">If a target type of a conditional expression is unknown (for example, when you use the [`var`](../keywords/var.md) keyword) or in C# 8.0 and earlier, the type of `consequent` and `alternative` must be the same or there must be an implicit conversion from one type to the other:</span></span>

[!code-csharp[not target-typed conditional](snippets/shared/ConditionalOperator.cs#NotTargetTyped)]

<span data-ttu-id="3ef08-113">Условный оператор имеет правую ассоциативность, то есть выражение формы.</span><span class="sxs-lookup"><span data-stu-id="3ef08-113">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="3ef08-114">вычисляется как</span><span class="sxs-lookup"><span data-stu-id="3ef08-114">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="3ef08-115">Вы можете использовать следующий мнемонический прием, чтобы запомнить, как оценивается условный оператор:</span><span class="sxs-lookup"><span data-stu-id="3ef08-115">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

## <a name="conditional-ref-expression"></a><span data-ttu-id="3ef08-116">Условное выражение REF</span><span class="sxs-lookup"><span data-stu-id="3ef08-116">Conditional ref expression</span></span>

<span data-ttu-id="3ef08-117">Начиная с версии C# 7.2 [локальные переменные REF](../keywords/ref.md#ref-locals) и [предназначенные только для чтения локальные переменные REF](../keywords/ref.md#ref-readonly-locals) можно присваивать условным образом с использованием условного выражения REF.</span><span class="sxs-lookup"><span data-stu-id="3ef08-117">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with a conditional ref expression.</span></span> <span data-ttu-id="3ef08-118">Кроме того, условное выражение REF можно использовать как [возвращаемое ссылочное значение](../keywords/ref.md#reference-return-values) или как [аргумент метода `ref`](../keywords/ref.md#passing-an-argument-by-reference).</span><span class="sxs-lookup"><span data-stu-id="3ef08-118">You can also use a conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="3ef08-119">Для условного выражения REF используется следующий синтаксис:</span><span class="sxs-lookup"><span data-stu-id="3ef08-119">The syntax for a conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="3ef08-120">Подобно исходному условному оператору, условное выражение REF вычисляет только одно из двух выражений: `consequent` или `alternative`.</span><span class="sxs-lookup"><span data-stu-id="3ef08-120">Like the original conditional operator, a conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="3ef08-121">Для условного выражения REF типы `consequent` и `alternative` должны совпадать.</span><span class="sxs-lookup"><span data-stu-id="3ef08-121">In the case of a conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span> <span data-ttu-id="3ef08-122">Условные выражения REF не имеют целевого типа.</span><span class="sxs-lookup"><span data-stu-id="3ef08-122">Conditional ref expressions are not target-typed.</span></span>

<span data-ttu-id="3ef08-123">В следующем примере иллюстрируется использование условного выражения REF:</span><span class="sxs-lookup"><span data-stu-id="3ef08-123">The following example demonstrates the usage of a conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="3ef08-124">Условный оператор и оператор `if..else`</span><span class="sxs-lookup"><span data-stu-id="3ef08-124">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="3ef08-125">Если использовать условный оператор с оператором [if-else](../keywords/if-else.md), может получиться более лаконичный код в случаях, когда необходимо условно вычислить значение.</span><span class="sxs-lookup"><span data-stu-id="3ef08-125">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="3ef08-126">В следующем примере иллюстрируются два вида классификации целого числа как положительного или отрицательного:</span><span class="sxs-lookup"><span data-stu-id="3ef08-126">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="3ef08-127">Возможность перегрузки оператора</span><span class="sxs-lookup"><span data-stu-id="3ef08-127">Operator overloadability</span></span>

<span data-ttu-id="3ef08-128">Определяемый пользователем тип не может перегружать условный оператор.</span><span class="sxs-lookup"><span data-stu-id="3ef08-128">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3ef08-129">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="3ef08-129">C# language specification</span></span>

<span data-ttu-id="3ef08-130">Дополнительные сведения см. в разделе [Условный оператор](~/_csharplang/spec/expressions.md#conditional-operator) статьи [Предварительная спецификация C# 6.0](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="3ef08-130">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="3ef08-131">Дополнительные сведения о функциях, добавленных в C# 7.2 и более поздние версии, см. в следующих заметках о функциях.</span><span class="sxs-lookup"><span data-stu-id="3ef08-131">For more information about features added in C# 7.2 and later, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="3ef08-132">Условные выражения REF (C# 7.2)</span><span class="sxs-lookup"><span data-stu-id="3ef08-132">Conditional ref expressions (C# 7.2)</span></span>](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)
- [<span data-ttu-id="3ef08-133">Условное выражение с целевым типом (C# 9.0)</span><span class="sxs-lookup"><span data-stu-id="3ef08-133">Target-typed conditional expression (C# 9.0)</span></span>](~/_csharplang/proposals/csharp-9.0/target-typed-conditional-expression.md)

## <a name="see-also"></a><span data-ttu-id="3ef08-134">См. также</span><span class="sxs-lookup"><span data-stu-id="3ef08-134">See also</span></span>

- [<span data-ttu-id="3ef08-135">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="3ef08-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3ef08-136">Операторы и выражения C#</span><span class="sxs-lookup"><span data-stu-id="3ef08-136">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="3ef08-137">if-else (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="3ef08-137">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="3ef08-138">[Операторы ?. и ?[]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="3ef08-138">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="3ef08-139">Операторы ?? и ??=</span><span class="sxs-lookup"><span data-stu-id="3ef08-139">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="3ef08-140">Ключевое слово ref</span><span class="sxs-lookup"><span data-stu-id="3ef08-140">ref keyword</span></span>](../keywords/ref.md)
