---
description: 'Дополнительные сведения: символы типа (Visual Basic)'
title: Символы типов
ms.date: 01/31/2018
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
ms.openlocfilehash: d1afccb821d2ffb4dfabe3c38e0db4a7f902c164
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454551"
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="b5bab-103">Символы типов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5bab-103">Type characters (Visual Basic)</span></span>

<span data-ttu-id="b5bab-104">Помимо указания типа данных в операторе объявления, можно принудительно указать тип данных некоторых программных элементов с помощью *символа типа*.</span><span class="sxs-lookup"><span data-stu-id="b5bab-104">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="b5bab-105">Символ типа должен следовать непосредственно за элементом, не имеющим промежуточных символов любого вида.</span><span class="sxs-lookup"><span data-stu-id="b5bab-105">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="b5bab-106">Символ типа не является частью имени элемента.</span><span class="sxs-lookup"><span data-stu-id="b5bab-106">The type character is not part of the name of the element.</span></span> <span data-ttu-id="b5bab-107">На элемент, определенный с помощью символа типа, можно ссылаться без символа типа.</span><span class="sxs-lookup"><span data-stu-id="b5bab-107">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="b5bab-108">Символы типа идентификатора</span><span class="sxs-lookup"><span data-stu-id="b5bab-108">Identifier type characters</span></span>

<span data-ttu-id="b5bab-109">Visual Basic предоставляет набор *символов типа идентификатора* , которые можно использовать в объявлении для указания типа данных переменной или константы.</span><span class="sxs-lookup"><span data-stu-id="b5bab-109">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="b5bab-110">В следующей таблице приведены доступные символы типа идентификатора с примерами использования.</span><span class="sxs-lookup"><span data-stu-id="b5bab-110">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="b5bab-111">Символ типа идентификатора</span><span class="sxs-lookup"><span data-stu-id="b5bab-111">Identifier type character</span></span>|<span data-ttu-id="b5bab-112">Тип данных</span><span class="sxs-lookup"><span data-stu-id="b5bab-112">Data type</span></span>|<span data-ttu-id="b5bab-113">Пример</span><span class="sxs-lookup"><span data-stu-id="b5bab-113">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="b5bab-114">Для `Boolean` `Byte` типов данных,,,,,, `Char` , `Date` , `Object` `SByte` `Short` `UInteger` `ULong` , или `UShort` для любых составных типов данных, таких как массивы или структуры, символы типа Identifier не существуют.</span><span class="sxs-lookup"><span data-stu-id="b5bab-114">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="b5bab-115">В некоторых случаях можно добавить `$` символ в Visual Basic функцию, например `Left$` `Left` , вместо, чтобы получить возвращаемое значение типа `String` .</span><span class="sxs-lookup"><span data-stu-id="b5bab-115">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="b5bab-116">Во всех случаях символ типа идентификатора должен следовать непосредственно за именем идентификатора.</span><span class="sxs-lookup"><span data-stu-id="b5bab-116">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="b5bab-117">Символы типа литерала</span><span class="sxs-lookup"><span data-stu-id="b5bab-117">Literal type characters</span></span>

<span data-ttu-id="b5bab-118">*Литерал* — это текстовое представление конкретного значения типа данных.</span><span class="sxs-lookup"><span data-stu-id="b5bab-118">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="b5bab-119">Типы литералов по умолчанию</span><span class="sxs-lookup"><span data-stu-id="b5bab-119">Default literal types</span></span>

<span data-ttu-id="b5bab-120">Форма литерала в том виде, в котором она отображается в коде, обычно определяет его тип данных.</span><span class="sxs-lookup"><span data-stu-id="b5bab-120">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="b5bab-121">В следующей таблице показаны эти типы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b5bab-121">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="b5bab-122">Текстовая форма литерала</span><span class="sxs-lookup"><span data-stu-id="b5bab-122">Textual form of literal</span></span>|<span data-ttu-id="b5bab-123">Тип данных по умолчанию</span><span class="sxs-lookup"><span data-stu-id="b5bab-123">Default data type</span></span>|<span data-ttu-id="b5bab-124">Пример</span><span class="sxs-lookup"><span data-stu-id="b5bab-124">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="b5bab-125">Numeric, без дробной части</span><span class="sxs-lookup"><span data-stu-id="b5bab-125">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="b5bab-126">Numeric, без дробной части, слишком большой для `Integer`</span><span class="sxs-lookup"><span data-stu-id="b5bab-126">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="b5bab-127">Числовая, дробная часть</span><span class="sxs-lookup"><span data-stu-id="b5bab-127">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="b5bab-128">Заключено в двойные кавычки</span><span class="sxs-lookup"><span data-stu-id="b5bab-128">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="b5bab-129">Заключено в знаки решетки</span><span class="sxs-lookup"><span data-stu-id="b5bab-129">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="b5bab-130">Принудительные типы литералов</span><span class="sxs-lookup"><span data-stu-id="b5bab-130">Forced literal types</span></span>

<span data-ttu-id="b5bab-131">Visual Basic предоставляет набор *символов типа литерала*, который можно использовать для принудительного применения литерала к типу данных, отличному от того, который указывает его форма.</span><span class="sxs-lookup"><span data-stu-id="b5bab-131">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="b5bab-132">Это можно сделать, добавив символ в конец литерала.</span><span class="sxs-lookup"><span data-stu-id="b5bab-132">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="b5bab-133">В следующей таблице показаны доступные символы типа литерала с примерами использования.</span><span class="sxs-lookup"><span data-stu-id="b5bab-133">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="b5bab-134">Символ типа литерала</span><span class="sxs-lookup"><span data-stu-id="b5bab-134">Literal type character</span></span>|<span data-ttu-id="b5bab-135">Тип данных</span><span class="sxs-lookup"><span data-stu-id="b5bab-135">Data type</span></span>|<span data-ttu-id="b5bab-136">Пример</span><span class="sxs-lookup"><span data-stu-id="b5bab-136">Example</span></span>|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

<span data-ttu-id="b5bab-137">Для `Boolean` `Byte` типов данных,,,, `Date` `Object` `SByte` , или `String` для любых составных типов данных, таких как массивы или структуры, не существует символов типа литерала.</span><span class="sxs-lookup"><span data-stu-id="b5bab-137">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="b5bab-138">Литералы также могут использовать символы типа идентификатора ( `%` ,,,, `&` `@` `!` `#` , `$` ), как это могут быть переменные, константы и выражения.</span><span class="sxs-lookup"><span data-stu-id="b5bab-138">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="b5bab-139">Однако символы типа литерала (,,,,, `S` `I` `L` `D` `F` `R` , `C` ) можно использовать только с литералами.</span><span class="sxs-lookup"><span data-stu-id="b5bab-139">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="b5bab-140">Во всех случаях символ типа литерала должен следовать непосредственно за литеральным значением.</span><span class="sxs-lookup"><span data-stu-id="b5bab-140">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="b5bab-141">Шестнадцатеричные, двоичные и восьмеричные литералы</span><span class="sxs-lookup"><span data-stu-id="b5bab-141">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="b5bab-142">Компилятор обычно интерпретирует целочисленный литерал в десятичной системе счисления (с основанием 10).</span><span class="sxs-lookup"><span data-stu-id="b5bab-142">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="b5bab-143">Можно также определить целочисленный литерал как шестнадцатеричное (с основанием 16) числом с `&H` префиксом, как двоичное (основание 2) с `&B` префиксом, а также как восьмеричное (основание 8) число с `&O` префиксом.</span><span class="sxs-lookup"><span data-stu-id="b5bab-143">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="b5bab-144">Цифры, которые следуют за префиксом, должны соответствовать системе счисления.</span><span class="sxs-lookup"><span data-stu-id="b5bab-144">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="b5bab-145">Это показано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="b5bab-145">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="b5bab-146">Базовый номер</span><span class="sxs-lookup"><span data-stu-id="b5bab-146">Number base</span></span>|<span data-ttu-id="b5bab-147">Prefix</span><span class="sxs-lookup"><span data-stu-id="b5bab-147">Prefix</span></span>|<span data-ttu-id="b5bab-148">Допустимые разрядные значения</span><span class="sxs-lookup"><span data-stu-id="b5bab-148">Valid digit values</span></span>|<span data-ttu-id="b5bab-149">Пример</span><span class="sxs-lookup"><span data-stu-id="b5bab-149">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="b5bab-150">16 (основание 16)</span><span class="sxs-lookup"><span data-stu-id="b5bab-150">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="b5bab-151">0-9 и A-F</span><span class="sxs-lookup"><span data-stu-id="b5bab-151">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="b5bab-152">Двоичный (основание 2)</span><span class="sxs-lookup"><span data-stu-id="b5bab-152">Binary (base 2)</span></span>|`&B`|<span data-ttu-id="b5bab-153">0—1</span><span class="sxs-lookup"><span data-stu-id="b5bab-153">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="b5bab-154">8 (основание 8)</span><span class="sxs-lookup"><span data-stu-id="b5bab-154">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="b5bab-155">0-7</span><span class="sxs-lookup"><span data-stu-id="b5bab-155">0-7</span></span>|`&O77`|

<span data-ttu-id="b5bab-156">Начиная с Visual Basic 2017, можно использовать символ подчеркивания () в `_` качестве разделителя групп, чтобы повысить удобочитаемость целочисленного литерала.</span><span class="sxs-lookup"><span data-stu-id="b5bab-156">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="b5bab-157">В следующем примере символ используется `_` для группирования двоичного литерала в 8-разрядные группы:</span><span class="sxs-lookup"><span data-stu-id="b5bab-157">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="b5bab-158">Можно следовать предопределенному литералу с символом типа литерала.</span><span class="sxs-lookup"><span data-stu-id="b5bab-158">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="b5bab-159">В следующем примере приведена иллюстрация этого.</span><span class="sxs-lookup"><span data-stu-id="b5bab-159">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="b5bab-160">В предыдущем примере `counter` имеет десятичное значение-32768 и `flags` имеет десятичное значение + 32768.</span><span class="sxs-lookup"><span data-stu-id="b5bab-160">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

<span data-ttu-id="b5bab-161">Начиная с Visual Basic 15,5, можно также использовать символ подчеркивания () в `_` качестве начального разделителя между префиксом и шестнадцатеричными, двоичными или восьмеричными цифрами.</span><span class="sxs-lookup"><span data-stu-id="b5bab-161">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="b5bab-162">Пример:</span><span class="sxs-lookup"><span data-stu-id="b5bab-162">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a><span data-ttu-id="b5bab-163">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b5bab-163">See also</span></span>

- [<span data-ttu-id="b5bab-164">Типы данных</span><span class="sxs-lookup"><span data-stu-id="b5bab-164">Data Types</span></span>](index.md)
- [<span data-ttu-id="b5bab-165">Простые типы данных</span><span class="sxs-lookup"><span data-stu-id="b5bab-165">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="b5bab-166">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="b5bab-166">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="b5bab-167">Преобразование типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5bab-167">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="b5bab-168">Устранение неполадок, связанных с типами данных</span><span class="sxs-lookup"><span data-stu-id="b5bab-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="b5bab-169">Объявление переменной</span><span class="sxs-lookup"><span data-stu-id="b5bab-169">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="b5bab-170">Типы данных</span><span class="sxs-lookup"><span data-stu-id="b5bab-170">Data Types</span></span>](../../../language-reference/data-types/index.md)
