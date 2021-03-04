---
description: Дополнительные сведения о типе данных "UInteger"
title: Тип данных UInteger
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: c3c04f746f0e2cf15bc1881544b93a538dbdc04e
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104839"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="d9d04-103">UInteger - тип данных</span><span class="sxs-lookup"><span data-stu-id="d9d04-103">UInteger data type</span></span>

<span data-ttu-id="d9d04-104">Содержит 32-разрядные (4-байтные) целые числа без знака, имеющие значение от 0 до 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="d9d04-104">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="d9d04-105">Комментарии</span><span class="sxs-lookup"><span data-stu-id="d9d04-105">Remarks</span></span>

<span data-ttu-id="d9d04-106">`UInteger`Тип данных предоставляет наибольшее значение без знака в наиболее эффективной ширине данных.</span><span class="sxs-lookup"><span data-stu-id="d9d04-106">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="d9d04-107">Значение по умолчанию для типа `UInteger` — 0.</span><span class="sxs-lookup"><span data-stu-id="d9d04-107">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="d9d04-108">Присваивания литералов</span><span class="sxs-lookup"><span data-stu-id="d9d04-108">Literal assignments</span></span>

<span data-ttu-id="d9d04-109">Можно объявить и инициализировать `UInteger` переменную, назначив ей десятичный литерал, шестнадцатеричный литерал, Восьмеричный литерал или (начиная с Visual Basic 2017) двоичный литерал.</span><span class="sxs-lookup"><span data-stu-id="d9d04-109">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="d9d04-110">Если целочисленный литерал выходит за пределы диапазона `UInteger` (то есть, если он меньше <xref:System.UInt32.MinValue?displayProperty=nameWithType> или больше <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), возникает ошибка компиляции.</span><span class="sxs-lookup"><span data-stu-id="d9d04-110">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="d9d04-111">В следующем примере целые числа, равные 3 000 000 000 и представленные в виде десятичного, шестнадцатеричного и двоичного литерала, назначаются значениям `UInteger`.</span><span class="sxs-lookup"><span data-stu-id="d9d04-111">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="d9d04-112">Используйте префикс `&h` или `&H` , чтобы обозначить шестнадцатеричный литерал, префикс `&b` или `&B` обозначить двоичный литерал, а также префикс `&o` или `&O` обозначить Восьмеричный литерал.</span><span class="sxs-lookup"><span data-stu-id="d9d04-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="d9d04-113">У десятичных литералов префиксов нет.</span><span class="sxs-lookup"><span data-stu-id="d9d04-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="d9d04-114">Начиная с Visual Basic 2017, можно также использовать символ подчеркивания () в `_` качестве разделителя цифр, чтобы улучшить удобочитаемость, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d9d04-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="d9d04-115">Начиная с Visual Basic 15,5, можно также использовать символ подчеркивания () в `_` качестве начального разделителя между префиксом и шестнадцатеричными, двоичными или восьмеричными цифрами.</span><span class="sxs-lookup"><span data-stu-id="d9d04-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="d9d04-116">Пример:</span><span class="sxs-lookup"><span data-stu-id="d9d04-116">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="d9d04-117">Числовые литералы также могут включать `UI` `ui` [символ типа](../../programming-guide/language-features/data-types/type-characters.md) или для обозначения `UInteger` типа данных, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d9d04-117">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="d9d04-118">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="d9d04-118">Programming tips</span></span>

<span data-ttu-id="d9d04-119">`UInteger` `Integer` Типы данных и обеспечивают оптимальную производительность на 32-разрядном процессоре, поскольку меньшие целочисленные типы ( `UShort` ,, `Short` `Byte` и `SByte` ), даже если они используют меньшее количество битов, занимают больше времени на загрузку, хранение и выборку.</span><span class="sxs-lookup"><span data-stu-id="d9d04-119">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="d9d04-120">**Отрицательные числа.**</span><span class="sxs-lookup"><span data-stu-id="d9d04-120">**Negative Numbers.**</span></span> <span data-ttu-id="d9d04-121">Так как `UInteger` является неподписанным типом, он не может представлять отрицательное число.</span><span class="sxs-lookup"><span data-stu-id="d9d04-121">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="d9d04-122">При использовании оператора унарного минуса ( `-` ) в выражении, результатом которого является тип `UInteger` , Visual Basic преобразует выражение в `Long` First.</span><span class="sxs-lookup"><span data-stu-id="d9d04-122">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="d9d04-123">**Соответствие CLS.**</span><span class="sxs-lookup"><span data-stu-id="d9d04-123">**CLS Compliance.**</span></span> <span data-ttu-id="d9d04-124">`UInteger`Тип данных не является частью [спецификации](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/) CLS, поэтому CLS-совместимый код не может использовать компонент, который его использует.</span><span class="sxs-lookup"><span data-stu-id="d9d04-124">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="d9d04-125">**Вопросы взаимодействия.**</span><span class="sxs-lookup"><span data-stu-id="d9d04-125">**Interop Considerations.**</span></span> <span data-ttu-id="d9d04-126">Если вы взаимодействуете с компонентами, которые не написаны для платформа .NET Framework, например автоматизации или COM-объекты, помните, что такие типы, как, `uint` могут иметь разную ширину данных (16 бит) в других средах.</span><span class="sxs-lookup"><span data-stu-id="d9d04-126">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="d9d04-127">При передаче 16-разрядного аргумента в такой компонент объявите его как `UShort` вместо `UInteger` в управляемом коде Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d9d04-127">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="d9d04-128">**Расширяющие.**</span><span class="sxs-lookup"><span data-stu-id="d9d04-128">**Widening.**</span></span> <span data-ttu-id="d9d04-129">`UInteger`Тип данных расширяется до `Long` , `ULong` , `Decimal` , `Single` и `Double` .</span><span class="sxs-lookup"><span data-stu-id="d9d04-129">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="d9d04-130">Это означает, что можно преобразовать `UInteger` в любой из этих типов без возникновения <xref:System.OverflowException?displayProperty=nameWithType> ошибки.</span><span class="sxs-lookup"><span data-stu-id="d9d04-130">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="d9d04-131">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="d9d04-131">**Type Characters.**</span></span> <span data-ttu-id="d9d04-132">При добавлении символов типа литерала `UI` к литералу он применяет его к `UInteger` типу данных.</span><span class="sxs-lookup"><span data-stu-id="d9d04-132">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="d9d04-133">`UInteger` не имеет символа типа идентификатора.</span><span class="sxs-lookup"><span data-stu-id="d9d04-133">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="d9d04-134">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="d9d04-134">**Framework Type.**</span></span> <span data-ttu-id="d9d04-135">В .NET Framework данный тип соответствует структуре <xref:System.UInt32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d9d04-135">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9d04-136">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="d9d04-136">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="d9d04-137">Типы данных</span><span class="sxs-lookup"><span data-stu-id="d9d04-137">Data Types</span></span>](index.md)
- [<span data-ttu-id="d9d04-138">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="d9d04-138">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="d9d04-139">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="d9d04-139">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="d9d04-140">Практическое руководство. Вызов функции Windows, принимающей значение беззнакового типа</span><span class="sxs-lookup"><span data-stu-id="d9d04-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="d9d04-141">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="d9d04-141">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
