---
title: Операторы и выражения для доступа к элементам. Справочник по C#
description: Дополнительные сведения об операторах C#, которые можно использовать для доступа к членам типа.
ms.date: 11/13/2020
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: b3ba56c7485d27d2692a589e2a8e5b330ea0de85
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873904"
---
# <a name="member-access-operators-and-expressions-c-reference"></a><span data-ttu-id="624d9-103">Операторы и выражения для доступа к элементам (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="624d9-103">Member access operators and expressions (C# reference)</span></span>

<span data-ttu-id="624d9-104">При получении доступа к элементу типа можно использовать следующие операторы и выражения:</span><span class="sxs-lookup"><span data-stu-id="624d9-104">You can use the following operators and expressions when you access a type member:</span></span>

- <span data-ttu-id="624d9-105">[`.` (доступ к члену) ](#member-access-expression-): для доступа к члену пространства имен или типа;</span><span class="sxs-lookup"><span data-stu-id="624d9-105">[`.` (member access)](#member-access-expression-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="624d9-106">[`[]` (элемент массива или индексатор доступа) ](#indexer-operator-): для доступа к элементу массива или индексатору типа;</span><span class="sxs-lookup"><span data-stu-id="624d9-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="624d9-107">[`?.` и `?[]` (null-условные операторы)](#null-conditional-operators--and-): для выполнения операции доступа члена или элемента только в том случае, если операнд не равен null;</span><span class="sxs-lookup"><span data-stu-id="624d9-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="624d9-108">[`()` (вызов) ](#invocation-expression-): для вызова метода или делегата.</span><span class="sxs-lookup"><span data-stu-id="624d9-108">[`()` (invocation)](#invocation-expression-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="624d9-109">[`^` (индекс от конца) ](#index-from-end-operator-): для определения того, что расположение элемента находится в конце последовательности.</span><span class="sxs-lookup"><span data-stu-id="624d9-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="624d9-110">[`..` (диапазон)](#range-operator-): для определения диапазона индексов, которые можно использовать для получения диапазона элементов последовательности.</span><span class="sxs-lookup"><span data-stu-id="624d9-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-expression-"></a><span data-ttu-id="624d9-111">Выражение доступа к члену</span><span class="sxs-lookup"><span data-stu-id="624d9-111">Member access expression .</span></span>

<span data-ttu-id="624d9-112">Маркер `.` используется для обращения к члену пространства имен или типа, как в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="624d9-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="624d9-113">Используйте `.` для обращения к пространству имен, вложенному в другое пространство имен, как показано в следующем примере [директивы `using`](../keywords/using-directive.md).</span><span class="sxs-lookup"><span data-stu-id="624d9-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/shared/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="624d9-114">Используйте `.` для создания *полного имени* для обращения к типу в пределах пространства имен, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="624d9-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/shared/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="624d9-115">Используйте [директиву `using`](../keywords/using-directive.md), чтобы сделать использование полных имен необязательным.</span><span class="sxs-lookup"><span data-stu-id="624d9-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="624d9-116">Используйте `.` для обращения к [членам типов](../../programming-guide/classes-and-structs/index.md#members) (статическим и нестатическим), как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="624d9-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/shared/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="624d9-117">Можно также использовать `.` для вызова [метода расширения](../../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="624d9-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="624d9-118">Оператор индексатора []</span><span class="sxs-lookup"><span data-stu-id="624d9-118">Indexer operator []</span></span>

<span data-ttu-id="624d9-119">Квадратные скобки, `[]`, обычно используются для доступа к элементам массива, индексатора или указателя.</span><span class="sxs-lookup"><span data-stu-id="624d9-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="624d9-120">Доступ к массиву</span><span class="sxs-lookup"><span data-stu-id="624d9-120">Array access</span></span>

<span data-ttu-id="624d9-121">В приведенном ниже примере показано, как получить доступ к элементам массива.</span><span class="sxs-lookup"><span data-stu-id="624d9-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/shared/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="624d9-122">Если индекс массива выходит за границы соответствующего измерения массива, возникает исключение <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="624d9-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="624d9-123">Как показано в предыдущем примере, квадратные скобки также используются в объявлении типа массива и для создания экземпляров массива.</span><span class="sxs-lookup"><span data-stu-id="624d9-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="624d9-124">Дополнительные сведения см. в руководстве по работе с [массивами](../../programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="624d9-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="624d9-125">Доступ к индексатору</span><span class="sxs-lookup"><span data-stu-id="624d9-125">Indexer access</span></span>

<span data-ttu-id="624d9-126">В приведенном ниже примере используется тип .NET <xref:System.Collections.Generic.Dictionary%602> для получения доступа к индексатору:</span><span class="sxs-lookup"><span data-stu-id="624d9-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/shared/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="624d9-127">Индексаторы позволяют индексировать экземпляры определяемого пользователем типа аналогично индексации массива.</span><span class="sxs-lookup"><span data-stu-id="624d9-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="624d9-128">В отличие от индексов массива, которые должны быть целым числом, параметры индексатора могут быть объявлены любым типом.</span><span class="sxs-lookup"><span data-stu-id="624d9-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="624d9-129">Дополнительные сведения см. в [руководстве по работе с индексаторами](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="624d9-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="624d9-130">Другие данные об использовании []</span><span class="sxs-lookup"><span data-stu-id="624d9-130">Other usages of []</span></span>

<span data-ttu-id="624d9-131">Сведения о доступе к элементу указателя см. в разделе, посвященном [оператору доступа к элементу указателя []](pointer-related-operators.md#pointer-element-access-operator-), статьи [Операторы, связанные с указателем](pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="624d9-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="624d9-132">Кроме того, с помощью квадратных скобок можно указывать [атрибуты](../../programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="624d9-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="624d9-133">NULL-условные операторы: ?.</span><span class="sxs-lookup"><span data-stu-id="624d9-133">Null-conditional operators ?.</span></span> <span data-ttu-id="624d9-134">и ?[]</span><span class="sxs-lookup"><span data-stu-id="624d9-134">and ?[]</span></span>

<span data-ttu-id="624d9-135">В C# 6 и более поздних версий доступен оператор с условием null, который применяется для [доступа к членам](#member-access-expression-), `?.`, или [доступа к элементам](#indexer-operator-), `?[]`, к операнду только в том случае, если он имеет значение, отличное от NULL, в противном случае он возвращает `null`.</span><span class="sxs-lookup"><span data-stu-id="624d9-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-expression-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="624d9-136">Это означает следующее:</span><span class="sxs-lookup"><span data-stu-id="624d9-136">That is,</span></span>

- <span data-ttu-id="624d9-137">Если `a` вычисляется как `null`, то результатом `a?.x` или `a?[x]` является `null`.</span><span class="sxs-lookup"><span data-stu-id="624d9-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="624d9-138">Если `a` принимает значение, отличное от NULL, результат `a?.x` или `a?[x]` совпадает с результатом `a.x` или `a[x]`соответственно.</span><span class="sxs-lookup"><span data-stu-id="624d9-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="624d9-139">Если `a.x` или `a[x]` вызывает исключение, `a?.x` или `a?[x]` вызовут то же исключение для отличного от NULL `a`.</span><span class="sxs-lookup"><span data-stu-id="624d9-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="624d9-140">Например, если `a` является экземпляром массива, не равным null, и `x` находится вне границ `a`, `a?[x]` вызовет <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="624d9-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="624d9-141">Операторы с условием NULL предусматривают сокращенную обработку.</span><span class="sxs-lookup"><span data-stu-id="624d9-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="624d9-142">То есть, если в цепочке операций условного доступа к элементу или члену одна из операций возвращает значение `null`, остальная цепочка не выполняется.</span><span class="sxs-lookup"><span data-stu-id="624d9-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="624d9-143">В следующем примере `B` не вычисляется, если `A` принимает значение `null`, и `C` не вычисляется, если `A` или `B` принимает значение `null`.</span><span class="sxs-lookup"><span data-stu-id="624d9-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="624d9-144">В следующем примере иллюстрируется использование операторов `?.` и `?[]`.</span><span class="sxs-lookup"><span data-stu-id="624d9-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/shared/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="624d9-145">В предыдущем примере также используется [оператор объединения со значением NULL `??`](null-coalescing-operator.md), чтобы указать альтернативное выражение для вычисления в случае, если результат выполнения условной операции NULL — это `null`.</span><span class="sxs-lookup"><span data-stu-id="624d9-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="624d9-146">Если `a.x` или `a[x]` является типом `T`, не допускающим значение NULL, `a?.x` или `a?[x]` является соответствующим [типом `T?`, допускающим значение NULL](../builtin-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="624d9-146">If `a.x` or `a[x]` is of a non-nullable value type `T`, `a?.x` or `a?[x]` is of the corresponding [nullable value type](../builtin-types/nullable-value-types.md) `T?`.</span></span> <span data-ttu-id="624d9-147">Если требуется выражение типа `T`, примените оператор объединения со значением NULL `??` к условному выражению NULL, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="624d9-147">If you need an expression of type `T`, apply the null-coalescing operator `??` to a null-conditional expression, as the following example shows:</span></span>

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/shared/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

<span data-ttu-id="624d9-148">Если в предыдущем примере оператор `??` не используется, `numbers?.Length < 2` вычисляется как `false`, если `numbers` имеет значение `null`.</span><span class="sxs-lookup"><span data-stu-id="624d9-148">In the preceding example, if you don't use the `??` operator, `numbers?.Length < 2` evaluates to `false` when `numbers` is `null`.</span></span>

<span data-ttu-id="624d9-149">Null-условный оператор доступа к элементу `?.` также называется элвис-оператором.</span><span class="sxs-lookup"><span data-stu-id="624d9-149">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="624d9-150">Потокобезопасный вызов делегата</span><span class="sxs-lookup"><span data-stu-id="624d9-150">Thread-safe delegate invocation</span></span>

<span data-ttu-id="624d9-151">Используйте оператор `?.` для проверки того, что делегат не равен null, и его вызова потокобезопасным способом (например, в том случае, когда вы собираетесь [породить событие](../../../standard/events/how-to-raise-and-consume-events.md)), как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="624d9-151">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="624d9-152">Этот код эквивалентен следующему коду, который будет использоваться в C# 5 или более ранней версии:</span><span class="sxs-lookup"><span data-stu-id="624d9-152">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

<span data-ttu-id="624d9-153">Этот потокобезопасный способ гарантирует, что вызывается только `handler`, не имеющий значения NULL.</span><span class="sxs-lookup"><span data-stu-id="624d9-153">That is a thread-safe way to ensure that only a non-null `handler` is invoked.</span></span> <span data-ttu-id="624d9-154">Так как экземпляры делегата являются неизменяемыми, ни один из потоков не может изменить объект, на который ссылается локальная переменная `handler`.</span><span class="sxs-lookup"><span data-stu-id="624d9-154">Because delegate instances are immutable, no thread can change the object referenced by the `handler` local variable.</span></span> <span data-ttu-id="624d9-155">В частности, если код, выполняемый другим потоком, отменяет подписку на событие `PropertyChanged` и событие `PropertyChanged` принимает значение `null` до вызова `handler`, объект, на который ссылается `handler`, остается неизменным.</span><span class="sxs-lookup"><span data-stu-id="624d9-155">In particular, if the code executed by another thread unsubscribes from the `PropertyChanged` event and `PropertyChanged` becomes `null` before `handler` is invoked, the object referenced by `handler` remains unaffected.</span></span> <span data-ttu-id="624d9-156">Оператор `?.` вычисляет левый операнд не более одного раза, гарантируя, что его нельзя изменить на `null` после того, как он пройдет проверку как не имеющий значение NULL.</span><span class="sxs-lookup"><span data-stu-id="624d9-156">The `?.` operator evaluates its left-hand operand no more than once, guaranteeing that it cannot be changed to `null` after being verified as non-null.</span></span>

## <a name="invocation-expression-"></a><span data-ttu-id="624d9-157">Выражения вызова ()</span><span class="sxs-lookup"><span data-stu-id="624d9-157">Invocation expression ()</span></span>

<span data-ttu-id="624d9-158">Используйте скобки, `()`, чтобы вызвать [метод](../../programming-guide/classes-and-structs/methods.md) или [делегат](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="624d9-158">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="624d9-159">Приведенный ниже пример демонстрирует вызов делегата и метода с аргументами или без них.</span><span class="sxs-lookup"><span data-stu-id="624d9-159">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/shared/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="624d9-160">Круглые скобки также можно использовать при вызове [конструктора](../../programming-guide/classes-and-structs/constructors.md) с оператором [`new`](new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="624d9-160">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="624d9-161">Другие данные об использовании ()</span><span class="sxs-lookup"><span data-stu-id="624d9-161">Other usages of ()</span></span>

<span data-ttu-id="624d9-162">Кроме того, с помощью круглых скобок можно настраивать порядок выполнения операций в выражении.</span><span class="sxs-lookup"><span data-stu-id="624d9-162">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="624d9-163">Дополнительные сведения см. в разделе [Операторы C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="624d9-163">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="624d9-164">В [выражениях приведения](type-testing-and-cast.md#cast-expression), которые выполняют явные преобразования типов, также используйте круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="624d9-164">[Cast expressions](type-testing-and-cast.md#cast-expression), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="624d9-165">Индекс от конца: оператор ^</span><span class="sxs-lookup"><span data-stu-id="624d9-165">Index from end operator ^</span></span>

<span data-ttu-id="624d9-166">Оператор `^`, доступный в C# 8.0 и последующих версиях, определяет расположение элемента от конца последовательности.</span><span class="sxs-lookup"><span data-stu-id="624d9-166">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="624d9-167">Для последовательности длины `length``^n` указывает на элемент с `length - n` смещения от начала последовательности.</span><span class="sxs-lookup"><span data-stu-id="624d9-167">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="624d9-168">Например, `^1` указывает на последний элемент последовательности, а `^length` — на первый элемент последовательности.</span><span class="sxs-lookup"><span data-stu-id="624d9-168">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/shared/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="624d9-169">В предыдущем примере выражение `^e` имеет тип <xref:System.Index?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="624d9-169">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="624d9-170">В выражении `^e` результат `e` должен быть неявно преобразован в `int`.</span><span class="sxs-lookup"><span data-stu-id="624d9-170">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="624d9-171">Можно также использовать оператор `^` с [оператором диапазона](#range-operator-) для создания диапазона индексов.</span><span class="sxs-lookup"><span data-stu-id="624d9-171">You can also use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="624d9-172">См. сведения в [руководстве по диапазонам и индексам](../../whats-new/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="624d9-172">For more information, see [Indices and ranges](../../whats-new/tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="624d9-173">Диапазон: оператор .</span><span class="sxs-lookup"><span data-stu-id="624d9-173">Range operator ..</span></span>

<span data-ttu-id="624d9-174">Оператор диапазона `..`, доступный в C# 8.0 и последующих версиях, определяет начало и конец диапазона индексов в качестве своих операндов.</span><span class="sxs-lookup"><span data-stu-id="624d9-174">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="624d9-175">Левый операнд является *инклюзивным* началом диапазона.</span><span class="sxs-lookup"><span data-stu-id="624d9-175">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="624d9-176">Правый операнд является *эксклюзивным* концом диапазона.</span><span class="sxs-lookup"><span data-stu-id="624d9-176">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="624d9-177">Любой из операндов может быть индексом от начала или конца последовательности, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="624d9-177">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/shared/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="624d9-178">В предыдущем примере выражение `a..b` имеет тип <xref:System.Range?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="624d9-178">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="624d9-179">В выражении `a..b` результаты `a` и `b` должны быть неявно преобразованы в `int` или <xref:System.Index>.</span><span class="sxs-lookup"><span data-stu-id="624d9-179">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="624d9-180">Можно проигнорировать любой из операндов оператора `..`, чтобы получить открытый диапазон:</span><span class="sxs-lookup"><span data-stu-id="624d9-180">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="624d9-181">`a..` — это эквивалент `a..^0`</span><span class="sxs-lookup"><span data-stu-id="624d9-181">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="624d9-182">`..b` — это эквивалент `0..b`</span><span class="sxs-lookup"><span data-stu-id="624d9-182">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="624d9-183">`..` — это эквивалент `0..^0`</span><span class="sxs-lookup"><span data-stu-id="624d9-183">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/shared/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="624d9-184">См. сведения в [руководстве по диапазонам и индексам](../../whats-new/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="624d9-184">For more information, see [Indices and ranges](../../whats-new/tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="624d9-185">Возможность перегрузки оператора</span><span class="sxs-lookup"><span data-stu-id="624d9-185">Operator overloadability</span></span>

<span data-ttu-id="624d9-186">Операторы `.`, `()`, `^` и `..` перегрузить нельзя.</span><span class="sxs-lookup"><span data-stu-id="624d9-186">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="624d9-187">Оператор `[]` также считается неперегружаемым.</span><span class="sxs-lookup"><span data-stu-id="624d9-187">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="624d9-188">Используйте [индексаторы](../../programming-guide/indexers/index.md) для поддержки индексирования с помощью определяемых пользователем типов.</span><span class="sxs-lookup"><span data-stu-id="624d9-188">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="624d9-189">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="624d9-189">C# language specification</span></span>

<span data-ttu-id="624d9-190">Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="624d9-190">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="624d9-191">Доступ к членам</span><span class="sxs-lookup"><span data-stu-id="624d9-191">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="624d9-192">Доступ к элементам</span><span class="sxs-lookup"><span data-stu-id="624d9-192">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="624d9-193">Null-условный оператор</span><span class="sxs-lookup"><span data-stu-id="624d9-193">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="624d9-194">Выражения вызова</span><span class="sxs-lookup"><span data-stu-id="624d9-194">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="624d9-195">См. сведения о индексах и диапазонах в [примечании к функциям](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="624d9-195">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="624d9-196">См. также</span><span class="sxs-lookup"><span data-stu-id="624d9-196">See also</span></span>

- [<span data-ttu-id="624d9-197">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="624d9-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="624d9-198">Операторы и выражения C#</span><span class="sxs-lookup"><span data-stu-id="624d9-198">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="624d9-199">Оператор ?? (оператор объединения со значением NULL)</span><span class="sxs-lookup"><span data-stu-id="624d9-199">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="624d9-200">Оператор ::</span><span class="sxs-lookup"><span data-stu-id="624d9-200">:: operator</span></span>](namespace-alias-qualifier.md)
