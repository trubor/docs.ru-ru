---
description: Справочник по C#. Арифметические операторы
title: Справочник по C#. Арифметические операторы
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 702652cc7ae05d6a2bfd419ebce55399b9403a52
ms.sourcegitcommit: 4b7f6b348c986556ef805cb6baacfd5b9ec18ed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2021
ms.locfileid: "107075437"
---
# <a name="assignment-operators-c-reference"></a><span data-ttu-id="a941a-103">Справочник по C#. Операторы присваивания</span><span class="sxs-lookup"><span data-stu-id="a941a-103">Assignment operators (C# reference)</span></span>

<span data-ttu-id="a941a-104">Оператор присваивания `=` назначает значение расположенного в правой части операнда переменной, [свойству](../../programming-guide/classes-and-structs/properties.md) или элементу [индексатора](../../programming-guide/indexers/index.md), которые указаны в операнде слева.</span><span class="sxs-lookup"><span data-stu-id="a941a-104">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="a941a-105">Результатом выражения присваивания является значение, назначенное расположенному слева операнду.</span><span class="sxs-lookup"><span data-stu-id="a941a-105">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="a941a-106">Расположенный справа операнд должен иметь тот же тип, что и операнд слева, либо же допускать неявное преобразование в этот тип.</span><span class="sxs-lookup"><span data-stu-id="a941a-106">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="a941a-107">Оператор присваивания `=` имеет правую ассоциативность, то есть выражение формы:</span><span class="sxs-lookup"><span data-stu-id="a941a-107">The assignment operator `=` is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="a941a-108">вычисляется как</span><span class="sxs-lookup"><span data-stu-id="a941a-108">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="a941a-109">В следующем примере показано использование оператора присваивания с локальной переменной, свойством и элементом индексатора в качестве левого операнда:</span><span class="sxs-lookup"><span data-stu-id="a941a-109">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](snippets/shared/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="a941a-110">Ссылочный оператор присваивания</span><span class="sxs-lookup"><span data-stu-id="a941a-110">ref assignment operator</span></span>

<span data-ttu-id="a941a-111">Начиная с C# 7.3, вы можете использовать ссылочный оператор присваивания `= ref`, чтобы переназначить [ссылочную локальную переменную](../keywords/ref.md#ref-locals) или [ссылочную локальную переменную только для чтения](../keywords/ref.md#ref-readonly-locals).</span><span class="sxs-lookup"><span data-stu-id="a941a-111">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="a941a-112">В следующем примере иллюстрируется использование ссылочного оператора присваивания:</span><span class="sxs-lookup"><span data-stu-id="a941a-112">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](snippets/shared/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="a941a-113">При использовании ссылочного оператора присваивания тип левого и правого операндов должен быть одинаковым.</span><span class="sxs-lookup"><span data-stu-id="a941a-113">In the case of the ref assignment operator, both of its operands must be of the same type.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="a941a-114">Составное присваивание</span><span class="sxs-lookup"><span data-stu-id="a941a-114">Compound assignment</span></span>

<span data-ttu-id="a941a-115">Для бинарного оператора `op` выражение составного присваивания в форме</span><span class="sxs-lookup"><span data-stu-id="a941a-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="a941a-116">эквивалентно</span><span class="sxs-lookup"><span data-stu-id="a941a-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="a941a-117">за исключением того, что `x` вычисляется только один раз.</span><span class="sxs-lookup"><span data-stu-id="a941a-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="a941a-118">Составное присваивание поддерживается [арифметическими](arithmetic-operators.md#compound-assignment), [логическими](boolean-logical-operators.md#compound-assignment), [побитовыми логическими операторами и операторами смещения](bitwise-and-shift-operators.md#compound-assignment).</span><span class="sxs-lookup"><span data-stu-id="a941a-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="a941a-119">Присваивание объединения со значением NULL</span><span class="sxs-lookup"><span data-stu-id="a941a-119">Null-coalescing assignment</span></span>

<span data-ttu-id="a941a-120">Начиная с C# 8.0 вы можете использовать оператор присваивания объединения со значением NULL `??=` для присваивания значения правого операнда левому операнду только в том случае, если левый операнд принимает значение `null`.</span><span class="sxs-lookup"><span data-stu-id="a941a-120">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="a941a-121">Дополнительные сведения см. в статье [Операторы ?? и ??=](null-coalescing-operator.md).</span><span class="sxs-lookup"><span data-stu-id="a941a-121">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="a941a-122">Возможность перегрузки оператора</span><span class="sxs-lookup"><span data-stu-id="a941a-122">Operator overloadability</span></span>

<span data-ttu-id="a941a-123">Пользовательский тип не может [перегружать](operator-overloading.md) оператор присваивания.</span><span class="sxs-lookup"><span data-stu-id="a941a-123">A user-defined type cannot [overload](operator-overloading.md) the assignment operator.</span></span> <span data-ttu-id="a941a-124">Однако пользовательский тип может определять неявное преобразование в другой тип.</span><span class="sxs-lookup"><span data-stu-id="a941a-124">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="a941a-125">Таким образом, значение пользовательского типа может быть присвоено переменной, свойству или элементу индексатора другого типа.</span><span class="sxs-lookup"><span data-stu-id="a941a-125">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="a941a-126">Дополнительные сведения см. в разделе [Операторы пользовательского преобразования](user-defined-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a941a-126">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

<span data-ttu-id="a941a-127">Определяемый пользователем тип не может перегружать оператор составного присваивания явным образом.</span><span class="sxs-lookup"><span data-stu-id="a941a-127">A user-defined type cannot explicitly overload a compound assignment operator.</span></span> <span data-ttu-id="a941a-128">Но если пользовательский тип перегружает бинарный оператор `op`, существующий оператор `op=` также будет неявно перегружен.</span><span class="sxs-lookup"><span data-stu-id="a941a-128">However, if a user-defined type overloads a binary operator `op`, the `op=` operator, if it exists, is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a941a-129">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="a941a-129">C# language specification</span></span>

<span data-ttu-id="a941a-130">Подробные сведения см. в разделе [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) (Операторы присваивания) в [спецификации языка C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a941a-130">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="a941a-131">См. сведения о ссылочном операторе присваивания `= ref` в [примечании к функциям](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span><span class="sxs-lookup"><span data-stu-id="a941a-131">For more information about the ref assignment operator `= ref`, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a941a-132">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a941a-132">See also</span></span>

- [<span data-ttu-id="a941a-133">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="a941a-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a941a-134">Операторы и выражения C#</span><span class="sxs-lookup"><span data-stu-id="a941a-134">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="a941a-135">Ключевое слово ref</span><span class="sxs-lookup"><span data-stu-id="a941a-135">ref keyword</span></span>](../keywords/ref.md)
