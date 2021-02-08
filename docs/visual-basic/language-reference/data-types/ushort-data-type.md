---
description: 'Дополнительные сведения: тип данных UShort (Visual Basic)'
title: Тип данных UShort
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 9c709e2110aef4281c348f697408044a191314c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774984"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="53ebd-103">Тип данных UShort (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53ebd-103">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="53ebd-104">Содержит 16-разрядные (2-байтные) целые числа без знака в диапазоне от 0 до 65 535.</span><span class="sxs-lookup"><span data-stu-id="53ebd-104">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53ebd-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="53ebd-105">Remarks</span></span>

 <span data-ttu-id="53ebd-106">Используйте `UShort` тип данных для хранения двоичных данных, размер которых слишком велик `Byte` .</span><span class="sxs-lookup"><span data-stu-id="53ebd-106">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="53ebd-107">Значение по умолчанию для типа `UShort` — 0.</span><span class="sxs-lookup"><span data-stu-id="53ebd-107">The default value of `UShort` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="53ebd-108">Присваивания литералов</span><span class="sxs-lookup"><span data-stu-id="53ebd-108">Literal assignments</span></span>

<span data-ttu-id="53ebd-109">Можно объявить и инициализировать `UShort` переменную, назначив ей десятичный литерал, шестнадцатеричный литерал, Восьмеричный литерал или (начиная с Visual Basic 2017) двоичный литерал.</span><span class="sxs-lookup"><span data-stu-id="53ebd-109">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="53ebd-110">Если целочисленный литерал выходит за пределы диапазона `UShort` (то есть, если он меньше <xref:System.UInt16.MinValue?displayProperty=nameWithType> или больше <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), возникает ошибка компиляции.</span><span class="sxs-lookup"><span data-stu-id="53ebd-110">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="53ebd-111">В следующем примере целые числа, равные 65 034, представленные в виде десятичных, шестнадцатеричных и двоичных литералов, присваиваются `UShort` значениям.</span><span class="sxs-lookup"><span data-stu-id="53ebd-111">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="53ebd-112">Используйте префикс `&h` или `&H` , чтобы обозначить шестнадцатеричный литерал, префикс `&b` или `&B` обозначить двоичный литерал, а также префикс `&o` или `&O` обозначить Восьмеричный литерал.</span><span class="sxs-lookup"><span data-stu-id="53ebd-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="53ebd-113">У десятичных литералов префиксов нет.</span><span class="sxs-lookup"><span data-stu-id="53ebd-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="53ebd-114">Начиная с Visual Basic 2017, можно также использовать символ подчеркивания () в `_` качестве разделителя цифр, чтобы улучшить удобочитаемость, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="53ebd-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="53ebd-115">Начиная с Visual Basic 15,5, можно также использовать символ подчеркивания () в `_` качестве начального разделителя между префиксом и шестнадцатеричными, двоичными или восьмеричными цифрами.</span><span class="sxs-lookup"><span data-stu-id="53ebd-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="53ebd-116">Пример:</span><span class="sxs-lookup"><span data-stu-id="53ebd-116">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="53ebd-117">Числовые литералы также могут включать `US` `us` [символ типа](../../programming-guide/language-features/data-types/type-characters.md) или для обозначения `UShort` типа данных, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="53ebd-117">Numeric literals can also include the `US` or `us` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="53ebd-118">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="53ebd-118">Programming tips</span></span>
  
- <span data-ttu-id="53ebd-119">**Отрицательные числа.**</span><span class="sxs-lookup"><span data-stu-id="53ebd-119">**Negative Numbers.**</span></span> <span data-ttu-id="53ebd-120">Так как `UShort` является неподписанным типом, он не может представлять отрицательное число.</span><span class="sxs-lookup"><span data-stu-id="53ebd-120">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="53ebd-121">При использовании оператора унарного минуса ( `-` ) в выражении, результатом которого является тип `UShort` , Visual Basic преобразует выражение в `Integer` First.</span><span class="sxs-lookup"><span data-stu-id="53ebd-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
- <span data-ttu-id="53ebd-122">**Соответствие CLS.**</span><span class="sxs-lookup"><span data-stu-id="53ebd-122">**CLS Compliance.**</span></span> <span data-ttu-id="53ebd-123">`UShort`Тип данных не является частью [спецификации](https://www.ecma-international.org/publications/standards/Ecma-335.htm) CLS, поэтому CLS-совместимый код не может использовать компонент, который его использует.</span><span class="sxs-lookup"><span data-stu-id="53ebd-123">The `UShort` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="53ebd-124">**Расширяющие.**</span><span class="sxs-lookup"><span data-stu-id="53ebd-124">**Widening.**</span></span> <span data-ttu-id="53ebd-125">`UShort`Тип данных расширяется до `Integer` ,,,,, `UInteger` `Long` `ULong` `Decimal` `Single` и `Double` .</span><span class="sxs-lookup"><span data-stu-id="53ebd-125">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="53ebd-126">Это означает, что можно преобразовать `UShort` в любой из этих типов без возникновения <xref:System.OverflowException?displayProperty=nameWithType> ошибки.</span><span class="sxs-lookup"><span data-stu-id="53ebd-126">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="53ebd-127">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="53ebd-127">**Type Characters.**</span></span> <span data-ttu-id="53ebd-128">При добавлении символов типа литерала `US` к литералу он применяет его к `UShort` типу данных.</span><span class="sxs-lookup"><span data-stu-id="53ebd-128">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="53ebd-129">`UShort` не имеет символа типа идентификатора.</span><span class="sxs-lookup"><span data-stu-id="53ebd-129">`UShort` has no identifier type character.</span></span>  
  
- <span data-ttu-id="53ebd-130">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="53ebd-130">**Framework Type.**</span></span> <span data-ttu-id="53ebd-131">В .NET Framework данный тип соответствует структуре <xref:System.UInt16?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53ebd-131">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53ebd-132">См. также</span><span class="sxs-lookup"><span data-stu-id="53ebd-132">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="53ebd-133">Типы данных</span><span class="sxs-lookup"><span data-stu-id="53ebd-133">Data Types</span></span>](index.md)
- [<span data-ttu-id="53ebd-134">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="53ebd-134">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="53ebd-135">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="53ebd-135">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="53ebd-136">Практическое руководство. Вызов функции Windows, принимающей значение беззнакового типа</span><span class="sxs-lookup"><span data-stu-id="53ebd-136">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="53ebd-137">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="53ebd-137">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
