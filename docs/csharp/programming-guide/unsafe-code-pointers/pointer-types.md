---
title: Руководство по программированию на C#. Типы указателей
description: Сведения о типах указателей. Ознакомьтесь с примерами различных указателей, примерами кода и дополнительными ресурсами.
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 0e384084ef1fbb9139c11880ffa8a79bad23b32e
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480580"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="18585-104">Типы указателей (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="18585-104">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="18585-105">В небезопасном контексте тип может быть типом указателя, типом значения или ссылочным типом.</span><span class="sxs-lookup"><span data-stu-id="18585-105">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="18585-106">Объявления типа указателя выполняется одним из следующих способов:</span><span class="sxs-lookup"><span data-stu-id="18585-106">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="18585-107">Тип, указанный до `*` в типе указателя, называется **ссылочным типом**.</span><span class="sxs-lookup"><span data-stu-id="18585-107">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="18585-108">Ссылочным типом может быть только [неуправляемый тип](../../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="18585-108">Only an [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md) can be a referent type.</span></span>

<span data-ttu-id="18585-109">Типы указателей не наследуются от [объекта](../../language-reference/builtin-types/reference-types.md), а типы указателей не преобразуются в `object`.</span><span class="sxs-lookup"><span data-stu-id="18585-109">Pointer types do not inherit from [object](../../language-reference/builtin-types/reference-types.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="18585-110">Кроме того, упаковка-преобразование и распаковка-преобразование не поддерживают указатели.</span><span class="sxs-lookup"><span data-stu-id="18585-110">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="18585-111">Однако можно выполнять преобразования между различными типами указателей, а также между типами указателей и целочисленными типами.</span><span class="sxs-lookup"><span data-stu-id="18585-111">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="18585-112">При объявлении нескольких указателей в одном объявлении знак \* указывается только с базовым типом; он не используется в качестве префикса для каждого имени указателя.</span><span class="sxs-lookup"><span data-stu-id="18585-112">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="18585-113">Пример:</span><span class="sxs-lookup"><span data-stu-id="18585-113">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="18585-114">Указатель не может указывать на ссылку или на [структуру](../../language-reference/builtin-types/struct.md), содержащую ссылки, поскольку ссылка на объект может быть подвергнута сбору мусора, даже если на нее указывает указатель.</span><span class="sxs-lookup"><span data-stu-id="18585-114">A pointer cannot point to a reference or to a [struct](../../language-reference/builtin-types/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="18585-115">Сборщик мусора не отслеживает наличие указателей любых типов, указывающих на объекты.</span><span class="sxs-lookup"><span data-stu-id="18585-115">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="18585-116">Значением переменной-указателя типа `myType*` является адрес переменной типа `myType`.</span><span class="sxs-lookup"><span data-stu-id="18585-116">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="18585-117">Ниже приведены примеры объявлений типов указателей.</span><span class="sxs-lookup"><span data-stu-id="18585-117">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="18585-118">Пример</span><span class="sxs-lookup"><span data-stu-id="18585-118">Example</span></span>|<span data-ttu-id="18585-119">Описание</span><span class="sxs-lookup"><span data-stu-id="18585-119">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="18585-120">`p` — указатель на целое число.</span><span class="sxs-lookup"><span data-stu-id="18585-120">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="18585-121">`p` — указатель на указатель на целое число.</span><span class="sxs-lookup"><span data-stu-id="18585-121">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="18585-122">`p` — одномерный массив указателей на целые числа.</span><span class="sxs-lookup"><span data-stu-id="18585-122">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="18585-123">`p` — указатель на тип char.</span><span class="sxs-lookup"><span data-stu-id="18585-123">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="18585-124">`p` — указатель на неизвестный тип.</span><span class="sxs-lookup"><span data-stu-id="18585-124">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="18585-125">Оператор косвенного обращения указателя \* можно использовать для доступа к содержимому, на которое указывает переменная-указатель.</span><span class="sxs-lookup"><span data-stu-id="18585-125">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="18585-126">В качестве примера рассмотрим следующее объявление:</span><span class="sxs-lookup"><span data-stu-id="18585-126">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="18585-127">Выражение `*myVariable` обозначает переменную `int`, находящуюся по адресу, содержащемуся в `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="18585-127">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="18585-128">Разделы [Оператор fixed](../../language-reference/keywords/fixed-statement.md) и [Преобразования указателей](./pointer-conversions.md) содержат несколько примеров.</span><span class="sxs-lookup"><span data-stu-id="18585-128">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](./pointer-conversions.md).</span></span> <span data-ttu-id="18585-129">В следующем примере используются ключевое слово `unsafe` и оператор `fixed`, а также демонстрируется способ инкрементирования внутреннего указателя.</span><span class="sxs-lookup"><span data-stu-id="18585-129">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="18585-130">Этот код можно вставить в функцию Main консольного приложения для его запуска.</span><span class="sxs-lookup"><span data-stu-id="18585-130">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="18585-131">Эти примеры должны быть скомпилированы с заданным параметром [**AllowUnsafeBlocks**](../../language-reference/compiler-options/language.md#allowunsafeblocks).</span><span class="sxs-lookup"><span data-stu-id="18585-131">These examples must be compiled with the [**AllowUnsafeBlocks**](../../language-reference/compiler-options/language.md#allowunsafeblocks) compiler option set.</span></span>

[!code-csharp[Using pointer types](snippets/FixedKeywordExamples.cs#5)]

<span data-ttu-id="18585-132">Для указателя типа `void*` использовать оператор косвенного обращения нельзя.</span><span class="sxs-lookup"><span data-stu-id="18585-132">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="18585-133">Однако можно использовать приведение для преобразования указателя типа void в любой другой тип и наоборот.</span><span class="sxs-lookup"><span data-stu-id="18585-133">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="18585-134">Указатель может иметь значение `null`.</span><span class="sxs-lookup"><span data-stu-id="18585-134">A pointer can be `null`.</span></span> <span data-ttu-id="18585-135">При применении оператора косвенного обращения к указателю со значением null результат зависит от конкретной реализации.</span><span class="sxs-lookup"><span data-stu-id="18585-135">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="18585-136">При передаче указателей между методами может возникнуть неопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="18585-136">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="18585-137">Рекомендуется использовать метод, возвращающий указатель в локальную переменную с помощью параметра `in`, `out` или `ref` либо в виде результата функции.</span><span class="sxs-lookup"><span data-stu-id="18585-137">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="18585-138">Если указатель был задан в фиксированном блоке, переменная, на которую он указывает, больше не может быть фиксированной.</span><span class="sxs-lookup"><span data-stu-id="18585-138">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="18585-139">В следующей таблице перечислены операторы, которые можно использовать для указателей в небезопасном контексте.</span><span class="sxs-lookup"><span data-stu-id="18585-139">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="18585-140">Оператор</span><span class="sxs-lookup"><span data-stu-id="18585-140">Operator/Statement</span></span>|<span data-ttu-id="18585-141">Использовать</span><span class="sxs-lookup"><span data-stu-id="18585-141">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="18585-142">Косвенное обращение к указателю.</span><span class="sxs-lookup"><span data-stu-id="18585-142">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="18585-143">Доступ к члену структуры через указатель.</span><span class="sxs-lookup"><span data-stu-id="18585-143">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="18585-144">Индексирование указателя.</span><span class="sxs-lookup"><span data-stu-id="18585-144">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="18585-145">Получение адреса переменной.</span><span class="sxs-lookup"><span data-stu-id="18585-145">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="18585-146">`++` и `--`</span><span class="sxs-lookup"><span data-stu-id="18585-146">`++` and `--`</span></span>|<span data-ttu-id="18585-147">Увеличение и уменьшение указателей.</span><span class="sxs-lookup"><span data-stu-id="18585-147">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="18585-148">`+` и `-`</span><span class="sxs-lookup"><span data-stu-id="18585-148">`+` and `-`</span></span>|<span data-ttu-id="18585-149">Арифметические действия с указателем.</span><span class="sxs-lookup"><span data-stu-id="18585-149">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="18585-150">`==`, `!=`, `<`, `>`, `<=` и `>=`</span><span class="sxs-lookup"><span data-stu-id="18585-150">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="18585-151">Сравнение указателей.</span><span class="sxs-lookup"><span data-stu-id="18585-151">Compares pointers.</span></span>|
|[`stackalloc`](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="18585-152">Выделение памяти в стеке.</span><span class="sxs-lookup"><span data-stu-id="18585-152">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="18585-153">Инструкция `fixed`</span><span class="sxs-lookup"><span data-stu-id="18585-153">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="18585-154">Временная фиксация переменной, чтобы можно было найти ее адрес.</span><span class="sxs-lookup"><span data-stu-id="18585-154">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="18585-155">Дополнительные сведения об операторах, связанных с указателем, см. в разделе [Операторы, связанные с указателем](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="18585-155">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="18585-156">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="18585-156">C# language specification</span></span>

<span data-ttu-id="18585-157">Дополнительные сведения см. в разделе [Типы указателей](~/_csharplang/spec/unsafe-code.md#pointer-types) в статье [Спецификации языка C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="18585-157">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="18585-158">См. также</span><span class="sxs-lookup"><span data-stu-id="18585-158">See also</span></span>

- [<span data-ttu-id="18585-159">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="18585-159">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="18585-160">Небезопасный код и указатели</span><span class="sxs-lookup"><span data-stu-id="18585-160">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="18585-161">Преобразования указателей</span><span class="sxs-lookup"><span data-stu-id="18585-161">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="18585-162">Ссылочные типы</span><span class="sxs-lookup"><span data-stu-id="18585-162">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="18585-163">Типы значений</span><span class="sxs-lookup"><span data-stu-id="18585-163">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="18585-164">unsafe</span><span class="sxs-lookup"><span data-stu-id="18585-164">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
