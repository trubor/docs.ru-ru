---
description: 'Подробнее о: короткий тип данных (Visual Basic)'
title: Тип данных Short
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 8c6bee45355548b3a32d74d059159918b4009fbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792145"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="6b311-103">Короткий тип данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b311-103">Short data type (Visual Basic)</span></span>

<span data-ttu-id="6b311-104">Содержит 16-битные (2-байтные) целые числа со знаком в диапазоне от-32 768 до 32 767.</span><span class="sxs-lookup"><span data-stu-id="6b311-104">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b311-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="6b311-105">Remarks</span></span>  

 <span data-ttu-id="6b311-106">Используйте `Short` тип данных для хранения целочисленных значений, не требующих полной ширины данных `Integer` .</span><span class="sxs-lookup"><span data-stu-id="6b311-106">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="6b311-107">В некоторых случаях среда CLR может `Short` объединять переменные и экономить потребление памяти.</span><span class="sxs-lookup"><span data-stu-id="6b311-107">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="6b311-108">Значение по умолчанию для типа `Short` — 0.</span><span class="sxs-lookup"><span data-stu-id="6b311-108">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="6b311-109">Присваивания литералов</span><span class="sxs-lookup"><span data-stu-id="6b311-109">Literal assignments</span></span>

<span data-ttu-id="6b311-110">Можно объявить и инициализировать `Short` переменную, назначив ей десятичный литерал, шестнадцатеричный литерал, Восьмеричный литерал или (начиная с Visual Basic 2017) двоичный литерал.</span><span class="sxs-lookup"><span data-stu-id="6b311-110">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="6b311-111">Если целочисленный литерал выходит за пределы диапазона `Short` (то есть, если он меньше <xref:System.Int16.MinValue?displayProperty=nameWithType> или больше <xref:System.Int16.MaxValue?displayProperty=nameWithType>), возникает ошибка компиляции.</span><span class="sxs-lookup"><span data-stu-id="6b311-111">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="6b311-112">В следующем примере целые числа, равные 1 034, представленные в виде десятичных, шестнадцатеричных и двоичных литералов, неявно преобразуются из [типа Integer](integer-data-type.md) в `Short` значения.</span><span class="sxs-lookup"><span data-stu-id="6b311-112">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="6b311-113">Используйте префикс `&h` или `&H` , чтобы обозначить шестнадцатеричный литерал, префикс `&b` или `&B` обозначить двоичный литерал, а также префикс `&o` или `&O` обозначить Восьмеричный литерал.</span><span class="sxs-lookup"><span data-stu-id="6b311-113">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="6b311-114">У десятичных литералов префиксов нет.</span><span class="sxs-lookup"><span data-stu-id="6b311-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="6b311-115">Начиная с Visual Basic 2017, можно также использовать символ подчеркивания () в `_` качестве разделителя цифр, чтобы улучшить удобочитаемость, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6b311-115">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="6b311-116">Начиная с Visual Basic 15,5, можно также использовать символ подчеркивания () в `_` качестве начального разделителя между префиксом и шестнадцатеричными, двоичными или восьмеричными цифрами.</span><span class="sxs-lookup"><span data-stu-id="6b311-116">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="6b311-117">Пример:</span><span class="sxs-lookup"><span data-stu-id="6b311-117">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="6b311-118">Числовые литералы также могут включать `S` [символ типа](../../programming-guide/language-features/data-types/type-characters.md) для обозначения `Short` типа данных, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6b311-118">Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="6b311-119">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="6b311-119">Programming tips</span></span>

- <span data-ttu-id="6b311-120">**Расширяющие.**</span><span class="sxs-lookup"><span data-stu-id="6b311-120">**Widening.**</span></span> <span data-ttu-id="6b311-121">`Short`Тип данных расширяется до `Integer` ,, `Long` , `Decimal` `Single` или `Double` .</span><span class="sxs-lookup"><span data-stu-id="6b311-121">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="6b311-122">Это означает, что тип `Short` можно преобразовать в любой из этих типов без возникновения ошибки <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b311-122">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="6b311-123">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="6b311-123">**Type Characters.**</span></span> <span data-ttu-id="6b311-124">При добавлении к литералу символа типа литерала `S` производится принудительное приведение литерала к типу данных `Short`.</span><span class="sxs-lookup"><span data-stu-id="6b311-124">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="6b311-125">`Short` не имеет символа типа идентификатора.</span><span class="sxs-lookup"><span data-stu-id="6b311-125">`Short` has no identifier type character.</span></span>  
  
- <span data-ttu-id="6b311-126">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="6b311-126">**Framework Type.**</span></span> <span data-ttu-id="6b311-127">В .NET Framework данный тип соответствует структуре <xref:System.Int16?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6b311-127">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b311-128">См. также</span><span class="sxs-lookup"><span data-stu-id="6b311-128">See also</span></span>

- <xref:System.Int16?displayProperty=nameWithType>
- [<span data-ttu-id="6b311-129">Типы данных</span><span class="sxs-lookup"><span data-stu-id="6b311-129">Data Types</span></span>](index.md)
- [<span data-ttu-id="6b311-130">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="6b311-130">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="6b311-131">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="6b311-131">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="6b311-132">Тип данных Integer</span><span class="sxs-lookup"><span data-stu-id="6b311-132">Integer Data Type</span></span>](integer-data-type.md)
- [<span data-ttu-id="6b311-133">Тип данных Long</span><span class="sxs-lookup"><span data-stu-id="6b311-133">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="6b311-134">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="6b311-134">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
