---
title: Операторы равенства. Справочник по C#
description: Из этой статьи вы узнаете об операторах сравнения на равенство и типах равенства в C#.
ms.date: 10/30/2020
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: ee45869dff19712d8e4ef30f2fc01c2d4633acf1
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255458"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="29fb7-103">Операторы равенства (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="29fb7-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="29fb7-104">Операторы [`==` (равенство)](#equality-operator-) и [`!=` (неравенство)](#inequality-operator-) проверяют равенство или неравенство своих операндов.</span><span class="sxs-lookup"><span data-stu-id="29fb7-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="29fb7-105">Оператор равенства ==</span><span class="sxs-lookup"><span data-stu-id="29fb7-105">Equality operator ==</span></span>

<span data-ttu-id="29fb7-106">Оператор равенства `==` возвращает значение `true`, если его операнды равны. В противном случае возвращается значение `false`.</span><span class="sxs-lookup"><span data-stu-id="29fb7-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="29fb7-107">Равенство типов значений</span><span class="sxs-lookup"><span data-stu-id="29fb7-107">Value types equality</span></span>

<span data-ttu-id="29fb7-108">Операнды [встроенных типов значений](../builtin-types/value-types.md#built-in-value-types) равны, если равны их значения.</span><span class="sxs-lookup"><span data-stu-id="29fb7-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](snippets/shared/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="29fb7-109">У операторов `==`, [`<`, `>`, `<=` и `>=`](comparison-operators.md), если какой-то из операндов не является числом (<xref:System.Double.NaN?displayProperty=nameWithType> или <xref:System.Single.NaN?displayProperty=nameWithType>), результатом операции является `false`.</span><span class="sxs-lookup"><span data-stu-id="29fb7-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="29fb7-110">Это означает, что значение `NaN` не больше, не меньше и не равно любому другому значению `double` (или `float`), включая `NaN`.</span><span class="sxs-lookup"><span data-stu-id="29fb7-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="29fb7-111">Дополнительные сведения и примеры см. в справочных статьях по <xref:System.Double.NaN?displayProperty=nameWithType> или <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="29fb7-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="29fb7-112">Два операнда одного типа [enum](../builtin-types/enum.md) равны, если равны соответствующие значения базового целочисленного типа.</span><span class="sxs-lookup"><span data-stu-id="29fb7-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="29fb7-113">По умолчанию пользовательские типы [struct](../builtin-types/struct.md) не поддерживают оператор `==`.</span><span class="sxs-lookup"><span data-stu-id="29fb7-113">User-defined [struct](../builtin-types/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="29fb7-114">Чтобы поддерживать оператор `==`, пользовательская структура должна [перегружать](operator-overloading.md) его.</span><span class="sxs-lookup"><span data-stu-id="29fb7-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="29fb7-115">Начиная с версии C# 7.3 операторы `==` и `!=` поддерживаются [кортежами](../builtin-types/value-tuples.md) C#.</span><span class="sxs-lookup"><span data-stu-id="29fb7-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="29fb7-116">Дополнительные сведения см. в разделе [Равенство кортежей](../builtin-types/value-tuples.md#tuple-equality) статьи [Типы кортежей](../builtin-types/value-tuples.md).</span><span class="sxs-lookup"><span data-stu-id="29fb7-116">For more information, see the [Tuple equality](../builtin-types/value-tuples.md#tuple-equality) section of the [Tuple types](../builtin-types/value-tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="29fb7-117">Равенство ссылочных типов</span><span class="sxs-lookup"><span data-stu-id="29fb7-117">Reference types equality</span></span>

<span data-ttu-id="29fb7-118">По умолчанию два операнда ссылочного типа, отличные от записи, являются равными, если они ссылаются на один и тот же объект.</span><span class="sxs-lookup"><span data-stu-id="29fb7-118">By default, two non-record reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](snippets/shared/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="29fb7-119">Как показано в примере, определяемые пользователем ссылочные типы поддерживают оператор `==` по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="29fb7-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="29fb7-120">Однако ссылочный тип может перегружать оператор `==`.</span><span class="sxs-lookup"><span data-stu-id="29fb7-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="29fb7-121">Если ссылочный тип перегружает оператор `==`, воспользуйтесь методом <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>, чтобы проверить, что две ссылки этого типа указывают на один и тот же объект.</span><span class="sxs-lookup"><span data-stu-id="29fb7-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="record-types-equality"></a><span data-ttu-id="29fb7-122">Равенство типов записей</span><span class="sxs-lookup"><span data-stu-id="29fb7-122">Record types equality</span></span>

<span data-ttu-id="29fb7-123">[Типы записей](../builtin-types/record.md), доступные в C# 9.0 и более поздних версий, поддерживают операторы `==` и `!=`, которые по умолчанию обеспечивают семантику равенства значений.</span><span class="sxs-lookup"><span data-stu-id="29fb7-123">Available in C# 9.0 and later, [record types](../builtin-types/record.md) support the `==` and `!=` operators that by default provide value equality semantics.</span></span> <span data-ttu-id="29fb7-124">То есть два операнда записи равны, когда оба они равны `null` или равны соответствующие значения всех полей и автоматически реализуемых свойств.</span><span class="sxs-lookup"><span data-stu-id="29fb7-124">That is, two record operands are equal when both of them are `null` or corresponding values of all fields and auto-implemented properties are equal.</span></span>

:::code language="csharp" source="snippets/shared/EqualityOperators.cs" id="RecordTypesEquality":::

<span data-ttu-id="29fb7-125">Как показано в предыдущем примере, в случае с элементами ссылочного типа, отличными от записей, сравниваются их ссылочные значения, а не экземпляры, на которые они ссылаются.</span><span class="sxs-lookup"><span data-stu-id="29fb7-125">As the preceding example shows, in case of non-record reference-type members their reference values are compared, not the referenced instances.</span></span>

### <a name="string-equality"></a><span data-ttu-id="29fb7-126">Равенство строк</span><span class="sxs-lookup"><span data-stu-id="29fb7-126">String equality</span></span>

<span data-ttu-id="29fb7-127">Два операнда [string](../builtin-types/reference-types.md#the-string-type) равны, если они оба имеют значение `null` или оба экземпляра строки имеют одинаковую длину и идентичные символы в каждой позиции символа.</span><span class="sxs-lookup"><span data-stu-id="29fb7-127">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](snippets/shared/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="29fb7-128">Это порядковое сравнение, учитывающее регистр.</span><span class="sxs-lookup"><span data-stu-id="29fb7-128">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="29fb7-129">Дополнительные сведения о том, как сравнивать строки, см. в статье [Сравнение строк в C#](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="29fb7-129">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="29fb7-130">Равенство делегатов</span><span class="sxs-lookup"><span data-stu-id="29fb7-130">Delegate equality</span></span>

<span data-ttu-id="29fb7-131">Два операнда [delegate](../../programming-guide/delegates/index.md) одного типа среды выполнения равны, если оба из них имеют значение `null` или их списки вызовов имеют одинаковую длину и содержат одинаковые записи в каждой позиции:</span><span class="sxs-lookup"><span data-stu-id="29fb7-131">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](snippets/shared/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="29fb7-132">Подробные сведения см. в разделе [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) (Операторы равенства делегатов) в [спецификации языка C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="29fb7-132">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="29fb7-133">Делегаты, созданные в результате оценки семантически идентичных [лямбда-выражений](lambda-expressions.md) не будут равны, как показано в примере ниже:</span><span class="sxs-lookup"><span data-stu-id="29fb7-133">Delegates that are produced from evaluation of semantically identical [lambda expressions](lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](snippets/shared/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="29fb7-134">Оператор неравенства !=</span><span class="sxs-lookup"><span data-stu-id="29fb7-134">Inequality operator !=</span></span>

<span data-ttu-id="29fb7-135">Оператор неравенства `!=` возвращает значение `true`, если его операнды не равны. В противном случае возвращается значение `false`.</span><span class="sxs-lookup"><span data-stu-id="29fb7-135">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="29fb7-136">Для операндов [встроенных типов](../builtin-types/built-in-types.md) выражение `x != y` дает тот же результат, что и выражение `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="29fb7-136">For the operands of the [built-in types](../builtin-types/built-in-types.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="29fb7-137">Дополнительные сведения о равенстве типов см. в разделе [Оператор равенства](#equality-operator-).</span><span class="sxs-lookup"><span data-stu-id="29fb7-137">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="29fb7-138">В следующем примере иллюстрируется использование оператора `!=`.</span><span class="sxs-lookup"><span data-stu-id="29fb7-138">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](snippets/shared/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="29fb7-139">Возможность перегрузки оператора</span><span class="sxs-lookup"><span data-stu-id="29fb7-139">Operator overloadability</span></span>

<span data-ttu-id="29fb7-140">Определяемый пользователем тип может [перегружать](operator-overloading.md) операторы `==` и `!=`.</span><span class="sxs-lookup"><span data-stu-id="29fb7-140">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="29fb7-141">Если тип перегружает один из двух операторов, он должен также перегружать и другой.</span><span class="sxs-lookup"><span data-stu-id="29fb7-141">If a type overloads one of the two operators, it must also overload the other one.</span></span>

<span data-ttu-id="29fb7-142">Тип записи не может перегружать операторы `==` и `!=` явным образом.</span><span class="sxs-lookup"><span data-stu-id="29fb7-142">A record type cannot explicitly overload the `==` and `!=` operators.</span></span> <span data-ttu-id="29fb7-143">Если необходимо изменить поведение операторов `==` и `!=` для типа записи `T`, реализуйте метод <xref:System.IEquatable%601.Equals%2A?displayProperty=nameWithType> со следующей сигнатурой.</span><span class="sxs-lookup"><span data-stu-id="29fb7-143">If you need to change the behavior of the `==` and `!=` operators for record type `T`, implement the <xref:System.IEquatable%601.Equals%2A?displayProperty=nameWithType> method with the following signature:</span></span>

```csharp
public virtual bool Equals(T? other);
```

## <a name="c-language-specification"></a><span data-ttu-id="29fb7-144">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="29fb7-144">C# language specification</span></span>

<span data-ttu-id="29fb7-145">Дополнительные сведения см. в разделе [Операторы отношения и проверки типа](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) в статье по [спецификации языка C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="29fb7-145">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="29fb7-146">Дополнительные сведения о равенстве типов записей см. в разделе [Элементы равенства](~/_csharplang/proposals/csharp-9.0/records.md#equality-members) [предложения функции записей](~/_csharplang/proposals/csharp-9.0/records.md).</span><span class="sxs-lookup"><span data-stu-id="29fb7-146">For more information about equality of record types, see the [Equality members](~/_csharplang/proposals/csharp-9.0/records.md#equality-members) section of the [records feature proposal note](~/_csharplang/proposals/csharp-9.0/records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29fb7-147">См. также</span><span class="sxs-lookup"><span data-stu-id="29fb7-147">See also</span></span>

- [<span data-ttu-id="29fb7-148">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="29fb7-148">C# reference</span></span>](../index.md)
- [<span data-ttu-id="29fb7-149">Операторы и выражения C#</span><span class="sxs-lookup"><span data-stu-id="29fb7-149">C# operators and expressions</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="29fb7-150">Сравнения на равенство</span><span class="sxs-lookup"><span data-stu-id="29fb7-150">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="29fb7-151">Операторы сравнения</span><span class="sxs-lookup"><span data-stu-id="29fb7-151">Comparison operators</span></span>](comparison-operators.md)
