---
description: 'Дополнительные сведения: явные и неявные преобразования (Visual Basic)'
title: Явные и неявные преобразования
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
ms.openlocfilehash: 6a53c0998025cc8c19274c67d9dfe1c50a4f1373
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483954"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="29ef9-103">Явные и неявные преобразования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29ef9-103">Implicit and Explicit Conversions (Visual Basic)</span></span>

<span data-ttu-id="29ef9-104">*Неявное преобразование* не требует специального синтаксиса в исходном коде.</span><span class="sxs-lookup"><span data-stu-id="29ef9-104">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="29ef9-105">В следующем примере Visual Basic неявно преобразует значение `k` в значение с плавающей запятой одиночной точности перед его присвоением `q` .</span><span class="sxs-lookup"><span data-stu-id="29ef9-105">In the following example, Visual Basic implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>

```vb
Dim k As Integer
Dim q As Double
' Integer widens to Double, so you can do this with Option Strict On.
k = 432
q = k
```

<span data-ttu-id="29ef9-106">При *явном преобразовании* используется ключевое слово преобразования типа.</span><span class="sxs-lookup"><span data-stu-id="29ef9-106">An *explicit conversion* uses a type conversion keyword.</span></span> <span data-ttu-id="29ef9-107">Visual Basic предоставляет несколько таких ключевых слов, которые применяют выражение в круглых скобках к требуемому типу данных.</span><span class="sxs-lookup"><span data-stu-id="29ef9-107">Visual Basic provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="29ef9-108">Эти ключевые слова действуют как функции, но компилятор создает встроенный код, поэтому выполнение выполняется немного быстрее, чем с помощью вызова функции.</span><span class="sxs-lookup"><span data-stu-id="29ef9-108">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>

<span data-ttu-id="29ef9-109">В следующем расширении предыдущего примера `CInt` ключевое слово преобразует значение `q` обратно в целое число перед его присвоением `k` .</span><span class="sxs-lookup"><span data-stu-id="29ef9-109">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>

```vb
' q had been assigned the value 432 from k.
q = Math.Sqrt(q)
k = CInt(q)
' k now has the value 21 (rounded square root of 432).
```

## <a name="conversion-keywords"></a><span data-ttu-id="29ef9-110">Ключевые слова преобразований</span><span class="sxs-lookup"><span data-stu-id="29ef9-110">Conversion Keywords</span></span>

<span data-ttu-id="29ef9-111">В следующей таблице приведены доступные ключевые слова для преобразования.</span><span class="sxs-lookup"><span data-stu-id="29ef9-111">The following table shows the available conversion keywords.</span></span>

|<span data-ttu-id="29ef9-112">Ключевое слово преобразования типа</span><span class="sxs-lookup"><span data-stu-id="29ef9-112">Type conversion keyword</span></span>|<span data-ttu-id="29ef9-113">Преобразует выражение в тип данных</span><span class="sxs-lookup"><span data-stu-id="29ef9-113">Converts an expression to data type</span></span>|<span data-ttu-id="29ef9-114">Допустимые типы данных выражения для преобразования</span><span class="sxs-lookup"><span data-stu-id="29ef9-114">Allowable data types of expression to be converted</span></span>|
|---|---|---|
|`CBool`|[<span data-ttu-id="29ef9-115">Логический тип данных</span><span class="sxs-lookup"><span data-stu-id="29ef9-115">Boolean Data Type</span></span>](../../../language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="29ef9-116">Любой числовой тип (включая `Byte` , `SByte` и перечислимые типы), `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-116">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|
|`CByte`|[<span data-ttu-id="29ef9-117">Тип данных Byte</span><span class="sxs-lookup"><span data-stu-id="29ef9-117">Byte Data Type</span></span>](../../../language-reference/data-types/byte-data-type.md)|<span data-ttu-id="29ef9-118">Любой числовой тип (включая `SByte` перечислимые типы и), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-118">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CChar`|[<span data-ttu-id="29ef9-119">Тип данных Char</span><span class="sxs-lookup"><span data-stu-id="29ef9-119">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)|<span data-ttu-id="29ef9-120">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-120">`String`, `Object`</span></span>|
|`CDate`|[<span data-ttu-id="29ef9-121">Тип данных Date</span><span class="sxs-lookup"><span data-stu-id="29ef9-121">Date Data Type</span></span>](../../../language-reference/data-types/date-data-type.md)|<span data-ttu-id="29ef9-122">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-122">`String`, `Object`</span></span>|
|`CDbl`|[<span data-ttu-id="29ef9-123">Тип данных Double</span><span class="sxs-lookup"><span data-stu-id="29ef9-123">Double Data Type</span></span>](../../../language-reference/data-types/double-data-type.md)|<span data-ttu-id="29ef9-124">Любой числовой тип (включая `Byte` , `SByte` и перечислимые типы), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-124">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CDec`|[<span data-ttu-id="29ef9-125">Тип данных Decimal</span><span class="sxs-lookup"><span data-stu-id="29ef9-125">Decimal Data Type</span></span>](../../../language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="29ef9-126">Любой числовой тип (включая `Byte` , `SByte` и перечислимые типы), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-126">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CInt`|[<span data-ttu-id="29ef9-127">Тип данных Integer</span><span class="sxs-lookup"><span data-stu-id="29ef9-127">Integer Data Type</span></span>](../../../language-reference/data-types/integer-data-type.md)|<span data-ttu-id="29ef9-128">Любой числовой тип (включая `Byte` , `SByte` и перечислимые типы), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-128">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CLng`|[<span data-ttu-id="29ef9-129">Тип данных Long</span><span class="sxs-lookup"><span data-stu-id="29ef9-129">Long Data Type</span></span>](../../../language-reference/data-types/long-data-type.md)|<span data-ttu-id="29ef9-130">Любой числовой тип (включая `Byte` , `SByte` и перечислимые типы), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-130">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CObj`|[<span data-ttu-id="29ef9-131">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="29ef9-131">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)|<span data-ttu-id="29ef9-132">Любой тип</span><span class="sxs-lookup"><span data-stu-id="29ef9-132">Any type</span></span>|
|`CSByte`|[<span data-ttu-id="29ef9-133">Тип данных SByte</span><span class="sxs-lookup"><span data-stu-id="29ef9-133">SByte Data Type</span></span>](../../../language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="29ef9-134">Любой числовой тип (включая `Byte` перечислимые типы и), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-134">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CShort`|[<span data-ttu-id="29ef9-135">Тип данных Short</span><span class="sxs-lookup"><span data-stu-id="29ef9-135">Short Data Type</span></span>](../../../language-reference/data-types/short-data-type.md)|<span data-ttu-id="29ef9-136">Любой числовой тип (включая `Byte` , `SByte` и перечислимые типы), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-136">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CSng`|[<span data-ttu-id="29ef9-137">Тип данных Single</span><span class="sxs-lookup"><span data-stu-id="29ef9-137">Single Data Type</span></span>](../../../language-reference/data-types/single-data-type.md)|<span data-ttu-id="29ef9-138">Любой числовой тип (включая `Byte` , `SByte` и перечислимые типы), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-138">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CStr`|[<span data-ttu-id="29ef9-139">Тип данных String</span><span class="sxs-lookup"><span data-stu-id="29ef9-139">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)|<span data-ttu-id="29ef9-140">Любой числовой тип (включая `Byte` , `SByte` и перечислимые типы), `Boolean` , `Char` , `Char` массив, `Date` , `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-140">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|
|`CType`|<span data-ttu-id="29ef9-141">Тип, указанный после запятой ( `,` )</span><span class="sxs-lookup"><span data-stu-id="29ef9-141">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="29ef9-142">При преобразовании в *простейший тип данных* (включая массив простейшего типа) типы, допустимые для соответствующего ключевого слова преобразования</span><span class="sxs-lookup"><span data-stu-id="29ef9-142">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="29ef9-143">При преобразовании в *составной тип данных* интерфейсы, которые он реализует, и классы, от которых он наследует</span><span class="sxs-lookup"><span data-stu-id="29ef9-143">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="29ef9-144">При преобразовании в класс или структуру, в которой вы перегружены `CType` , этот класс или структура</span><span class="sxs-lookup"><span data-stu-id="29ef9-144">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|
|`CUInt`|[<span data-ttu-id="29ef9-145">Тип данных UInteger</span><span class="sxs-lookup"><span data-stu-id="29ef9-145">UInteger Data Type</span></span>](../../../language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="29ef9-146">Любой числовой тип (включая `Byte` , `SByte` и перечислимые типы), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-146">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CULng`|[<span data-ttu-id="29ef9-147">Тип данных ULong</span><span class="sxs-lookup"><span data-stu-id="29ef9-147">ULong Data Type</span></span>](../../../language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="29ef9-148">Любой числовой тип (включая `Byte` , `SByte` и перечислимые типы), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-148">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CUShort`|[<span data-ttu-id="29ef9-149">Тип данных UShort</span><span class="sxs-lookup"><span data-stu-id="29ef9-149">UShort Data Type</span></span>](../../../language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="29ef9-150">Любой числовой тип (включая `Byte` , `SByte` и перечислимые типы), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="29ef9-150">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|

## <a name="the-ctype-function"></a><span data-ttu-id="29ef9-151">Функция CType</span><span class="sxs-lookup"><span data-stu-id="29ef9-151">The CType Function</span></span>

<span data-ttu-id="29ef9-152">[Функция CType](../../../language-reference/functions/ctype-function.md) работает с двумя аргументами.</span><span class="sxs-lookup"><span data-stu-id="29ef9-152">The [CType Function](../../../language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="29ef9-153">Первое — выражение, которое необходимо преобразовать, а второе — целевой тип данных или класс объекта.</span><span class="sxs-lookup"><span data-stu-id="29ef9-153">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="29ef9-154">Обратите внимание, что первый аргумент должен быть выражением, а не типом.</span><span class="sxs-lookup"><span data-stu-id="29ef9-154">Note that the first argument must be an expression, not a type.</span></span>

<span data-ttu-id="29ef9-155">`CType` — Это *Встроенная функция*, то есть скомпилированный код выполняет преобразование, часто без создания вызова функции.</span><span class="sxs-lookup"><span data-stu-id="29ef9-155">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="29ef9-156">Это повышает производительность.</span><span class="sxs-lookup"><span data-stu-id="29ef9-156">This improves performance.</span></span>

<span data-ttu-id="29ef9-157">Сравнение `CType` с другими ключевыми словами преобразования типов см. в разделе Оператор [DirectCast](../../../language-reference/operators/directcast-operator.md) и [Оператор TryCast](../../../language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="29ef9-157">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../language-reference/operators/trycast-operator.md).</span></span>

### <a name="elementary-types"></a><span data-ttu-id="29ef9-158">Простые типы</span><span class="sxs-lookup"><span data-stu-id="29ef9-158">Elementary Types</span></span>

<span data-ttu-id="29ef9-159">В следующем примере показано использование функции `CType`.</span><span class="sxs-lookup"><span data-stu-id="29ef9-159">The following example demonstrates the use of `CType`.</span></span>

```vb
k = CType(q, Integer)
' The following statement coerces w to the specific object class Label.
f = CType(w, Label)
```

### <a name="composite-types"></a><span data-ttu-id="29ef9-160">Составные типы</span><span class="sxs-lookup"><span data-stu-id="29ef9-160">Composite Types</span></span>

<span data-ttu-id="29ef9-161">Можно использовать `CType` для преобразования значений в составные типы данных, а также в простые типы.</span><span class="sxs-lookup"><span data-stu-id="29ef9-161">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="29ef9-162">Его также можно использовать для приведения класса объекта к типу одного из его интерфейсов, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="29ef9-162">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>

```vb
' Assume class cZone implements interface iZone.
Dim h As Object
' The first argument to CType must be an expression, not a type.
Dim cZ As cZone
' The following statement coerces a cZone object to its interface iZone.
h = CType(cZ, iZone)
```

### <a name="array-types"></a><span data-ttu-id="29ef9-163">Типы массивов</span><span class="sxs-lookup"><span data-stu-id="29ef9-163">Array Types</span></span>

<span data-ttu-id="29ef9-164">`CType` также может преобразовывать типы данных массива, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="29ef9-164">`CType` can also convert array data types, as in the following example.</span></span>

```vb
Dim v() As classV
Dim obArray() As Object
' Assume some object array has been assigned to obArray.
' Check for run-time type compatibility.
If TypeOf obArray Is classV()
    ' obArray can be converted to classV.
    v = CType(obArray, classV())
End If
```

<span data-ttu-id="29ef9-165">Дополнительные сведения и пример см. в разделе [Преобразование массивов](array-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="29ef9-165">For more information and an example, see [Array Conversions](array-conversions.md).</span></span>

### <a name="types-defining-ctype"></a><span data-ttu-id="29ef9-166">Типы, определяющие CType</span><span class="sxs-lookup"><span data-stu-id="29ef9-166">Types Defining CType</span></span>

<span data-ttu-id="29ef9-167">Можно определить `CType` для класса или структуры, которые вы определили.</span><span class="sxs-lookup"><span data-stu-id="29ef9-167">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="29ef9-168">Это позволяет преобразовать значения в тип класса или структуры и из него.</span><span class="sxs-lookup"><span data-stu-id="29ef9-168">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="29ef9-169">Дополнительные сведения и пример см. в разделе [инструкции. Определение оператора преобразования](../procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="29ef9-169">For more information and an example, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>

> [!NOTE]
> <span data-ttu-id="29ef9-170">Значения, используемые с ключевым словом преобразования, должны быть допустимыми для целевого типа данных, иначе возникает ошибка.</span><span class="sxs-lookup"><span data-stu-id="29ef9-170">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="29ef9-171">Например, при попытке преобразовать в `Long` объект `Integer` значение `Long` должно находиться в пределах допустимого диапазона для `Integer` типа данных.</span><span class="sxs-lookup"><span data-stu-id="29ef9-171">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>

> [!CAUTION]
> <span data-ttu-id="29ef9-172">При указании `CType` преобразования из одного типа класса в другой происходит сбой во время выполнения, если исходный тип не является производным от целевого типа.</span><span class="sxs-lookup"><span data-stu-id="29ef9-172">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="29ef9-173">Такой сбой приводит к <xref:System.InvalidCastException> возникновению исключения.</span><span class="sxs-lookup"><span data-stu-id="29ef9-173">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>

<span data-ttu-id="29ef9-174">Однако если один из типов является определенной структурой или классом, и если вы определили `CType` в этой структуре или классе, то преобразование может быть выполнено успешно, если оно удовлетворяет требованиям `CType` .</span><span class="sxs-lookup"><span data-stu-id="29ef9-174">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="29ef9-175">См. раздел [как определить оператор преобразования](../procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="29ef9-175">See [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>

<span data-ttu-id="29ef9-176">Выполнение явного преобразования также называется *приведением* выражения к заданному типу данных или классу объекта.</span><span class="sxs-lookup"><span data-stu-id="29ef9-176">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>

## <a name="see-also"></a><span data-ttu-id="29ef9-177">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="29ef9-177">See also</span></span>

- [<span data-ttu-id="29ef9-178">Преобразование типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29ef9-178">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="29ef9-179">Преобразования значений между строковыми и другими типами</span><span class="sxs-lookup"><span data-stu-id="29ef9-179">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="29ef9-180">Практическое руководство. Преобразование объекта к другому типу в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29ef9-180">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="29ef9-181">Структуры</span><span class="sxs-lookup"><span data-stu-id="29ef9-181">Structures</span></span>](structures.md)
- [<span data-ttu-id="29ef9-182">Типы данных</span><span class="sxs-lookup"><span data-stu-id="29ef9-182">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="29ef9-183">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="29ef9-183">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="29ef9-184">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="29ef9-184">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
