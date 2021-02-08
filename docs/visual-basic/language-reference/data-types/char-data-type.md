---
description: 'Дополнительные сведения: тип данных char (Visual Basic)'
title: Тип данных Char
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 371244ee4eae6d7dde20487dd7f38c09f3929cd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792249"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="93111-103">Тип данных Char (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93111-103">Char Data Type (Visual Basic)</span></span>

<span data-ttu-id="93111-104">Содержит 16-разрядные (2-байтовые) кодовые точки без знака в диапазоне от 0 до 65535.</span><span class="sxs-lookup"><span data-stu-id="93111-104">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="93111-105">Каждая кодовая *точка*, или код символа, представляет один символ Юникода.</span><span class="sxs-lookup"><span data-stu-id="93111-105">Each *code point*, or character code, represents a single Unicode character.</span></span>

## <a name="remarks"></a><span data-ttu-id="93111-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="93111-106">Remarks</span></span>

<span data-ttu-id="93111-107">Используйте `Char` тип данных, если необходимо хранить только один символ и не требуется дополнительная нагрузка `String` .</span><span class="sxs-lookup"><span data-stu-id="93111-107">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="93111-108">В некоторых случаях `Char()` `Char` для хранения нескольких символов можно использовать массив элементов.</span><span class="sxs-lookup"><span data-stu-id="93111-108">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>

<span data-ttu-id="93111-109">Значение по умолчанию `Char` — символ с кодовой точкой 0.</span><span class="sxs-lookup"><span data-stu-id="93111-109">The default value of `Char` is the character with a code point of 0.</span></span>

## <a name="unicode-characters"></a><span data-ttu-id="93111-110">Символы Юникода</span><span class="sxs-lookup"><span data-stu-id="93111-110">Unicode Characters</span></span>

<span data-ttu-id="93111-111">Первая 128 кодовых позиций (0 – 127) Юникода соответствует буквам и символам стандартной клавиатуры США.</span><span class="sxs-lookup"><span data-stu-id="93111-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="93111-112">Первые 128 кодовые точки те же, что и кодировка ASCII.</span><span class="sxs-lookup"><span data-stu-id="93111-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="93111-113">Вторая 128 кодовых позиций (128 – 255) представляет специальные символы, такие как буквы латинского алфавита, диакритические знаки, символы валют и дроби.</span><span class="sxs-lookup"><span data-stu-id="93111-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="93111-114">В Юникоде используются оставшиеся кодовые точки (256-65535) для широкого спектра символов, включая международные текстовые символы, диакритические знаки, математические и технические символы.</span><span class="sxs-lookup"><span data-stu-id="93111-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>

<span data-ttu-id="93111-115"><xref:System.Char.IsDigit%2A> <xref:System.Char.IsPunctuation%2A> Для определения своей классификации в Юникоде можно использовать методы, такие как и, `Char` для переменной.</span><span class="sxs-lookup"><span data-stu-id="93111-115">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>

## <a name="type-conversions"></a><span data-ttu-id="93111-116">Преобразования типов</span><span class="sxs-lookup"><span data-stu-id="93111-116">Type Conversions</span></span>

<span data-ttu-id="93111-117">Visual Basic не выполняет прямое преобразование между `Char` и числовыми типами.</span><span class="sxs-lookup"><span data-stu-id="93111-117">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="93111-118">Можно использовать <xref:Microsoft.VisualBasic.Strings.Asc%2A> <xref:Microsoft.VisualBasic.Strings.AscW%2A> функцию или для преобразования `Char` значения в `Integer` , представляющего ее кодовую точку.</span><span class="sxs-lookup"><span data-stu-id="93111-118">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="93111-119"><xref:Microsoft.VisualBasic.Strings.Chr%2A> <xref:Microsoft.VisualBasic.Strings.ChrW%2A> Для преобразования `Integer` значения в `Char` , которое имеет эту кодовую точку, можно использовать функцию или.</span><span class="sxs-lookup"><span data-stu-id="93111-119">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>

<span data-ttu-id="93111-120">Если параметр проверки типов ( [оператор Option строго](../statements/option-strict-statement.md)) включен, необходимо добавить символ типа литерала в односимвольный строковый литерал, чтобы его можно было обозначить как `Char` тип данных.</span><span class="sxs-lookup"><span data-stu-id="93111-120">If the type checking switch (the [Option Strict Statement](../statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="93111-121">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="93111-121">The following example illustrates this.</span></span> <span data-ttu-id="93111-122">Первое присваивание `charVar` переменной приводит к ошибке компилятора [BC30512](../../misc/bc30512.md) , так как `Option Strict` имеет значение ON.</span><span class="sxs-lookup"><span data-stu-id="93111-122">The first assignment to the `charVar` variable generates compiler error [BC30512](../../misc/bc30512.md) because `Option Strict` is on.</span></span> <span data-ttu-id="93111-123">Вторая компилируется успешно, так как `c` символ типа литерала определяет литерал как `Char` значение.</span><span class="sxs-lookup"><span data-stu-id="93111-123">The second compiles successfully because the `c` literal type character identifies the literal as a `Char` value.</span></span>

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a><span data-ttu-id="93111-124">Советы по программированию</span><span class="sxs-lookup"><span data-stu-id="93111-124">Programming Tips</span></span>

- <span data-ttu-id="93111-125">**Отрицательные числа.**</span><span class="sxs-lookup"><span data-stu-id="93111-125">**Negative Numbers.**</span></span> <span data-ttu-id="93111-126">`Char` является неподписанным типом и не может представлять отрицательное значение.</span><span class="sxs-lookup"><span data-stu-id="93111-126">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="93111-127">В любом случае не следует использовать `Char` для хранения числовых значений.</span><span class="sxs-lookup"><span data-stu-id="93111-127">In any case, you should not use `Char` to hold numeric values.</span></span>

- <span data-ttu-id="93111-128">**Вопросы взаимодействия.**</span><span class="sxs-lookup"><span data-stu-id="93111-128">**Interop Considerations.**</span></span> <span data-ttu-id="93111-129">Если вы используете компоненты, не написанные для платформа .NET Framework, например автоматизацию или COM-объекты, помните, что в других средах символьные типы имеют разную ширину данных (8 бит).</span><span class="sxs-lookup"><span data-stu-id="93111-129">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="93111-130">При передаче 8-разрядного аргумента в такой компонент объявите его как `Byte` вместо `Char` в новом коде Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="93111-130">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>

- <span data-ttu-id="93111-131">**Расширяющие.**</span><span class="sxs-lookup"><span data-stu-id="93111-131">**Widening.**</span></span> <span data-ttu-id="93111-132">`Char`Тип данных расширяется до `String` .</span><span class="sxs-lookup"><span data-stu-id="93111-132">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="93111-133">Это означает, что можно выполнить преобразование `Char` в `String` и не будет возникать <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="93111-133">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="93111-134">**Символы типа.**</span><span class="sxs-lookup"><span data-stu-id="93111-134">**Type Characters.**</span></span> <span data-ttu-id="93111-135">Добавление символа типа литерала `C` к строковому литералу с одним символом приводит к тому, что он применяет его к `Char` типу данных.</span><span class="sxs-lookup"><span data-stu-id="93111-135">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="93111-136">`Char` не имеет символа типа идентификатора.</span><span class="sxs-lookup"><span data-stu-id="93111-136">`Char` has no identifier type character.</span></span>

- <span data-ttu-id="93111-137">**Тип Framework.**</span><span class="sxs-lookup"><span data-stu-id="93111-137">**Framework Type.**</span></span> <span data-ttu-id="93111-138">В .NET Framework данный тип соответствует структуре <xref:System.Char?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="93111-138">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="93111-139">См. также</span><span class="sxs-lookup"><span data-stu-id="93111-139">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="93111-140">Типы данных</span><span class="sxs-lookup"><span data-stu-id="93111-140">Data Types</span></span>](index.md)
- [<span data-ttu-id="93111-141">Тип данных String</span><span class="sxs-lookup"><span data-stu-id="93111-141">String Data Type</span></span>](string-data-type.md)
- [<span data-ttu-id="93111-142">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="93111-142">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="93111-143">Сводка по преобразованию</span><span class="sxs-lookup"><span data-stu-id="93111-143">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="93111-144">Практическое руководство. Вызов функции Windows, принимающей значение беззнакового типа</span><span class="sxs-lookup"><span data-stu-id="93111-144">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="93111-145">Эффективное использование типов данных</span><span class="sxs-lookup"><span data-stu-id="93111-145">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
