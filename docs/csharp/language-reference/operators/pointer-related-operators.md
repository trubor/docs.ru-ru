---
title: Операторы, связанные с указателем — справочник по C#
description: Дополнительные сведения об операторах C#, которые можно использовать при работе с указателями.
ms.date: 05/20/2019
author: pkulikov
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- pointer related operators [C#]
- address-of operator [C#]
- '& operator [C#]'
- pointer indirection operator [C#]
- dereference operator [C#]
- '* operator [C#]'
- pointer member access operator [C#]
- -> operator [C#]
- pointer element access [C#]
- '[] operator [C#]'
- pointer arithmetic [C#]
- pointer increment [C#]
- pointer decrement [C#]
- pointer comparison [C#]
ms.openlocfilehash: 2d522e9357fb6da7b8d66a663e99e8858c9dd521
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480381"
---
# <a name="pointer-related-operators-c-reference"></a><span data-ttu-id="3de7f-103">Операторы, связанные с указателем (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="3de7f-103">Pointer related operators (C# reference)</span></span>

<span data-ttu-id="3de7f-104">Для работы с указателями можно использовать следующие операторы:</span><span class="sxs-lookup"><span data-stu-id="3de7f-104">You can use the following operators to work with pointers:</span></span>

- <span data-ttu-id="3de7f-105">Унарный оператор [`&` (address-of)](#address-of-operator-): для получения адреса переменной</span><span class="sxs-lookup"><span data-stu-id="3de7f-105">Unary [`&` (address-of)](#address-of-operator-) operator: to get the address of a variable</span></span>
- <span data-ttu-id="3de7f-106">Унарный оператор [`*` (косвенное обращение к указателю)](#pointer-indirection-operator-): для получения переменной, на которую указывает указатель</span><span class="sxs-lookup"><span data-stu-id="3de7f-106">Unary [`*` (pointer indirection)](#pointer-indirection-operator-) operator: to obtain the variable pointed by a pointer</span></span>
- <span data-ttu-id="3de7f-107">Операторы [`->` (доступ к членам)](#pointer-member-access-operator--) и [`[]` (доступ к элементам)](#pointer-element-access-operator-)</span><span class="sxs-lookup"><span data-stu-id="3de7f-107">The [`->` (member access)](#pointer-member-access-operator--) and [`[]` (element access)](#pointer-element-access-operator-) operators</span></span>
- <span data-ttu-id="3de7f-108">Арифметические операторы [`+`, `-`, `++` и `--`](#pointer-arithmetic-operators)</span><span class="sxs-lookup"><span data-stu-id="3de7f-108">Arithmetic operators [`+`, `-`, `++`, and `--`](#pointer-arithmetic-operators)</span></span>
- <span data-ttu-id="3de7f-109">Операторы сравнения [`==`, `!=`, `<`, `>`, `<=` и `>=`](#pointer-comparison-operators)</span><span class="sxs-lookup"><span data-stu-id="3de7f-109">Comparison operators [`==`, `!=`, `<`, `>`, `<=`, and `>=`](#pointer-comparison-operators)</span></span>

<span data-ttu-id="3de7f-110">Сведения о типах указателей см. в разделе [Типы указателей](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="3de7f-110">For information about pointer types, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

> [!NOTE]
> <span data-ttu-id="3de7f-111">Для всех операций с указателями требуется [небезопасный](../keywords/unsafe.md) контекст.</span><span class="sxs-lookup"><span data-stu-id="3de7f-111">Any operation with pointers requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="3de7f-112">Код, содержащий небезопасные блоки, должен компилироваться с параметром компилятора [**AllowUnsafeBlocks**](../compiler-options/language.md#allowunsafeblocks).</span><span class="sxs-lookup"><span data-stu-id="3de7f-112">The code that contains unsafe blocks must be compiled with the [**AllowUnsafeBlocks**](../compiler-options/language.md#allowunsafeblocks) compiler option.</span></span>

## <a name="address-of-operator-amp"></a><a name="address-of-operator-"></a> <span data-ttu-id="3de7f-113">Оператор address-of &amp;</span><span class="sxs-lookup"><span data-stu-id="3de7f-113">Address-of operator &amp;</span></span>

<span data-ttu-id="3de7f-114">Унарный оператор `&` возвращает адрес своего операнда:</span><span class="sxs-lookup"><span data-stu-id="3de7f-114">The unary `&` operator returns the address of its operand:</span></span>

[!code-csharp[address of local](snippets/shared/PointerOperators.cs#AddressOf)]

<span data-ttu-id="3de7f-115">Операнд оператора `&` должен быть фиксированной переменной.</span><span class="sxs-lookup"><span data-stu-id="3de7f-115">The operand of the `&` operator must be a fixed variable.</span></span> <span data-ttu-id="3de7f-116">*Фиксированные* переменные — это переменные в местах хранения, на которые не распространяется [сборка мусора](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="3de7f-116">*Fixed* variables are variables that reside in storage locations that are unaffected by operation of the [garbage collector](../../../standard/garbage-collection/index.md).</span></span> <span data-ttu-id="3de7f-117">В приведенном выше примере локальная переменная `number` — это фиксированная переменная, так как она находится в стеке.</span><span class="sxs-lookup"><span data-stu-id="3de7f-117">In the preceding example, the local variable `number` is a fixed variable, because it resides on the stack.</span></span> <span data-ttu-id="3de7f-118">Переменные, которые находятся в местах хранения, обслуживаемых сборщиком мусора (например, перемещение), называются *перемещаемыми* переменными.</span><span class="sxs-lookup"><span data-stu-id="3de7f-118">Variables that reside in storage locations that can be affected by the garbage collector (for example, relocated) are called *movable* variables.</span></span> <span data-ttu-id="3de7f-119">Поля объекта и элементы массива являются примерами перемещаемых переменных.</span><span class="sxs-lookup"><span data-stu-id="3de7f-119">Object fields and array elements are examples of movable variables.</span></span> <span data-ttu-id="3de7f-120">Вы можете получить адрес перемещаемой переменной, если зафиксируете или закрепите ее с помощью [ инструкции `fixed`](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3de7f-120">You can get the address of a movable variable if you "fix", or "pin", it with a [`fixed` statement](../keywords/fixed-statement.md).</span></span> <span data-ttu-id="3de7f-121">Полученный адрес действителен только в пределах блока инструкции `fixed`.</span><span class="sxs-lookup"><span data-stu-id="3de7f-121">The obtained address is valid only inside the block of a `fixed` statement.</span></span> <span data-ttu-id="3de7f-122">В следующем примере показано, как использовать инструкцию `fixed` и оператор `&`:</span><span class="sxs-lookup"><span data-stu-id="3de7f-122">The following example shows how to use a `fixed` statement and the `&` operator:</span></span>

[!code-csharp[address of fixed](snippets/shared/PointerOperators.cs#AddressOfFixed)]

<span data-ttu-id="3de7f-123">Получить адрес константы или значения нельзя.</span><span class="sxs-lookup"><span data-stu-id="3de7f-123">You can't get the address of a constant or a value.</span></span>

<span data-ttu-id="3de7f-124">Дополнительные сведения о фиксированных и перемещаемых переменных см. в разделе [Фиксированные и перемещаемые переменные](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) в [спецификации языка C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="3de7f-124">For more information about fixed and movable variables, see the [Fixed and moveable variables](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="3de7f-125">Бинарный оператор `&` вычисляет [логическое И](boolean-logical-operators.md#logical-and-operator-) своих логических операндов или [побитовое логическое И](bitwise-and-shift-operators.md#logical-and-operator-) своих целочисленных операндов.</span><span class="sxs-lookup"><span data-stu-id="3de7f-125">The binary `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its Boolean operands or the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its integral operands.</span></span>

## <a name="pointer-indirection-operator-"></a><span data-ttu-id="3de7f-126">Оператор косвенного обращения указателя \*</span><span class="sxs-lookup"><span data-stu-id="3de7f-126">Pointer indirection operator \*</span></span>

<span data-ttu-id="3de7f-127">Унарный оператор косвенного обращения указателя `*` получает переменную, на которую указывает операнд.</span><span class="sxs-lookup"><span data-stu-id="3de7f-127">The unary pointer indirection operator `*` obtains the variable to which its operand points.</span></span> <span data-ttu-id="3de7f-128">Он также называется оператором разыменования.</span><span class="sxs-lookup"><span data-stu-id="3de7f-128">It's also known as the dereference operator.</span></span> <span data-ttu-id="3de7f-129">Операнд оператора `*` должен иметь тип указателя.</span><span class="sxs-lookup"><span data-stu-id="3de7f-129">The operand of the `*` operator must be of a pointer type.</span></span>

[!code-csharp[pointer indirection](snippets/shared/PointerOperators.cs#PointerIndirection)]

<span data-ttu-id="3de7f-130">Невозможно применить оператор `*` к выражению типа `void*`.</span><span class="sxs-lookup"><span data-stu-id="3de7f-130">You cannot apply the `*` operator to an expression of type `void*`.</span></span>

<span data-ttu-id="3de7f-131">Бинарный оператор `*` вычисляет [продукт](arithmetic-operators.md#multiplication-operator-) своих числовых операндов.</span><span class="sxs-lookup"><span data-stu-id="3de7f-131">The binary `*` operator computes the [product](arithmetic-operators.md#multiplication-operator-) of its numeric operands.</span></span>

## <a name="pointer-member-access-operator--"></a><span data-ttu-id="3de7f-132">Оператор доступа к члену указателя -></span><span class="sxs-lookup"><span data-stu-id="3de7f-132">Pointer member access operator -></span></span>

<span data-ttu-id="3de7f-133">Оператор `->` объединяет [косвенное обращение к указателю](#pointer-indirection-operator-) и [доступ к члену](member-access-operators.md#member-access-expression-).</span><span class="sxs-lookup"><span data-stu-id="3de7f-133">The `->` operator combines [pointer indirection](#pointer-indirection-operator-) and [member access](member-access-operators.md#member-access-expression-).</span></span> <span data-ttu-id="3de7f-134">То есть если `x` — это указатель типа `T*`, а `y` является доступным членом типа `T`, выражение формы</span><span class="sxs-lookup"><span data-stu-id="3de7f-134">That is, if `x` is a pointer of type `T*` and `y` is an accessible member of type `T`, an expression of the form</span></span>

```csharp
x->y
```

<span data-ttu-id="3de7f-135">эквивалентно</span><span class="sxs-lookup"><span data-stu-id="3de7f-135">is equivalent to</span></span>

```csharp
(*x).y
```

<span data-ttu-id="3de7f-136">В следующем примере иллюстрируется использование оператора `->`.</span><span class="sxs-lookup"><span data-stu-id="3de7f-136">The following example demonstrates the usage of the `->` operator:</span></span>

[!code-csharp[pointer member access](snippets/shared/PointerOperators.cs#MemberAccess)]

<span data-ttu-id="3de7f-137">Невозможно применить оператор `->` к выражению типа `void*`.</span><span class="sxs-lookup"><span data-stu-id="3de7f-137">You cannot apply the `->` operator to an expression of type `void*`.</span></span>

## <a name="pointer-element-access-operator-"></a><span data-ttu-id="3de7f-138">Оператор доступа к элементу указателя []</span><span class="sxs-lookup"><span data-stu-id="3de7f-138">Pointer element access operator []</span></span>

<span data-ttu-id="3de7f-139">Для выражения `p` типа указателя доступ к элементу указателя формы `p[n]` вычисляется как `*(p + n)`, где `n` должен иметь тип, неявно преобразуемый в `int`, `uint`, `long` или `ulong`.</span><span class="sxs-lookup"><span data-stu-id="3de7f-139">For an expression `p` of a pointer type, a pointer element access of the form `p[n]` is evaluated as `*(p + n)`, where `n` must be of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`.</span></span> <span data-ttu-id="3de7f-140">Сведения о поведении оператора `+` с указателями см. в разделе [Сложение целочисленного значения с указателем или его вычитание из указателя](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer).</span><span class="sxs-lookup"><span data-stu-id="3de7f-140">For information about the behavior of the `+` operator with pointers, see the [Addition or subtraction of an integral value to or from a pointer](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) section.</span></span>

<span data-ttu-id="3de7f-141">Следующий пример демонстрирует доступ к элементам массива с указателем и оператором `[]`:</span><span class="sxs-lookup"><span data-stu-id="3de7f-141">The following example demonstrates how to access array elements with a pointer and the `[]` operator:</span></span>

[!code-csharp[pointer element access](snippets/shared/PointerOperators.cs#ElementAccess)]

<span data-ttu-id="3de7f-142">В предыдущем примере [выражение `stackalloc`](stackalloc.md) выделяет блок памяти в стеке.</span><span class="sxs-lookup"><span data-stu-id="3de7f-142">In the preceding example, a [`stackalloc` expression](stackalloc.md) allocates a block of memory on the stack.</span></span>

> [!NOTE]
> <span data-ttu-id="3de7f-143">Оператор доступа к элементу указателя не проверяет ошибки за пределами области.</span><span class="sxs-lookup"><span data-stu-id="3de7f-143">The pointer element access operator doesn't check for out-of-bounds errors.</span></span>

<span data-ttu-id="3de7f-144">Нельзя использовать `[]` для доступа к элементу указателя с помощью выражения типа `void*`.</span><span class="sxs-lookup"><span data-stu-id="3de7f-144">You cannot use `[]` for pointer element access with an expression of type `void*`.</span></span>

<span data-ttu-id="3de7f-145">Можно также использовать оператор `[]` для [доступа к элементу массива или индексатору](member-access-operators.md#indexer-operator-).</span><span class="sxs-lookup"><span data-stu-id="3de7f-145">You can also use the `[]` operator for [array element or indexer access](member-access-operators.md#indexer-operator-).</span></span>

## <a name="pointer-arithmetic-operators"></a><span data-ttu-id="3de7f-146">Арифметические операторы указателя</span><span class="sxs-lookup"><span data-stu-id="3de7f-146">Pointer arithmetic operators</span></span>

<span data-ttu-id="3de7f-147">Вы можете выполнить следующие арифметические операции с указателями:</span><span class="sxs-lookup"><span data-stu-id="3de7f-147">You can perform the following arithmetic operations with pointers:</span></span>

- <span data-ttu-id="3de7f-148">Сложение целочисленного значения с указателем или его вычитание из указателя</span><span class="sxs-lookup"><span data-stu-id="3de7f-148">Add or subtract an integral value to or from a pointer</span></span>
- <span data-ttu-id="3de7f-149">Вычитание двух указателей</span><span class="sxs-lookup"><span data-stu-id="3de7f-149">Subtract two pointers</span></span>
- <span data-ttu-id="3de7f-150">Инкремент или декремент указателя</span><span class="sxs-lookup"><span data-stu-id="3de7f-150">Increment or decrement a pointer</span></span>

<span data-ttu-id="3de7f-151">Невозможно выполнить эти операции с указателями типа `void*`.</span><span class="sxs-lookup"><span data-stu-id="3de7f-151">You cannot perform those operations with pointers of type `void*`.</span></span>

<span data-ttu-id="3de7f-152">Сведения о поддерживаемых арифметических операциях с числовыми типами см. в разделе [Арифметические операторы](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="3de7f-152">For information about supported arithmetic operations with numeric types, see [Arithmetic operators](arithmetic-operators.md).</span></span>

### <a name="addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer"></a><span data-ttu-id="3de7f-153">Сложение целочисленного значения с указателем или его вычитание из указателя</span><span class="sxs-lookup"><span data-stu-id="3de7f-153">Addition or subtraction of an integral value to or from a pointer</span></span>

<span data-ttu-id="3de7f-154">Для указателя `p` типа `T*` и выражения `n` типа, неявно преобразуемого в `int`, `uint`, `long` или `ulong`, сложение и вычитание определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="3de7f-154">For a pointer `p` of type `T*` and an expression `n` of a type implicitly convertible to `int`, `uint`, `long`, or `ulong`, addition and subtraction are defined as follows:</span></span>

- <span data-ttu-id="3de7f-155">Выражения `p + n` и `n + p` создают указатель типа `T*`, полученный добавлением `n * sizeof(T)` к адресу, предоставленному `p`.</span><span class="sxs-lookup"><span data-stu-id="3de7f-155">Both `p + n` and `n + p` expressions produce a pointer of type `T*` that results from adding `n * sizeof(T)` to the address given by `p`.</span></span>
- <span data-ttu-id="3de7f-156">Выражение `p - n` создает указатель типа `T*`, полученный вычитанием `n * sizeof(T)` из адреса, предоставленного `p`.</span><span class="sxs-lookup"><span data-stu-id="3de7f-156">The `p - n` expression produces a pointer of type `T*` that results from subtracting `n * sizeof(T)` from the address given by `p`.</span></span>

<span data-ttu-id="3de7f-157">[Оператор `sizeof`](sizeof.md) получает размер типа в байтах.</span><span class="sxs-lookup"><span data-stu-id="3de7f-157">The [`sizeof` operator](sizeof.md) obtains the size of a type in bytes.</span></span>

<span data-ttu-id="3de7f-158">В следующем примере показано использование оператора `+` с указателем:</span><span class="sxs-lookup"><span data-stu-id="3de7f-158">The following example demonstrates the usage of the `+` operator with a pointer:</span></span>

[!code-csharp[pointer addition](snippets/shared/PointerOperators.cs#AddNumber)]

### <a name="pointer-subtraction"></a><span data-ttu-id="3de7f-159">Вычитание указателей</span><span class="sxs-lookup"><span data-stu-id="3de7f-159">Pointer subtraction</span></span>

<span data-ttu-id="3de7f-160">Для двух указателей `p1` и `p2` типа `T*` выражение `p1 - p2` находит разность между адресами, предоставленными `p1` и `p2`, деленную на `sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="3de7f-160">For two pointers `p1` and `p2` of type `T*`, the expression `p1 - p2` produces the difference between the addresses given by `p1` and `p2` divided by `sizeof(T)`.</span></span> <span data-ttu-id="3de7f-161">Результат имеет тип `long`.</span><span class="sxs-lookup"><span data-stu-id="3de7f-161">The type of the result is `long`.</span></span> <span data-ttu-id="3de7f-162">То есть `p1 - p2` вычисляется как `((long)(p1) - (long)(p2)) / sizeof(T)`.</span><span class="sxs-lookup"><span data-stu-id="3de7f-162">That is, `p1 - p2` is computed as `((long)(p1) - (long)(p2)) / sizeof(T)`.</span></span>

<span data-ttu-id="3de7f-163">В следующем примере показано вычитание указателей:</span><span class="sxs-lookup"><span data-stu-id="3de7f-163">The following example demonstrates the pointer subtraction:</span></span>

[!code-csharp[pointer subtraction](snippets/shared/PointerOperators.cs#SubtractPointers)]

### <a name="pointer-increment-and-decrement"></a><span data-ttu-id="3de7f-164">Инкремент и декремент указателя</span><span class="sxs-lookup"><span data-stu-id="3de7f-164">Pointer increment and decrement</span></span>

<span data-ttu-id="3de7f-165">Оператор инкремента `++`[добавляет](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 к своему операнду указателя.</span><span class="sxs-lookup"><span data-stu-id="3de7f-165">The `++` increment operator [adds](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 to its pointer operand.</span></span> <span data-ttu-id="3de7f-166">Оператор декремента `--`[вычитает](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 из своего операнда указателя.</span><span class="sxs-lookup"><span data-stu-id="3de7f-166">The `--` decrement operator [subtracts](#addition-or-subtraction-of-an-integral-value-to-or-from-a-pointer) 1 from its pointer operand.</span></span>

<span data-ttu-id="3de7f-167">Оба оператора поддерживаются в двух формах: постфикс (`p++` и `p--`) и префикс (`++p` и `--p`).</span><span class="sxs-lookup"><span data-stu-id="3de7f-167">Both operators are supported in two forms: postfix (`p++` and `p--`) and prefix (`++p` and `--p`).</span></span> <span data-ttu-id="3de7f-168">Результат `p++` и `p--` — это значение `p` *перед* операцией.</span><span class="sxs-lookup"><span data-stu-id="3de7f-168">The result of `p++` and `p--` is the value of `p` *before* the operation.</span></span> <span data-ttu-id="3de7f-169">Результат `++p` и `--p` — это значение `p` *после* операции.</span><span class="sxs-lookup"><span data-stu-id="3de7f-169">The result of `++p` and `--p` is the value of `p` *after* the operation.</span></span>

<span data-ttu-id="3de7f-170">В следующем примере показано поведение постфиксных и префиксных операторов инкремента:</span><span class="sxs-lookup"><span data-stu-id="3de7f-170">The following example demonstrates the behavior of both postfix and prefix increment operators:</span></span>

[!code-csharp[pointer increment](snippets/shared/PointerOperators.cs#Increment)]

## <a name="pointer-comparison-operators"></a><span data-ttu-id="3de7f-171">Операторы сравнения указателей</span><span class="sxs-lookup"><span data-stu-id="3de7f-171">Pointer comparison operators</span></span>

<span data-ttu-id="3de7f-172">Вы можете использовать операторы `==`, `!=`, `<`, `>`, `<=` и `>=` для сравнения операндов любого типа указателя, включая `void*`.</span><span class="sxs-lookup"><span data-stu-id="3de7f-172">You can use the `==`, `!=`, `<`, `>`, `<=`, and `>=` operators to compare operands of any pointer type, including `void*`.</span></span> <span data-ttu-id="3de7f-173">Эти операторы сравнивают адреса, предоставленные двумя операндами, как если бы они были целыми числами без знака.</span><span class="sxs-lookup"><span data-stu-id="3de7f-173">Those operators compare the addresses given by the two operands as if they were unsigned integers.</span></span>

<span data-ttu-id="3de7f-174">Сведения о поведении этих операторов для операндов других типов см. в статьях [Операторы равенства](equality-operators.md) и [Операторы сравнения](comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="3de7f-174">For information about the behavior of those operators for operands of other types, see the [Equality operators](equality-operators.md) and [Comparison operators](comparison-operators.md) articles.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="3de7f-175">Приоритет операторов</span><span class="sxs-lookup"><span data-stu-id="3de7f-175">Operator precedence</span></span>

<span data-ttu-id="3de7f-176">В следующем списке операторы, связанные с указателями, упорядочены от самого высокого до самого низкого приоритета:</span><span class="sxs-lookup"><span data-stu-id="3de7f-176">The following list orders pointer related operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="3de7f-177">Постфиксные операторы инкремента `x++` и декремента `x--` и операторы `->` и `[]`</span><span class="sxs-lookup"><span data-stu-id="3de7f-177">Postfix increment `x++` and decrement `x--` operators and the `->` and `[]` operators</span></span>
- <span data-ttu-id="3de7f-178">Префиксные операторы инкремента `++x` и декремента `--x` и операторы `&` и `*`</span><span class="sxs-lookup"><span data-stu-id="3de7f-178">Prefix increment `++x` and decrement `--x` operators and the `&` and `*` operators</span></span>
- <span data-ttu-id="3de7f-179">Аддитивные операторы `+` и `-`</span><span class="sxs-lookup"><span data-stu-id="3de7f-179">Additive `+` and `-` operators</span></span>
- <span data-ttu-id="3de7f-180">Операторы сравнения `<`, `>`, `<=` и `>=`</span><span class="sxs-lookup"><span data-stu-id="3de7f-180">Comparison `<`, `>`, `<=`, and `>=` operators</span></span>
- <span data-ttu-id="3de7f-181">Операторы равенства `==` и `!=`</span><span class="sxs-lookup"><span data-stu-id="3de7f-181">Equality `==` and `!=` operators</span></span>

<span data-ttu-id="3de7f-182">Используйте скобки `()`, чтобы изменить порядок вычисления, накладываемый приоритетом операторов.</span><span class="sxs-lookup"><span data-stu-id="3de7f-182">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence.</span></span>

<span data-ttu-id="3de7f-183">Полный список операторов C#, упорядоченный по уровню приоритета, можно найти в разделе [Приоритет операторов](index.md#operator-precedence) статьи [Операторы C#](index.md).</span><span class="sxs-lookup"><span data-stu-id="3de7f-183">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="3de7f-184">Возможность перегрузки оператора</span><span class="sxs-lookup"><span data-stu-id="3de7f-184">Operator overloadability</span></span>

<span data-ttu-id="3de7f-185">Определяемый пользователем тип не может перегружать операторы, связанные с указателем, `&`, `*`, `->` и `[]`.</span><span class="sxs-lookup"><span data-stu-id="3de7f-185">A user-defined type cannot overload the pointer related operators `&`, `*`, `->`, and `[]`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3de7f-186">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="3de7f-186">C# language specification</span></span>

<span data-ttu-id="3de7f-187">Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="3de7f-187">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="3de7f-188">Фиксированные и перемещаемые переменные</span><span class="sxs-lookup"><span data-stu-id="3de7f-188">Fixed and moveable variables</span></span>](~/_csharplang/spec/unsafe-code.md#fixed-and-moveable-variables)
- [<span data-ttu-id="3de7f-189">Оператор address-of</span><span class="sxs-lookup"><span data-stu-id="3de7f-189">The address-of operator</span></span>](~/_csharplang/spec/unsafe-code.md#the-address-of-operator)
- [<span data-ttu-id="3de7f-190">Косвенное обращение к указателю</span><span class="sxs-lookup"><span data-stu-id="3de7f-190">Pointer indirection</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-indirection)
- [<span data-ttu-id="3de7f-191">Доступ к членам указателей</span><span class="sxs-lookup"><span data-stu-id="3de7f-191">Pointer member access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-member-access)
- [<span data-ttu-id="3de7f-192">Доступ к элементам указателей</span><span class="sxs-lookup"><span data-stu-id="3de7f-192">Pointer element access</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-element-access)
- [<span data-ttu-id="3de7f-193">Расчеты указателей</span><span class="sxs-lookup"><span data-stu-id="3de7f-193">Pointer arithmetic</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-arithmetic)
- [<span data-ttu-id="3de7f-194">Инкремент и декремент указателя</span><span class="sxs-lookup"><span data-stu-id="3de7f-194">Pointer increment and decrement</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-increment-and-decrement)
- [<span data-ttu-id="3de7f-195">Сравнение указателей</span><span class="sxs-lookup"><span data-stu-id="3de7f-195">Pointer comparison</span></span>](~/_csharplang/spec/unsafe-code.md#pointer-comparison)

## <a name="see-also"></a><span data-ttu-id="3de7f-196">См. также</span><span class="sxs-lookup"><span data-stu-id="3de7f-196">See also</span></span>

- [<span data-ttu-id="3de7f-197">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="3de7f-197">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3de7f-198">Операторы и выражения C#</span><span class="sxs-lookup"><span data-stu-id="3de7f-198">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="3de7f-199">Типы указателей</span><span class="sxs-lookup"><span data-stu-id="3de7f-199">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="3de7f-200">Ключевое слово unsafe</span><span class="sxs-lookup"><span data-stu-id="3de7f-200">unsafe keyword</span></span>](../keywords/unsafe.md)
- [<span data-ttu-id="3de7f-201">Ключевое слово fixed</span><span class="sxs-lookup"><span data-stu-id="3de7f-201">fixed keyword</span></span>](../keywords/fixed-statement.md)
- [<span data-ttu-id="3de7f-202">stackalloc</span><span class="sxs-lookup"><span data-stu-id="3de7f-202">stackalloc</span></span>](stackalloc.md)
- [<span data-ttu-id="3de7f-203">Оператор sizeof</span><span class="sxs-lookup"><span data-stu-id="3de7f-203">sizeof operator</span></span>](sizeof.md)
