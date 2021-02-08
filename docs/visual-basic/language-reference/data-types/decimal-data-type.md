---
description: Дополнительные сведения о типе данных Decimal (Visual Basic)
title: Тип данных Decimal
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: 5806041e7737b8fe0f1c7ffa63f6cbadcbf92e42
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792236"
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="8bdbe-103">Тип данных Decimal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bdbe-103">Decimal Data Type (Visual Basic)</span></span>

<span data-ttu-id="8bdbe-104">Содержит 128-разрядные (16-байтные) значения со знаком, представляющие 96-разрядные (12-байтные) целые числа с переменной степенью, кратной 10.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-104">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="8bdbe-105">Коэффициент масштабирования определяет количество цифр справа от десятичной запятой. Он находится в диапазоне от 0 до 28.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-105">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="8bdbe-106">С масштабом 0 (без десятичных знаков) максимально возможное значение — +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E + 28).</span><span class="sxs-lookup"><span data-stu-id="8bdbe-106">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="8bdbe-107">С 28 десятичными разрядами максимальное значение — +/-7.9228162514264337593543950335, а наименьшее ненулевое значение — +/-0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="8bdbe-107">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>

## <a name="remarks"></a><span data-ttu-id="8bdbe-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="8bdbe-108">Remarks</span></span>

<span data-ttu-id="8bdbe-109">`Decimal`Тип данных предоставляет наибольшее количество значащих цифр для числа.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-109">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="8bdbe-110">Он поддерживает до 29 значащих цифр и может представлять значения, превышающие 7,9228 x 10 ^ 28.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-110">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="8bdbe-111">Он особенно подходит для вычислений, например финансовых, которые нуждаются в большом количестве цифр, но не могут допускать ошибки округления.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-111">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>

<span data-ttu-id="8bdbe-112">Значение по умолчанию для типа `Decimal` — 0.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-112">The default value of `Decimal` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="8bdbe-113">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="8bdbe-113">Programming Tips</span></span>

- <span data-ttu-id="8bdbe-114">**Обеспечивают.**</span><span class="sxs-lookup"><span data-stu-id="8bdbe-114">**Precision.**</span></span> <span data-ttu-id="8bdbe-115">`Decimal` не является типом данных с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-115">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="8bdbe-116">`Decimal`Структура содержит двоичное целочисленное значение, а также бит знака и целочисленный коэффициент масштабирования, указывающий, какая часть значения является десятичной дробью.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-116">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="8bdbe-117">По этой причине `Decimal` числа имеют более точное представление в памяти, чем типы с плавающей запятой ( `Single` и `Double` ).</span><span class="sxs-lookup"><span data-stu-id="8bdbe-117">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>

- <span data-ttu-id="8bdbe-118">**Производительность.**</span><span class="sxs-lookup"><span data-stu-id="8bdbe-118">**Performance.**</span></span> <span data-ttu-id="8bdbe-119">`Decimal`Тип данных является самым медленным из всех числовых типов.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-119">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="8bdbe-120">Перед выбором типа данных следует оценить важность точности в соответствии с производительностью.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-120">You should weigh the importance of precision against performance before choosing a data type.</span></span>

- <span data-ttu-id="8bdbe-121">**Расширяющие.**</span><span class="sxs-lookup"><span data-stu-id="8bdbe-121">**Widening.**</span></span> <span data-ttu-id="8bdbe-122">`Decimal`Тип данных расширяется до `Single` или `Double` .</span><span class="sxs-lookup"><span data-stu-id="8bdbe-122">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="8bdbe-123">Это означает, что можно преобразовать `Decimal` в любой из этих типов без возникновения <xref:System.OverflowException?displayProperty=nameWithType> ошибки.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-123">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="8bdbe-124">**Нули в конце.**</span><span class="sxs-lookup"><span data-stu-id="8bdbe-124">**Trailing Zeros.**</span></span> <span data-ttu-id="8bdbe-125">Visual Basic не сохраняет конечные нули в `Decimal` литерале.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-125">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="8bdbe-126">Однако `Decimal` переменная сохраняет все конечные нули, полученные при вычислении.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-126">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="8bdbe-127">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-127">The following example illustrates this.</span></span>

  ```vb
  Dim d1, d2, d3, d4 As Decimal
  d1 = 2.375D
  d2 = 1.625D
  d3 = d1 + d2
  d4 = 4.000D
  MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &
        ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))
  ```

  <span data-ttu-id="8bdbe-128">Выходные данные `MsgBox` в предыдущем примере имеют следующий вид:</span><span class="sxs-lookup"><span data-stu-id="8bdbe-128">The output of `MsgBox` in the preceding example is as follows:</span></span>

  ```console
  d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4
  ```

- <span data-ttu-id="8bdbe-129">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="8bdbe-129">**Type Characters.**</span></span> <span data-ttu-id="8bdbe-130">При добавлении к литералу символа типа литерала `D` производится принудительное приведение литерала к типу данных `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-130">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="8bdbe-131">При добавлении символа идентификатора типа `@` к любому идентификатору производится принудительное приведение этого идентификатора к типу `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-131">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>

- <span data-ttu-id="8bdbe-132">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="8bdbe-132">**Framework Type.**</span></span> <span data-ttu-id="8bdbe-133">В .NET Framework данный тип соответствует структуре <xref:System.Decimal?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-133">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>

## <a name="range"></a><span data-ttu-id="8bdbe-134">Диапазон</span><span class="sxs-lookup"><span data-stu-id="8bdbe-134">Range</span></span>

 <span data-ttu-id="8bdbe-135">Может потребоваться использовать `D` символ типа, чтобы присвоить большое значение `Decimal` переменной или константе.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-135">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="8bdbe-136">Это требование обусловлено тем, что компилятор интерпретирует литерал как `Long` , если символ типа литерала не соответствует литералу, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-136">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>

```vb
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.
```

<span data-ttu-id="8bdbe-137">Объявление для `bigDec1` не создает переполнение, так как присваиваемое ему значение попадает в диапазон для `Long` .</span><span class="sxs-lookup"><span data-stu-id="8bdbe-137">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="8bdbe-138">`Long`Значение может быть присвоено `Decimal` переменной.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-138">The `Long` value can be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="8bdbe-139">Объявление для `bigDec2` создает ошибку переполнения, так как присвоенное ей значение слишком велико для `Long` .</span><span class="sxs-lookup"><span data-stu-id="8bdbe-139">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="8bdbe-140">Поскольку числовой литерал не может быть интерпретирован как `Long` , он не может быть назначен `Decimal` переменной.</span><span class="sxs-lookup"><span data-stu-id="8bdbe-140">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>

<span data-ttu-id="8bdbe-141">Для `bigDec3` символ типа литерала `D` решает проблему, вызывая компилятору интерпретировать литерал как, `Decimal` а не как `Long` .</span><span class="sxs-lookup"><span data-stu-id="8bdbe-141">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>

## <a name="see-also"></a><span data-ttu-id="8bdbe-142">См. также</span><span class="sxs-lookup"><span data-stu-id="8bdbe-142">See also</span></span>

- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Decimal.%23ctor%2A>
- <xref:System.Math.Round%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8bdbe-143">Типы данных</span><span class="sxs-lookup"><span data-stu-id="8bdbe-143">Data Types</span></span>](index.md)
- [<span data-ttu-id="8bdbe-144">Тип данных Single</span><span class="sxs-lookup"><span data-stu-id="8bdbe-144">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="8bdbe-145">Тип данных Double</span><span class="sxs-lookup"><span data-stu-id="8bdbe-145">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="8bdbe-146">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="8bdbe-146">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="8bdbe-147">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="8bdbe-147">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="8bdbe-148">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="8bdbe-148">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
