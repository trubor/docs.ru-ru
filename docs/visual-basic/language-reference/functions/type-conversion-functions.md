---
description: 'Дополнительные сведения: функции преобразования типов (Visual Basic)'
title: Type Conversion Functions
ms.date: 10/24/2018
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: c2e701b522bbeb32f4f6f448acd78e09b0616f46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731088"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="ff313-103">Функции преобразования типов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff313-103">Type Conversion Functions (Visual Basic)</span></span>

<span data-ttu-id="ff313-104">Эти функции компилируются встроенным, то есть код преобразования является частью кода, который вычисляет выражение.</span><span class="sxs-lookup"><span data-stu-id="ff313-104">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="ff313-105">Иногда нет вызова процедуры для выполнения преобразования, что повышает производительность.</span><span class="sxs-lookup"><span data-stu-id="ff313-105">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="ff313-106">Каждая функция приводит выражение к определенному типу данных.</span><span class="sxs-lookup"><span data-stu-id="ff313-106">Each function coerces an expression to a specific data type.</span></span>

## <a name="syntax"></a><span data-ttu-id="ff313-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ff313-107">Syntax</span></span>

```vb
CBool(expression)
CByte(expression)
CChar(expression)
CDate(expression)
CDbl(expression)
CDec(expression)
CInt(expression)
CLng(expression)
CObj(expression)
CSByte(expression)
CShort(expression)
CSng(expression)
CStr(expression)
CUInt(expression)
CULng(expression)
CUShort(expression)
```

## <a name="part"></a><span data-ttu-id="ff313-108">Отделение</span><span class="sxs-lookup"><span data-stu-id="ff313-108">Part</span></span>

`expression`  
<span data-ttu-id="ff313-109">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="ff313-109">Required.</span></span> <span data-ttu-id="ff313-110">Любое выражение исходного типа данных.</span><span class="sxs-lookup"><span data-stu-id="ff313-110">Any expression of the source data type.</span></span>

## <a name="return-value-data-type"></a><span data-ttu-id="ff313-111">Тип данных возвращаемого значения</span><span class="sxs-lookup"><span data-stu-id="ff313-111">Return Value Data Type</span></span>

<span data-ttu-id="ff313-112">Имя функции определяет тип данных возвращаемого значения, как показано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="ff313-112">The function name determines the data type of the value it returns, as shown in the following table.</span></span>

|<span data-ttu-id="ff313-113">Имя функции</span><span class="sxs-lookup"><span data-stu-id="ff313-113">Function name</span></span>|<span data-ttu-id="ff313-114">Тип возвращаемых данных</span><span class="sxs-lookup"><span data-stu-id="ff313-114">Return data type</span></span>|<span data-ttu-id="ff313-115">Диапазон для `expression` аргумента</span><span class="sxs-lookup"><span data-stu-id="ff313-115">Range for `expression` argument</span></span>|
|-------------------|----------------------|-------------------------------------|
|`CBool`|[<span data-ttu-id="ff313-116">Логический тип данных</span><span class="sxs-lookup"><span data-stu-id="ff313-116">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)|<span data-ttu-id="ff313-117">Любое допустимое `Char` или `String` числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="ff313-117">Any valid `Char` or `String` or numeric expression.</span></span>|
|`CByte`|[<span data-ttu-id="ff313-118">Тип данных Byte</span><span class="sxs-lookup"><span data-stu-id="ff313-118">Byte Data Type</span></span>](../data-types/byte-data-type.md)|<span data-ttu-id="ff313-119"><xref:System.Byte.MinValue?displayProperty=nameWithType> (от 0) до <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (без знака); дробные части округляются.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="ff313-119"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="ff313-120">Начиная с Visual Basic 15,8 Visual Basic оптимизирует производительность преобразования с плавающей запятой в байтовую `CByte` функцию. Дополнительные сведения см. в разделе ["Примечания"](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="ff313-120">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="ff313-121">Пример см. в разделе пример для функции [CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="ff313-121">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CChar`|[<span data-ttu-id="ff313-122">Тип данных Char</span><span class="sxs-lookup"><span data-stu-id="ff313-122">Char Data Type</span></span>](../data-types/char-data-type.md)|<span data-ttu-id="ff313-123">Любое допустимое `Char` `String` выражение или; преобразуется только первый символ `String` ; значение может быть от 0 до 65535 (без знака).</span><span class="sxs-lookup"><span data-stu-id="ff313-123">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|
|`CDate`|[<span data-ttu-id="ff313-124">Тип данных Date</span><span class="sxs-lookup"><span data-stu-id="ff313-124">Date Data Type</span></span>](../data-types/date-data-type.md)|<span data-ttu-id="ff313-125">Любое допустимое представление даты и времени.</span><span class="sxs-lookup"><span data-stu-id="ff313-125">Any valid representation of a date and time.</span></span>|
|`CDbl`|[<span data-ttu-id="ff313-126">Тип данных Double</span><span class="sxs-lookup"><span data-stu-id="ff313-126">Double Data Type</span></span>](../data-types/double-data-type.md)|<span data-ttu-id="ff313-127">-1.79769313486231570 e + 308 до-4.94065645841246544 E-324 для отрицательных значений; 4.94065645841246544 e-324 до 1.79769313486231570 E + 308 для положительных значений.</span><span class="sxs-lookup"><span data-stu-id="ff313-127">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|
|`CDec`|[<span data-ttu-id="ff313-128">Тип данных Decimal</span><span class="sxs-lookup"><span data-stu-id="ff313-128">Decimal Data Type</span></span>](../data-types/decimal-data-type.md)|<span data-ttu-id="ff313-129">+/-79,228,162,514,264,337,593,543,950,335 для чисел с нулевым масштабом, то есть чисел без десятичных разрядов.</span><span class="sxs-lookup"><span data-stu-id="ff313-129">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="ff313-130">Для чисел с 28 десятичными разрядами диапазоном является +/-7.9228162514264337593543950335.</span><span class="sxs-lookup"><span data-stu-id="ff313-130">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="ff313-131">Наименьшее возможное ненулевое число — 0,0000000000000000000000000001 (+/-1E-28).</span><span class="sxs-lookup"><span data-stu-id="ff313-131">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|
|`CInt`|[<span data-ttu-id="ff313-132">Тип данных Integer</span><span class="sxs-lookup"><span data-stu-id="ff313-132">Integer Data Type</span></span>](../data-types/integer-data-type.md)|<span data-ttu-id="ff313-133"><xref:System.Int32.MinValue?displayProperty=nameWithType> (от-2 147 483 648) до <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2 147 483 647); дробные части округляются.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="ff313-133"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="ff313-134">Начиная с Visual Basic 15,8 Visual Basic оптимизирует производительность преобразования с плавающей запятой в целое с помощью `CInt` функции. Дополнительные сведения см. в разделе ["Примечания](#remarks) ".</span><span class="sxs-lookup"><span data-stu-id="ff313-134">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="ff313-135">Пример см. в разделе пример для функции [CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="ff313-135">See the [CInt Example](#cint-example) section for an example.</span></span> |
|`CLng`|[<span data-ttu-id="ff313-136">Тип данных Long</span><span class="sxs-lookup"><span data-stu-id="ff313-136">Long Data Type</span></span>](../data-types/long-data-type.md)|<span data-ttu-id="ff313-137"><xref:System.Int64.MinValue?displayProperty=nameWithType> (от-9223372036854775808) до <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9 223 372 036 854 775 807); дробные части округляются.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="ff313-137"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="ff313-138">Начиная с Visual Basic 15,8 Visual Basic оптимизирует производительность преобразования с плавающей запятой в 64-разрядное целое число с помощью `CLng` функции; Дополнительные сведения см. в разделе ["Примечания"](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="ff313-138">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="ff313-139">Пример см. в разделе пример для функции [CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="ff313-139">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CObj`|[<span data-ttu-id="ff313-140">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="ff313-140">Object Data Type</span></span>](../data-types/object-data-type.md)|<span data-ttu-id="ff313-141">Любое допустимое выражение.</span><span class="sxs-lookup"><span data-stu-id="ff313-141">Any valid expression.</span></span>|
|`CSByte`|[<span data-ttu-id="ff313-142">Тип данных SByte</span><span class="sxs-lookup"><span data-stu-id="ff313-142">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)|<span data-ttu-id="ff313-143"><xref:System.SByte.MinValue?displayProperty=nameWithType> (от-128) до <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); дробные части округляются.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="ff313-143"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="ff313-144">Начиная с Visual Basic 15,8, Visual Basic оптимизирует производительность преобразования байтов с плавающей запятой в функцию с помощью `CSByte` функции. Дополнительные сведения см. в разделе ["Примечания"](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="ff313-144">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="ff313-145">Пример см. в разделе пример для функции [CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="ff313-145">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CShort`|[<span data-ttu-id="ff313-146">Тип данных Short</span><span class="sxs-lookup"><span data-stu-id="ff313-146">Short Data Type</span></span>](../data-types/short-data-type.md)|<span data-ttu-id="ff313-147"><xref:System.Int16.MinValue?displayProperty=nameWithType> (от-32 768) до <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32 767); дробные части округляются.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="ff313-147"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="ff313-148">Начиная с Visual Basic 15,8 Visual Basic оптимизирует производительность преобразования с плавающей запятой в 16-разрядное целое с помощью `CShort` функции. Дополнительные сведения см. в разделе ["Примечания"](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="ff313-148">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="ff313-149">Пример см. в разделе пример для функции [CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="ff313-149">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CSng`|[<span data-ttu-id="ff313-150">Тип данных Single</span><span class="sxs-lookup"><span data-stu-id="ff313-150">Single Data Type</span></span>](../data-types/single-data-type.md)|<span data-ttu-id="ff313-151">-3.402823 e + 38 – 1.401298 E-45 для отрицательных значений; 1.401298 e-45 до 3.402823 E + 38 для положительных значений.</span><span class="sxs-lookup"><span data-stu-id="ff313-151">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|
|`CStr`|[<span data-ttu-id="ff313-152">Тип данных String</span><span class="sxs-lookup"><span data-stu-id="ff313-152">String Data Type</span></span>](../data-types/string-data-type.md)|<span data-ttu-id="ff313-153">Для `CStr` зависит от `expression` аргумента.</span><span class="sxs-lookup"><span data-stu-id="ff313-153">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="ff313-154">См. раздел [возвращаемые значения для функции CStr](return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="ff313-154">See [Return Values for the CStr Function](return-values-for-the-cstr-function.md).</span></span>|
|`CUInt`|[<span data-ttu-id="ff313-155">Тип данных UInteger</span><span class="sxs-lookup"><span data-stu-id="ff313-155">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)|<span data-ttu-id="ff313-156"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (от 0) до <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4 294 967 295) (без знака); дробные части округляются.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="ff313-156"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="ff313-157">Начиная с Visual Basic 15,8 Visual Basic оптимизирует производительность преобразования с плавающей запятой в целое число без знака с помощью `CUInt` функции. Дополнительные сведения см. в разделе ["Примечания"](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="ff313-157">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="ff313-158">Пример см. в разделе пример для функции [CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="ff313-158">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CULng`|[<span data-ttu-id="ff313-159">Тип данных ULong</span><span class="sxs-lookup"><span data-stu-id="ff313-159">ULong Data Type</span></span>](../data-types/ulong-data-type.md)|<span data-ttu-id="ff313-160"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (от 0) до <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615) (без знака); дробные части округляются.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="ff313-160"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="ff313-161">Начиная с Visual Basic 15,8, Visual Basic оптимизирует производительность преобразования с плавающей запятой в функцию длинного целого числа без знака с помощью `CULng` функции. Дополнительные сведения см. в разделе ["Примечания"](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="ff313-161">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="ff313-162">Пример см. в разделе пример для функции [CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="ff313-162">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CUShort`|[<span data-ttu-id="ff313-163">Тип данных UShort</span><span class="sxs-lookup"><span data-stu-id="ff313-163">UShort Data Type</span></span>](../data-types/ushort-data-type.md)|<span data-ttu-id="ff313-164"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (от 0) до <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65 535) (без знака); дробные части округляются.<sup> 1</sup></span><span class="sxs-lookup"><span data-stu-id="ff313-164"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="ff313-165">Начиная с Visual Basic 15,8, Visual Basic оптимизирует производительность преобразования 16-разрядного целого числа без знака с плавающей запятой в `CUShort` функцию. Дополнительные сведения см. в разделе ["Примечания"](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="ff313-165">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="ff313-166">Пример см. в разделе пример для функции [CInt](#cint-example) .</span><span class="sxs-lookup"><span data-stu-id="ff313-166">See the [CInt Example](#cint-example) section for an example.</span></span>|

<span data-ttu-id="ff313-167"><sup>1</sup> дробная часть может подвергаться специальному типу округления, называемому *банковским округлением*.</span><span class="sxs-lookup"><span data-stu-id="ff313-167"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="ff313-168">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="ff313-168">See "Remarks" for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff313-169">Remarks</span><span class="sxs-lookup"><span data-stu-id="ff313-169">Remarks</span></span>

<span data-ttu-id="ff313-170">Как правило, следует использовать функции преобразования типа Visual Basic в качестве предпочтений для методов платформа .NET Framework, таких как `ToString()` , в <xref:System.Convert> классе или в отдельной структуре типа или классе.</span><span class="sxs-lookup"><span data-stu-id="ff313-170">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="ff313-171">Функции Visual Basic предназначены для оптимального взаимодействия с Visual Basicным кодом, а также для сокращения исходного кода и упрощения его чтения.</span><span class="sxs-lookup"><span data-stu-id="ff313-171">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="ff313-172">Кроме того, методы преобразования платформа .NET Framework не всегда дают те же результаты, что и функции Visual Basic, например при преобразовании `Boolean` в `Integer` .</span><span class="sxs-lookup"><span data-stu-id="ff313-172">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="ff313-173">Дополнительные сведения см. в разделе [Устранение неполадок типов данных](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="ff313-173">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

<span data-ttu-id="ff313-174">Начиная с Visual Basic 15,8, производительность преобразования с плавающей запятой в целое число оптимизируется при передаче <xref:System.Single> значения или, <xref:System.Double> возвращаемого следующими методами, в одну из целочисленных функций преобразования (,,,,,, `CByte` `CShort` `CInt` `CLng` `CSByte` `CUShort` `CUInt` , `CULng` ):</span><span class="sxs-lookup"><span data-stu-id="ff313-174">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

<span data-ttu-id="ff313-175">Такая оптимизация позволяет выполнять код, выполняющий большое количество целочисленных преобразований, в два раза быстрее.</span><span class="sxs-lookup"><span data-stu-id="ff313-175">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="ff313-176">В следующем примере демонстрируются эти оптимизированные преобразования с плавающей запятой в целые числа:</span><span class="sxs-lookup"><span data-stu-id="ff313-176">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="ff313-177">Поведение</span><span class="sxs-lookup"><span data-stu-id="ff313-177">Behavior</span></span>

- <span data-ttu-id="ff313-178">**Приведение.**</span><span class="sxs-lookup"><span data-stu-id="ff313-178">**Coercion.**</span></span> <span data-ttu-id="ff313-179">В общем случае можно использовать функции преобразования типов данных для приведения результата операции к конкретному типу данных, а не по типу данных по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ff313-179">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="ff313-180">Например, используйте `CDec` для принудительного выполнения десятичных арифметических операций в случаях, когда обычно выполняется операция с одиночной точностью, двойной точностью или целочисленной.</span><span class="sxs-lookup"><span data-stu-id="ff313-180">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>

- <span data-ttu-id="ff313-181">**Неудачные преобразования.**</span><span class="sxs-lookup"><span data-stu-id="ff313-181">**Failed Conversions.**</span></span> <span data-ttu-id="ff313-182">Если `expression` переданный функции объект находится вне диапазона типа данных, в который она должна быть преобразована, <xref:System.OverflowException> возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="ff313-182">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>

- <span data-ttu-id="ff313-183">**Дробные части.**</span><span class="sxs-lookup"><span data-stu-id="ff313-183">**Fractional Parts.**</span></span> <span data-ttu-id="ff313-184">При преобразовании нецелочисленного значения в целочисленные функции целочисленного преобразования ( `CByte` , `CInt` ,,, `CLng` , `CSByte` `CShort` `CUInt` , `CULng` и `CUShort` ) удаляют дробную часть и округляют значение до ближайшего целого.</span><span class="sxs-lookup"><span data-stu-id="ff313-184">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>

     <span data-ttu-id="ff313-185">Если дробная часть равна точности 0,5, функции целочисленного преобразования округляют его до ближайшего четного целого числа.</span><span class="sxs-lookup"><span data-stu-id="ff313-185">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="ff313-186">Например, 0,5 округляется до 0, а 1,5 и 2,5 оба округляются в 2.</span><span class="sxs-lookup"><span data-stu-id="ff313-186">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="ff313-187">Иногда это называется *округлением банка* и предназначено для компенсации смещения, которое может накапливаться при одновременном добавлении многих таких чисел.</span><span class="sxs-lookup"><span data-stu-id="ff313-187">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>

     <span data-ttu-id="ff313-188">`CInt` и `CLng` отличаются от <xref:Microsoft.VisualBasic.Conversion.Int%2A> функций и <xref:Microsoft.VisualBasic.Conversion.Fix%2A> , которые усекаются, а не округляют дробную часть числа.</span><span class="sxs-lookup"><span data-stu-id="ff313-188">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="ff313-189">Кроме того, `Fix` и `Int` всегда возвращают значение того же типа данных, что и при передаче.</span><span class="sxs-lookup"><span data-stu-id="ff313-189">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>

- <span data-ttu-id="ff313-190">**Преобразования даты и времени.**</span><span class="sxs-lookup"><span data-stu-id="ff313-190">**Date/Time Conversions.**</span></span> <span data-ttu-id="ff313-191">Используйте <xref:Microsoft.VisualBasic.Information.IsDate%2A> функцию, чтобы определить, можно ли преобразовать значение в дату и время.</span><span class="sxs-lookup"><span data-stu-id="ff313-191">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="ff313-192">`CDate` распознает литералы даты и литералы времени, но не числовые значения.</span><span class="sxs-lookup"><span data-stu-id="ff313-192">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="ff313-193">Чтобы преобразовать значение Visual Basic 6,0 в `Date` `Date` значение в Visual Basic 2005 или более поздней версии, можно использовать <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> метод.</span><span class="sxs-lookup"><span data-stu-id="ff313-193">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="ff313-194">**Нейтральные значения даты и времени.**</span><span class="sxs-lookup"><span data-stu-id="ff313-194">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="ff313-195">[Тип данных Date](../data-types/date-data-type.md) всегда содержит сведения о дате и времени.</span><span class="sxs-lookup"><span data-stu-id="ff313-195">The [Date Data Type](../data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="ff313-196">В целях преобразования типов Visual Basic учитывает 1/1/0001 (1 января 1 года) как *нейтральное значение* для даты, а 00:00:00 (полночь) — как нейтральное значение времени.</span><span class="sxs-lookup"><span data-stu-id="ff313-196">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="ff313-197">При преобразовании `Date` значения в строку не `CStr` включает нейтральные значения в результирующую строку.</span><span class="sxs-lookup"><span data-stu-id="ff313-197">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="ff313-198">Например, если преобразовать `#January 1, 0001 9:30:00#` в строку, то результатом будет "9:30:00 AM"; сведения о дате подавляются.</span><span class="sxs-lookup"><span data-stu-id="ff313-198">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="ff313-199">Однако сведения о дате по-прежнему содержатся в исходном `Date` значении и могут быть восстановлены с помощью таких функций, как <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> Function.</span><span class="sxs-lookup"><span data-stu-id="ff313-199">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>

- <span data-ttu-id="ff313-200">**Чувствительность языка и региональных параметров.**</span><span class="sxs-lookup"><span data-stu-id="ff313-200">**Culture Sensitivity.**</span></span> <span data-ttu-id="ff313-201">Функции преобразования типов, включающие строки, выполняют преобразования в соответствии с текущими параметрами языка и региональных параметров для приложения.</span><span class="sxs-lookup"><span data-stu-id="ff313-201">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="ff313-202">Например, `CDate` распознает форматы даты в соответствии с настройками языкового стандарта системы.</span><span class="sxs-lookup"><span data-stu-id="ff313-202">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="ff313-203">Необходимо указать день, месяц и год в правильном порядке для вашего языкового стандарта, иначе Дата может интерпретироваться неправильно.</span><span class="sxs-lookup"><span data-stu-id="ff313-203">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="ff313-204">Длинный формат даты не распознается, если он содержит строку дня недели, например "среда".</span><span class="sxs-lookup"><span data-stu-id="ff313-204">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>

     <span data-ttu-id="ff313-205">Если необходимо преобразовать в строковое представление значения или из него в формате, отличном от указанного в Вашем языковом стандарте, то нельзя использовать функции преобразования типа Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ff313-205">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="ff313-206">Для этого используйте `ToString(IFormatProvider)` `Parse(String, IFormatProvider)` методы и типа этого значения.</span><span class="sxs-lookup"><span data-stu-id="ff313-206">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="ff313-207">Например, используйте <xref:System.Double.Parse%2A?displayProperty=nameWithType> при преобразовании строки в `Double` и используйте <xref:System.Double.ToString%2A?displayProperty=nameWithType> при преобразовании значения типа `Double` в строку.</span><span class="sxs-lookup"><span data-stu-id="ff313-207">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>

## <a name="ctype-function"></a><span data-ttu-id="ff313-208">CType Function</span><span class="sxs-lookup"><span data-stu-id="ff313-208">CType Function</span></span>

<span data-ttu-id="ff313-209">[Функция CType](ctype-function.md) принимает второй аргумент, `typename` и `expression` `typename` `typename` применяет к, где может быть любым типом данных, структурой, классом или интерфейсом, к которому существует допустимое преобразование.</span><span class="sxs-lookup"><span data-stu-id="ff313-209">The [CType Function](ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>

<span data-ttu-id="ff313-210">Сравнение `CType` с другими ключевыми словами преобразования типов см. в разделе Оператор [DirectCast](../operators/directcast-operator.md) и [Оператор TryCast](../operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="ff313-210">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../operators/directcast-operator.md) and [TryCast Operator](../operators/trycast-operator.md).</span></span>

## <a name="cbool-example"></a><span data-ttu-id="ff313-211">Пример CBool</span><span class="sxs-lookup"><span data-stu-id="ff313-211">CBool Example</span></span>

<span data-ttu-id="ff313-212">В следующем примере функция используется `CBool` для преобразования выражений в `Boolean` значения.</span><span class="sxs-lookup"><span data-stu-id="ff313-212">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="ff313-213">Если результат выражения равен ненулевому значению, `CBool` `True` функция возвращает; в противном случае возвращается значение `False` .</span><span class="sxs-lookup"><span data-stu-id="ff313-213">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>

[!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]

## <a name="cbyte-example"></a><span data-ttu-id="ff313-214">Пример CByte</span><span class="sxs-lookup"><span data-stu-id="ff313-214">CByte Example</span></span>

<span data-ttu-id="ff313-215">В следующем примере функция используется `CByte` для преобразования выражения в `Byte` .</span><span class="sxs-lookup"><span data-stu-id="ff313-215">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>

[!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]

## <a name="cchar-example"></a><span data-ttu-id="ff313-216">Пример CChar</span><span class="sxs-lookup"><span data-stu-id="ff313-216">CChar Example</span></span>

<span data-ttu-id="ff313-217">В следующем примере функция используется `CChar` для преобразования первого символа `String` выражения в `Char` тип.</span><span class="sxs-lookup"><span data-stu-id="ff313-217">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>

[!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]

<span data-ttu-id="ff313-218">Входной аргумент `CChar` должен иметь тип данных `Char` или `String` .</span><span class="sxs-lookup"><span data-stu-id="ff313-218">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="ff313-219">Нельзя использовать `CChar` для преобразования числа в символ, поскольку `CChar` не может принимать числовые типы данных.</span><span class="sxs-lookup"><span data-stu-id="ff313-219">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="ff313-220">В следующем примере получается число, представляющее кодовую точку (код символа), и преобразуется в соответствующий символ.</span><span class="sxs-lookup"><span data-stu-id="ff313-220">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="ff313-221">Она использует <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> функцию для получения строки разрядов, `CInt` преобразования строки в тип `Integer` и `ChrW` для преобразования числа в тип `Char` .</span><span class="sxs-lookup"><span data-stu-id="ff313-221">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>

[!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]

## <a name="cdate-example"></a><span data-ttu-id="ff313-222">Пример для CDate</span><span class="sxs-lookup"><span data-stu-id="ff313-222">CDate Example</span></span>

<span data-ttu-id="ff313-223">В следующем примере функция используется `CDate` для преобразования строк в `Date` значения.</span><span class="sxs-lookup"><span data-stu-id="ff313-223">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="ff313-224">Обычно не рекомендуется жестко кодировать даты и время в виде строк (как показано в этом примере).</span><span class="sxs-lookup"><span data-stu-id="ff313-224">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="ff313-225">Вместо этого используйте литералы даты и временные литералы, например #Feb 12, 1969 # и #4:45:23 PM #.</span><span class="sxs-lookup"><span data-stu-id="ff313-225">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>

[!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]

## <a name="cdbl-example"></a><span data-ttu-id="ff313-226">Пример с CDbl</span><span class="sxs-lookup"><span data-stu-id="ff313-226">CDbl Example</span></span>

[!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]

## <a name="cdec-example"></a><span data-ttu-id="ff313-227">Пример CDec</span><span class="sxs-lookup"><span data-stu-id="ff313-227">CDec Example</span></span>

<span data-ttu-id="ff313-228">В следующем примере функция используется `CDec` для преобразования числового значения в `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="ff313-228">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>

[!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]

## <a name="cint-example"></a><span data-ttu-id="ff313-229">Пример функции CInt</span><span class="sxs-lookup"><span data-stu-id="ff313-229">CInt Example</span></span>

<span data-ttu-id="ff313-230">В следующем примере функция используется `CInt` для преобразования значения в `Integer` .</span><span class="sxs-lookup"><span data-stu-id="ff313-230">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>

[!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]

## <a name="clng-example"></a><span data-ttu-id="ff313-231">Пример с CLng</span><span class="sxs-lookup"><span data-stu-id="ff313-231">CLng Example</span></span>

<span data-ttu-id="ff313-232">В следующем примере функция используется `CLng` для преобразования значений в `Long` .</span><span class="sxs-lookup"><span data-stu-id="ff313-232">The following example uses the `CLng` function to convert values to `Long`.</span></span>

[!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]

## <a name="cobj-example"></a><span data-ttu-id="ff313-233">Пример CObj</span><span class="sxs-lookup"><span data-stu-id="ff313-233">CObj Example</span></span>

<span data-ttu-id="ff313-234">В следующем примере функция используется `CObj` для преобразования числового значения в `Object` .</span><span class="sxs-lookup"><span data-stu-id="ff313-234">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="ff313-235">`Object`Сама переменная содержит только 4-байтовый указатель, указывающий на `Double` присвоенное ему значение.</span><span class="sxs-lookup"><span data-stu-id="ff313-235">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>

[!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]

## <a name="csbyte-example"></a><span data-ttu-id="ff313-236">Пример Ксбите</span><span class="sxs-lookup"><span data-stu-id="ff313-236">CSByte Example</span></span>

<span data-ttu-id="ff313-237">В следующем примере функция используется `CSByte` для преобразования числового значения в `SByte` .</span><span class="sxs-lookup"><span data-stu-id="ff313-237">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>

[!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]

## <a name="cshort-example"></a><span data-ttu-id="ff313-238">Пример CShort</span><span class="sxs-lookup"><span data-stu-id="ff313-238">CShort Example</span></span>

<span data-ttu-id="ff313-239">В следующем примере функция используется `CShort` для преобразования числового значения в `Short` .</span><span class="sxs-lookup"><span data-stu-id="ff313-239">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>

[!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]

## <a name="csng-example"></a><span data-ttu-id="ff313-240">Пример CSng</span><span class="sxs-lookup"><span data-stu-id="ff313-240">CSng Example</span></span>

<span data-ttu-id="ff313-241">В следующем примере функция используется `CSng` для преобразования значений в `Single` .</span><span class="sxs-lookup"><span data-stu-id="ff313-241">The following example uses the `CSng` function to convert values to `Single`.</span></span>

[!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]

## <a name="cstr-example"></a><span data-ttu-id="ff313-242">Пример функции CStr</span><span class="sxs-lookup"><span data-stu-id="ff313-242">CStr Example</span></span>

<span data-ttu-id="ff313-243">В следующем примере функция используется `CStr` для преобразования числового значения в `String` .</span><span class="sxs-lookup"><span data-stu-id="ff313-243">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>

[!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]

<span data-ttu-id="ff313-244">В следующем примере функция используется `CStr` для преобразования `Date` значений в `String` значения.</span><span class="sxs-lookup"><span data-stu-id="ff313-244">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>

[!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]

<span data-ttu-id="ff313-245">`CStr` всегда отображает `Date` значение в стандартном коротком формате для текущего языкового стандарта, например "6/15/2003 4:35:47 PM".</span><span class="sxs-lookup"><span data-stu-id="ff313-245">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="ff313-246">Однако `CStr` подавляет *нейтральные значения* 1/1/0001 для даты и 00:00:00 для времени.</span><span class="sxs-lookup"><span data-stu-id="ff313-246">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>

<span data-ttu-id="ff313-247">Дополнительные сведения о значениях, возвращаемых `CStr` , см. в разделе [возвращаемые значения функции CStr](return-values-for-the-cstr-function.md).</span><span class="sxs-lookup"><span data-stu-id="ff313-247">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](return-values-for-the-cstr-function.md).</span></span>

## <a name="cuint-example"></a><span data-ttu-id="ff313-248">Пример Куинт</span><span class="sxs-lookup"><span data-stu-id="ff313-248">CUInt Example</span></span>

<span data-ttu-id="ff313-249">В следующем примере функция используется `CUInt` для преобразования числового значения в `UInteger` .</span><span class="sxs-lookup"><span data-stu-id="ff313-249">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>

[!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]

## <a name="culng-example"></a><span data-ttu-id="ff313-250">Пример Кулнг</span><span class="sxs-lookup"><span data-stu-id="ff313-250">CULng Example</span></span>

<span data-ttu-id="ff313-251">В следующем примере функция используется `CULng` для преобразования числового значения в `ULong` .</span><span class="sxs-lookup"><span data-stu-id="ff313-251">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>

[!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]

## <a name="cushort-example"></a><span data-ttu-id="ff313-252">Пример Кушорт</span><span class="sxs-lookup"><span data-stu-id="ff313-252">CUShort Example</span></span>

<span data-ttu-id="ff313-253">В следующем примере функция используется `CUShort` для преобразования числового значения в `UShort` .</span><span class="sxs-lookup"><span data-stu-id="ff313-253">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>

[!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]

## <a name="see-also"></a><span data-ttu-id="ff313-254">См. также</span><span class="sxs-lookup"><span data-stu-id="ff313-254">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="ff313-255">Функции преобразования</span><span class="sxs-lookup"><span data-stu-id="ff313-255">Conversion Functions</span></span>](conversion-functions.md)
- [<span data-ttu-id="ff313-256">Преобразование типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff313-256">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
