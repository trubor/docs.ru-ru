---
description: 'Дополнительные сведения: тип данных SByte (Visual Basic)'
title: Тип данных SByte
ms.date: 04/20/2017
f1_keywords:
- vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
ms.openlocfilehash: e6e314a34469083433289c0fff9b404d4549824d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792171"
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="ed2ad-103">Тип данных SByte (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed2ad-103">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="ed2ad-104">Содержит 8-битные (1-байтные) целые числа со знаком в диапазоне от-128 до 127.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-104">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>

## <a name="remarks"></a><span data-ttu-id="ed2ad-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="ed2ad-105">Remarks</span></span>

<span data-ttu-id="ed2ad-106">Используйте `SByte` тип данных для хранения целочисленных значений, не требующих полной ширины данных `Integer` или даже половины ширины данных `Short` .</span><span class="sxs-lookup"><span data-stu-id="ed2ad-106">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="ed2ad-107">В некоторых случаях среда CLR может `SByte` одновременно упаковать переменные и сэкономить потребление памяти.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-107">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="ed2ad-108">Значение по умолчанию для типа `SByte` — 0.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-108">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="ed2ad-109">Присваивания литералов</span><span class="sxs-lookup"><span data-stu-id="ed2ad-109">Literal assignments</span></span>

<span data-ttu-id="ed2ad-110">Вы можете объявить и инициализировать `SByte` переменную, назначив ей десятичный литерал, шестнадцатеричный литерал, Восьмеричный литерал или (начиная с Visual Basic 2017) двоичный литерал.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-110">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="ed2ad-111">В следующем примере целые числа, равные-102, представленные в виде десятичных, шестнадцатеричных и двоичных литералов, присваиваются `SByte` значениям.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-111">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="ed2ad-112">В этом примере требуется компилировать с `/removeintchecks` параметром компилятора.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-112">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]

> [!NOTE]
> <span data-ttu-id="ed2ad-113">Используйте префикс `&h` или `&H` , чтобы обозначить шестнадцатеричный литерал, префикс `&b` или `&B` обозначить двоичный литерал, а также префикс `&o` или `&O` обозначить Восьмеричный литерал.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-113">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="ed2ad-114">У десятичных литералов префиксов нет.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="ed2ad-115">Начиная с Visual Basic 2017, можно также использовать символ подчеркивания () в `_` качестве разделителя цифр, чтобы улучшить удобочитаемость, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-115">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]

<span data-ttu-id="ed2ad-116">Начиная с Visual Basic 15,5, можно также использовать символ подчеркивания () в `_` качестве начального разделителя между префиксом и шестнадцатеричными, двоичными или восьмеричными цифрами.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-116">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="ed2ad-117">Пример:</span><span class="sxs-lookup"><span data-stu-id="ed2ad-117">For example:</span></span>

```vb
Dim number As SByte = &H_F9
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="ed2ad-118">Если целочисленный литерал выходит за пределы диапазона `SByte` (то есть, если он меньше <xref:System.SByte.MinValue?displayProperty=nameWithType> или больше <xref:System.SByte.MaxValue?displayProperty=nameWithType>), возникает ошибка компиляции.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-118">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="ed2ad-119">Если у целочисленного литерала нет суффикса, выводится [целое число](integer-data-type.md) .</span><span class="sxs-lookup"><span data-stu-id="ed2ad-119">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="ed2ad-120">Если целочисленный литерал находится за пределами диапазона `Integer` типа, выводится значение [Long](long-data-type.md) .</span><span class="sxs-lookup"><span data-stu-id="ed2ad-120">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="ed2ad-121">Это означает, что в предыдущих примерах числовые литералы и обрабатываются `0x9A` `0b10011010` как 32-разрядные целые числа со знаком со значением 156, что превышает <xref:System.SByte.MaxValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ed2ad-121">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ed2ad-122">Чтобы успешно скомпилировать код, подобный этому, который присваивает недесятичное целое число `SByte` , можно выполнить одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-122">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="ed2ad-123">Отключает проверку целочисленных границ путем компиляции с `/removeintchecks` переключателем компилятора.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-123">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="ed2ad-124">Используйте [символ типа](../../programming-guide/language-features/data-types/type-characters.md) , чтобы явно определить литеральное значение, которое нужно присвоить `SByte` .</span><span class="sxs-lookup"><span data-stu-id="ed2ad-124">Use a [type character](../../programming-guide/language-features/data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="ed2ad-125">В следующем примере для переназначается отрицательное литеральное `Short` значение `SByte` .</span><span class="sxs-lookup"><span data-stu-id="ed2ad-125">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="ed2ad-126">Обратите внимание, что для отрицательных чисел необходимо задать старшие разрядные слова в числовом литерале с высоким порядком.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-126">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="ed2ad-127">В нашем примере это бит 15 литерального `Short` значения.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-127">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="ed2ad-128">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="ed2ad-128">Programming tips</span></span>

- <span data-ttu-id="ed2ad-129">**Соответствие CLS.**</span><span class="sxs-lookup"><span data-stu-id="ed2ad-129">**CLS Compliance.**</span></span> <span data-ttu-id="ed2ad-130">`SByte`Тип данных не является частью [спецификации](https://www.ecma-international.org/publications/standards/Ecma-335.htm) CLS, поэтому CLS-совместимый код не может использовать компонент, который его использует.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-130">The `SByte` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="ed2ad-131">**Расширяющие.**</span><span class="sxs-lookup"><span data-stu-id="ed2ad-131">**Widening.**</span></span> <span data-ttu-id="ed2ad-132">`SByte`Тип данных расширяется до `Short` , `Integer` ,,, `Long` `Decimal` `Single` и `Double` .</span><span class="sxs-lookup"><span data-stu-id="ed2ad-132">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="ed2ad-133">Это означает, что можно преобразовать `SByte` в любой из этих типов без возникновения <xref:System.OverflowException?displayProperty=nameWithType> ошибки.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-133">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="ed2ad-134">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="ed2ad-134">**Type Characters.**</span></span> <span data-ttu-id="ed2ad-135">`SByte` не имеет символа типа литерала или символа типа идентификатора.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-135">`SByte` has no literal type character or identifier type character.</span></span>

- <span data-ttu-id="ed2ad-136">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="ed2ad-136">**Framework Type.**</span></span> <span data-ttu-id="ed2ad-137">В .NET Framework данный тип соответствует структуре <xref:System.SByte?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ed2ad-137">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed2ad-138">См. также</span><span class="sxs-lookup"><span data-stu-id="ed2ad-138">See also</span></span>

- <xref:System.SByte?displayProperty=nameWithType>
- [<span data-ttu-id="ed2ad-139">Типы данных</span><span class="sxs-lookup"><span data-stu-id="ed2ad-139">Data Types</span></span>](index.md)
- [<span data-ttu-id="ed2ad-140">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="ed2ad-140">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="ed2ad-141">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="ed2ad-141">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="ed2ad-142">Тип данных Short</span><span class="sxs-lookup"><span data-stu-id="ed2ad-142">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="ed2ad-143">Тип данных Integer</span><span class="sxs-lookup"><span data-stu-id="ed2ad-143">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="ed2ad-144">Тип данных Long</span><span class="sxs-lookup"><span data-stu-id="ed2ad-144">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="ed2ad-145">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="ed2ad-145">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
