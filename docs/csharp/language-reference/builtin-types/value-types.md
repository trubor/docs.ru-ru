---
description: Сведения о типах значений, их видах и встроенных типах в C#
title: Справочник по C#. Типы значений
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 64c9e9eba2495531cfef8a603d53fb21c95c87a4
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599399"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="6e784-103">Типы значений (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="6e784-103">Value types (C# reference)</span></span>

<span data-ttu-id="6e784-104">*Типы значений* и [ссылочные типы](../keywords/reference-types.md) — это две основные категории типов C#.</span><span class="sxs-lookup"><span data-stu-id="6e784-104">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="6e784-105">Переменная типа значения содержит экземпляр типа.</span><span class="sxs-lookup"><span data-stu-id="6e784-105">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="6e784-106">Это отличается от переменной ссылочного типа, которая содержит ссылку на экземпляр типа.</span><span class="sxs-lookup"><span data-stu-id="6e784-106">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="6e784-107">По умолчанию при [назначении](../operators/assignment-operator.md), передаче аргумента в метод и возврате результата метода копируются значения переменных.</span><span class="sxs-lookup"><span data-stu-id="6e784-107">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="6e784-108">В случае переменных типа значения копируются соответствующие экземпляры типа.</span><span class="sxs-lookup"><span data-stu-id="6e784-108">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="6e784-109">В следующем примере продемонстрировано такое поведение.</span><span class="sxs-lookup"><span data-stu-id="6e784-109">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](snippets/shared/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="6e784-110">Как показано в предыдущем примере, операции с переменной типа значения влияют только на этот экземпляр типа значения, хранящийся в переменной.</span><span class="sxs-lookup"><span data-stu-id="6e784-110">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="6e784-111">Если тип значения содержит элемент данных ссылочного типа, то при копировании экземпляра типа значения копируется только ссылка на экземпляр ссылочного типа.</span><span class="sxs-lookup"><span data-stu-id="6e784-111">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="6e784-112">Как скопированный, так и исходный экземпляр типа значения имеют доступ к одному и тому же экземпляру ссылочного типа.</span><span class="sxs-lookup"><span data-stu-id="6e784-112">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="6e784-113">В следующем примере продемонстрировано такое поведение.</span><span class="sxs-lookup"><span data-stu-id="6e784-113">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](snippets/shared/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="6e784-114">Чтобы сделать код менее подверженным ошибкам и более надежным, определите и используйте неизменяемые типы значений.</span><span class="sxs-lookup"><span data-stu-id="6e784-114">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="6e784-115">В этой статье изменяемые типы значений используются только в демонстрационных целях.</span><span class="sxs-lookup"><span data-stu-id="6e784-115">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types-and-type-constraints"></a><span data-ttu-id="6e784-116">Виды типов значений и ограничения типов</span><span class="sxs-lookup"><span data-stu-id="6e784-116">Kinds of value types and type constraints</span></span>

<span data-ttu-id="6e784-117">Тип значения может относится к одному из двух следующих видов:</span><span class="sxs-lookup"><span data-stu-id="6e784-117">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="6e784-118">[тип структуры](struct.md), который инкапсулирует данные и связанные функции;</span><span class="sxs-lookup"><span data-stu-id="6e784-118">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="6e784-119">[тип перечисления](enum.md), который определяется набором именованных констант и представляет выбор или сочетание вариантов для выбора.</span><span class="sxs-lookup"><span data-stu-id="6e784-119">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="6e784-120">[Тип значений `T?`, допускающий значение NULL](nullable-value-types.md), представляет все значения своего базового типа значения `T`, а также дополнительное значение [NULL](../keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="6e784-120">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="6e784-121">Вы не можете назначить `null` переменной типа значения, если только это не тип, допускающий значение NULL.</span><span class="sxs-lookup"><span data-stu-id="6e784-121">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

<span data-ttu-id="6e784-122">Вы можете использовать [ограничение `struct`](../../programming-guide/generics/constraints-on-type-parameters.md), чтобы указать, что параметр типа является типом значения, не допускающим значения NULL.</span><span class="sxs-lookup"><span data-stu-id="6e784-122">You can use the [`struct` constraint](../../programming-guide/generics/constraints-on-type-parameters.md) to specify that a type parameter is a non-nullable value type.</span></span> <span data-ttu-id="6e784-123">Типы структуры и перечисления удовлетворяют ограничению `struct`.</span><span class="sxs-lookup"><span data-stu-id="6e784-123">Both structure and enumeration types satisfy the `struct` constraint.</span></span> <span data-ttu-id="6e784-124">Начиная с C# версии 7.3, вы можете использовать тип `System.Enum` в ограничении базового класса (которое известно как [ограничение перечисления](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)), чтобы указать, что параметр типа является типом перечисления.</span><span class="sxs-lookup"><span data-stu-id="6e784-124">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="6e784-125">Встроенные типы значений</span><span class="sxs-lookup"><span data-stu-id="6e784-125">Built-in value types</span></span>

<span data-ttu-id="6e784-126">C# предоставляет следующие встроенные типы значений, которые также называются *простыми типами*.</span><span class="sxs-lookup"><span data-stu-id="6e784-126">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="6e784-127">Целочисленные типы</span><span class="sxs-lookup"><span data-stu-id="6e784-127">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="6e784-128">Числовые типы с плавающей запятой</span><span class="sxs-lookup"><span data-stu-id="6e784-128">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="6e784-129">[bool](bool.md), представляющий логическое значение</span><span class="sxs-lookup"><span data-stu-id="6e784-129">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="6e784-130">[char](char.md), представляющий символ Юникода UTF-16</span><span class="sxs-lookup"><span data-stu-id="6e784-130">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="6e784-131">Все простые типы являются типами структур и отличаются от других типов структур тем, что разрешают некоторые дополнительные операции.</span><span class="sxs-lookup"><span data-stu-id="6e784-131">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="6e784-132">Литералы можно использовать для предоставления значения простого типа.</span><span class="sxs-lookup"><span data-stu-id="6e784-132">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="6e784-133">Например, `'A'` — это литерал типа `char`, а `2001` — литерал типа `int`.</span><span class="sxs-lookup"><span data-stu-id="6e784-133">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="6e784-134">Константы простых типов можно объявить с помощью ключевого слова [const](../keywords/const.md).</span><span class="sxs-lookup"><span data-stu-id="6e784-134">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="6e784-135">Невозможно использовать константы других типов структур.</span><span class="sxs-lookup"><span data-stu-id="6e784-135">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="6e784-136">Константные выражения, операнды которых являются константами простых типов, вычисляются во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="6e784-136">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="6e784-137">Начиная с версии 7.0 в языке C# поддерживаются [кортежи значений](value-tuples.md).</span><span class="sxs-lookup"><span data-stu-id="6e784-137">Beginning with C# 7.0, C# supports [value tuples](value-tuples.md).</span></span> <span data-ttu-id="6e784-138">Кортеж значений — это тип значения, не являющийся простым.</span><span class="sxs-lookup"><span data-stu-id="6e784-138">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6e784-139">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="6e784-139">C# language specification</span></span>

<span data-ttu-id="6e784-140">Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="6e784-140">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="6e784-141">Типы значений</span><span class="sxs-lookup"><span data-stu-id="6e784-141">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="6e784-142">Простые типы</span><span class="sxs-lookup"><span data-stu-id="6e784-142">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="6e784-143">Переменные</span><span class="sxs-lookup"><span data-stu-id="6e784-143">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="6e784-144">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6e784-144">See also</span></span>

- [<span data-ttu-id="6e784-145">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="6e784-145">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="6e784-146">Ссылочные типы</span><span class="sxs-lookup"><span data-stu-id="6e784-146">Reference types</span></span>](../keywords/reference-types.md)
