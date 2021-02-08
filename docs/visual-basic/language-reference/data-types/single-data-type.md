---
description: 'Дополнительные сведения: один тип данных (Visual Basic)'
title: Тип данных Single
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: f30e21d3b2d2960a040609a9422ec71cc029f5be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792132"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="2ff78-103">Тип данных Single (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ff78-103">Single Data Type (Visual Basic)</span></span>

<span data-ttu-id="2ff78-104">Содержит подписанные 32-разрядные (4-байтовые) числа с плавающей запятой с одиночной точностью в диапазоне от-4028235E E + 38 до-1.401298 E-45 для отрицательных значений и от 1.401298 E-45 до 4028235E E + 38 для положительных значений.</span><span class="sxs-lookup"><span data-stu-id="2ff78-104">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="2ff78-105">Числа с одиночной точностью хранят приближение вещественного числа.</span><span class="sxs-lookup"><span data-stu-id="2ff78-105">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ff78-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="2ff78-106">Remarks</span></span>  

 <span data-ttu-id="2ff78-107">Используйте `Single` тип данных для хранения значений с плавающей запятой, не требующих полной ширины данных `Double` .</span><span class="sxs-lookup"><span data-stu-id="2ff78-107">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="2ff78-108">В некоторых случаях среда CLR может `Single` объединять переменные и экономить потребление памяти.</span><span class="sxs-lookup"><span data-stu-id="2ff78-108">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="2ff78-109">Значение по умолчанию для типа `Single` — 0.</span><span class="sxs-lookup"><span data-stu-id="2ff78-109">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="2ff78-110">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="2ff78-110">Programming Tips</span></span>  
  
- <span data-ttu-id="2ff78-111">**Обеспечивают.**</span><span class="sxs-lookup"><span data-stu-id="2ff78-111">**Precision.**</span></span> <span data-ttu-id="2ff78-112">При работе с числами с плавающей запятой следует помнить, что они не всегда имеют точное представление в памяти.</span><span class="sxs-lookup"><span data-stu-id="2ff78-112">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="2ff78-113">Это может привести к непредвиденным результатам некоторых операций, таких как сравнение значений и `Mod` оператор.</span><span class="sxs-lookup"><span data-stu-id="2ff78-113">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="2ff78-114">Дополнительные сведения см. в разделе [Устранение неполадок типов данных](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="2ff78-114">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
- <span data-ttu-id="2ff78-115">**Расширяющие.**</span><span class="sxs-lookup"><span data-stu-id="2ff78-115">**Widening.**</span></span> <span data-ttu-id="2ff78-116">`Single`Тип данных расширяется до `Double` .</span><span class="sxs-lookup"><span data-stu-id="2ff78-116">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="2ff78-117">Это означает, что можно преобразовать `Single` в `Double` без возникновения <xref:System.OverflowException?displayProperty=nameWithType> ошибки.</span><span class="sxs-lookup"><span data-stu-id="2ff78-117">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="2ff78-118">**Нули в конце.**</span><span class="sxs-lookup"><span data-stu-id="2ff78-118">**Trailing Zeros.**</span></span> <span data-ttu-id="2ff78-119">Типы данных с плавающей запятой не имеют внутреннего представления конечных знаков 0.</span><span class="sxs-lookup"><span data-stu-id="2ff78-119">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="2ff78-120">Например, они не различаются между 4,2000 и 4,2.</span><span class="sxs-lookup"><span data-stu-id="2ff78-120">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="2ff78-121">Следовательно, замыкающие символы (0) не отображаются при отображении или печати значений с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="2ff78-121">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
- <span data-ttu-id="2ff78-122">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="2ff78-122">**Type Characters.**</span></span> <span data-ttu-id="2ff78-123">При добавлении к литералу символа типа литерала `F` производится принудительное приведение литерала к типу данных `Single`.</span><span class="sxs-lookup"><span data-stu-id="2ff78-123">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="2ff78-124">При добавлении символа идентификатора типа `!` к любому идентификатору производится принудительное приведение этого идентификатора к типу `Single`.</span><span class="sxs-lookup"><span data-stu-id="2ff78-124">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
- <span data-ttu-id="2ff78-125">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="2ff78-125">**Framework Type.**</span></span> <span data-ttu-id="2ff78-126">В .NET Framework данный тип соответствует структуре <xref:System.Single?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2ff78-126">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff78-127">См. также</span><span class="sxs-lookup"><span data-stu-id="2ff78-127">See also</span></span>

- <xref:System.Single?displayProperty=nameWithType>
- [<span data-ttu-id="2ff78-128">Типы данных</span><span class="sxs-lookup"><span data-stu-id="2ff78-128">Data Types</span></span>](index.md)
- [<span data-ttu-id="2ff78-129">Тип данных Decimal</span><span class="sxs-lookup"><span data-stu-id="2ff78-129">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="2ff78-130">Тип данных Double</span><span class="sxs-lookup"><span data-stu-id="2ff78-130">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="2ff78-131">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="2ff78-131">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="2ff78-132">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="2ff78-132">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="2ff78-133">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="2ff78-133">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="2ff78-134">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="2ff78-134">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
