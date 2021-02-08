---
description: Дополнительные сведения о типе данных Double (Visual Basic)
title: Тип данных Double
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: ae7b87b392038c67ba47e09d7ca995562bf06c1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792223"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="d0473-103">Тип данных Double (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0473-103">Double Data Type (Visual Basic)</span></span>

<span data-ttu-id="d0473-104">Содержит подписанные 64-разрядные (8-байтные) числа с плавающей запятой двойной точности, которые находятся в диапазоне от-1.79769313486231570 E + 308 до-4.94065645841246544 E-324 для отрицательных значений и от 4.94065645841246544 E-324 до 1.79769313486231570 E + 308 для положительных значений.</span><span class="sxs-lookup"><span data-stu-id="d0473-104">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="d0473-105">Числа двойной точности хранят приближение вещественного числа.</span><span class="sxs-lookup"><span data-stu-id="d0473-105">Double-precision numbers store an approximation of a real number.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0473-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="d0473-106">Remarks</span></span>

<span data-ttu-id="d0473-107">`Double`Тип данных предоставляет самые большие и наименьшие возможные величины числа.</span><span class="sxs-lookup"><span data-stu-id="d0473-107">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>

<span data-ttu-id="d0473-108">Значение по умолчанию для типа `Double` — 0.</span><span class="sxs-lookup"><span data-stu-id="d0473-108">The default value of `Double` is 0.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="d0473-109">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="d0473-109">Programming Tips</span></span>

- <span data-ttu-id="d0473-110">**Обеспечивают.**</span><span class="sxs-lookup"><span data-stu-id="d0473-110">**Precision.**</span></span> <span data-ttu-id="d0473-111">При работе с числами с плавающей запятой Помните, что они не всегда имеют точное представление в памяти.</span><span class="sxs-lookup"><span data-stu-id="d0473-111">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="d0473-112">Это может привести к непредвиденным результатам некоторых операций, таких как сравнение значений и `Mod` оператор.</span><span class="sxs-lookup"><span data-stu-id="d0473-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="d0473-113">Дополнительные сведения см. в разделе [Устранение неполадок типов данных](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="d0473-113">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

- <span data-ttu-id="d0473-114">**Нули в конце.**</span><span class="sxs-lookup"><span data-stu-id="d0473-114">**Trailing Zeros.**</span></span> <span data-ttu-id="d0473-115">Типы данных с плавающей запятой не имеют внутреннего представления конечных нулей.</span><span class="sxs-lookup"><span data-stu-id="d0473-115">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="d0473-116">Например, они не различаются между 4,2000 и 4,2.</span><span class="sxs-lookup"><span data-stu-id="d0473-116">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="d0473-117">Следовательно, конечные нули не отображаются при отображении или печати значений с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="d0473-117">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>

- <span data-ttu-id="d0473-118">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="d0473-118">**Type Characters.**</span></span> <span data-ttu-id="d0473-119">При добавлении к литералу символа типа литерала `R` производится принудительное приведение литерала к типу данных `Double`.</span><span class="sxs-lookup"><span data-stu-id="d0473-119">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="d0473-120">Например, если после целочисленного значения указывается `R` , значение изменяется на `Double` .</span><span class="sxs-lookup"><span data-stu-id="d0473-120">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>

  ```vb
  ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:
  Dim dub As Double = 4.0R
  ```

  <span data-ttu-id="d0473-121">При добавлении символа идентификатора типа `#` к любому идентификатору производится принудительное приведение этого идентификатора к типу `Double`.</span><span class="sxs-lookup"><span data-stu-id="d0473-121">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="d0473-122">В следующем примере переменная `num` типизирована как `Double` :</span><span class="sxs-lookup"><span data-stu-id="d0473-122">In the following example, the variable `num` is typed as a `Double`:</span></span>

  ```vb
  Dim num# = 3
  ```

- <span data-ttu-id="d0473-123">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="d0473-123">**Framework Type.**</span></span> <span data-ttu-id="d0473-124">В .NET Framework данный тип соответствует структуре <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d0473-124">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0473-125">См. также</span><span class="sxs-lookup"><span data-stu-id="d0473-125">See also</span></span>

- <xref:System.Double?displayProperty=nameWithType>
- [<span data-ttu-id="d0473-126">Типы данных</span><span class="sxs-lookup"><span data-stu-id="d0473-126">Data Types</span></span>](index.md)
- [<span data-ttu-id="d0473-127">Тип данных Decimal</span><span class="sxs-lookup"><span data-stu-id="d0473-127">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="d0473-128">Тип данных Single</span><span class="sxs-lookup"><span data-stu-id="d0473-128">Single Data Type</span></span>](single-data-type.md)
- [<span data-ttu-id="d0473-129">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="d0473-129">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="d0473-130">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="d0473-130">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="d0473-131">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="d0473-131">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="d0473-132">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="d0473-132">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="d0473-133">Символы типов</span><span class="sxs-lookup"><span data-stu-id="d0473-133">Type Characters</span></span>](../../programming-guide/language-features/data-types/type-characters.md)
