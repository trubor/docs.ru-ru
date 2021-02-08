---
description: Дополнительные сведения о типе данных Integer (Visual Basic)
title: Тип данных Integer
ms.date: 01/31/2018
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
ms.openlocfilehash: 8c60bf19ecd44ca7c9972cbfeb4ee2197bcb137c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792210"
---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="8137c-103">Тип данных Integer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8137c-103">Integer data type (Visual Basic)</span></span>

<span data-ttu-id="8137c-104">Содержит 32-разрядные (4-байтовые) целые числа со знаком в диапазоне от -2 147 483 648 до 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="8137c-104">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8137c-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="8137c-105">Remarks</span></span>

 <span data-ttu-id="8137c-106">Тип данных `Integer` обеспечивает оптимальную производительность на 32-разрядных процессорах.</span><span class="sxs-lookup"><span data-stu-id="8137c-106">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="8137c-107">Другие целочисленные типы загружаются в память и сохраняются в памяти с более низкой скоростью.</span><span class="sxs-lookup"><span data-stu-id="8137c-107">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="8137c-108">Значение по умолчанию для типа `Integer` — 0.</span><span class="sxs-lookup"><span data-stu-id="8137c-108">The default value of `Integer` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="8137c-109">Присваивания литералов</span><span class="sxs-lookup"><span data-stu-id="8137c-109">Literal assignments</span></span>

<span data-ttu-id="8137c-110">Вы можете объявить и инициализировать `Integer` переменную, назначив ей десятичный литерал, шестнадцатеричный литерал, Восьмеричный литерал или (начиная с Visual Basic 2017) двоичный литерал.</span><span class="sxs-lookup"><span data-stu-id="8137c-110">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="8137c-111">Если целочисленный литерал выходит за пределы диапазона `Integer` (то есть, если он меньше <xref:System.Int32.MinValue?displayProperty=nameWithType> или больше <xref:System.Int32.MaxValue?displayProperty=nameWithType>), возникает ошибка компиляции.</span><span class="sxs-lookup"><span data-stu-id="8137c-111">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="8137c-112">В следующем примере целые числа, равные 90 946 и представленные в виде десятичного, шестнадцатеричного и двоичного литерала, назначаются значениям `Integer`.</span><span class="sxs-lookup"><span data-stu-id="8137c-112">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> <span data-ttu-id="8137c-113">Используйте префикс `&h` или `&H` , чтобы обозначить шестнадцатеричный литерал, префикс `&b` или `&B` обозначить двоичный литерал, а также префикс `&o` или `&O` обозначить Восьмеричный литерал.</span><span class="sxs-lookup"><span data-stu-id="8137c-113">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="8137c-114">У десятичных литералов префиксов нет.</span><span class="sxs-lookup"><span data-stu-id="8137c-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="8137c-115">Начиная с Visual Basic 2017, можно также использовать символ подчеркивания () в `_` качестве разделителя цифр, чтобы улучшить удобочитаемость, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="8137c-115">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

<span data-ttu-id="8137c-116">Начиная с Visual Basic 15,5, можно также использовать символ подчеркивания () в `_` качестве начального разделителя между префиксом и шестнадцатеричными, двоичными или восьмеричными цифрами.</span><span class="sxs-lookup"><span data-stu-id="8137c-116">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="8137c-117">Пример:</span><span class="sxs-lookup"><span data-stu-id="8137c-117">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="8137c-118">Числовые литералы также могут включать `I` [символ типа](../../programming-guide/language-features/data-types/type-characters.md) для обозначения `Integer` типа данных, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="8137c-118">Numeric literals can also include the `I` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span></span>

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a><span data-ttu-id="8137c-119">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="8137c-119">Programming tips</span></span>

- <span data-ttu-id="8137c-120">**Вопросы взаимодействия.**</span><span class="sxs-lookup"><span data-stu-id="8137c-120">**Interop Considerations.**</span></span> <span data-ttu-id="8137c-121">При взаимоработе с компонентами, которые не записываются для платформа .NET Framework, таких как автоматизация или COM-объекты, помните, что `Integer` в других средах ширина данных (16 бит) отличается.</span><span class="sxs-lookup"><span data-stu-id="8137c-121">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="8137c-122">При передаче 16-разрядного аргумента такому компоненту в новом коде Visual Basic следует объявить его как `Short`, а не как `Integer`.</span><span class="sxs-lookup"><span data-stu-id="8137c-122">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="8137c-123">**Расширяющие.**</span><span class="sxs-lookup"><span data-stu-id="8137c-123">**Widening.**</span></span> <span data-ttu-id="8137c-124">Тип данных `Integer` можно расширить до `Long`, `Decimal`, `Single` или `Double`.</span><span class="sxs-lookup"><span data-stu-id="8137c-124">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="8137c-125">Это означает, что тип `Integer` можно преобразовать в любой из этих типов без возникновения ошибки <xref:System.OverflowException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8137c-125">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="8137c-126">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="8137c-126">**Type Characters.**</span></span> <span data-ttu-id="8137c-127">При добавлении к литералу символа типа литерала `I` производится принудительное приведение литерала к типу данных `Integer`.</span><span class="sxs-lookup"><span data-stu-id="8137c-127">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="8137c-128">При добавлении символа идентификатора типа `%` к любому идентификатору производится принудительное приведение этого идентификатора к типу `Integer`.</span><span class="sxs-lookup"><span data-stu-id="8137c-128">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
- <span data-ttu-id="8137c-129">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="8137c-129">**Framework Type.**</span></span> <span data-ttu-id="8137c-130">В .NET Framework данный тип соответствует структуре <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8137c-130">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="8137c-131">Диапазон</span><span class="sxs-lookup"><span data-stu-id="8137c-131">Range</span></span>

<span data-ttu-id="8137c-132">При попытке присвоить целочисленной переменной значение, лежащее за пределами диапазона данного типа, возникает ошибка.</span><span class="sxs-lookup"><span data-stu-id="8137c-132">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="8137c-133">При попытке задать дробное значение оно округляется вверх или вниз до ближайшего целого значения.</span><span class="sxs-lookup"><span data-stu-id="8137c-133">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="8137c-134">Если число находится точно посередине между двумя целыми числами, значение округляется до ближайшего четного целого.</span><span class="sxs-lookup"><span data-stu-id="8137c-134">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="8137c-135">Такое поведение минимизирует ошибки округления, происходящие от постоянного округления среднего значения в одном направлении.</span><span class="sxs-lookup"><span data-stu-id="8137c-135">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="8137c-136">В следующем коде приведены примеры округления.</span><span class="sxs-lookup"><span data-stu-id="8137c-136">The following code shows examples of rounding.</span></span>  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a><span data-ttu-id="8137c-137">См. также</span><span class="sxs-lookup"><span data-stu-id="8137c-137">See also</span></span>

- <xref:System.Int32?displayProperty=nameWithType>
- [<span data-ttu-id="8137c-138">Типы данных</span><span class="sxs-lookup"><span data-stu-id="8137c-138">Data Types</span></span>](index.md)
- [<span data-ttu-id="8137c-139">Тип данных Long</span><span class="sxs-lookup"><span data-stu-id="8137c-139">Long Data Type</span></span>](long-data-type.md)
- [<span data-ttu-id="8137c-140">Тип данных Short</span><span class="sxs-lookup"><span data-stu-id="8137c-140">Short Data Type</span></span>](short-data-type.md)
- [<span data-ttu-id="8137c-141">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="8137c-141">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="8137c-142">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="8137c-142">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="8137c-143">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="8137c-143">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
