---
description: 'Дополнительные сведения: строковые функции (Visual Basic)'
title: Строковые функции
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: 1c121bc3de66caf748426b5cd04d049b30bf78bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731153"
---
# <a name="string-functions-visual-basic"></a><span data-ttu-id="162ab-103">Строковые функции (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="162ab-103">String Functions (Visual Basic)</span></span>

<span data-ttu-id="162ab-104">В следующей таблице перечислены функции, которые Visual Basic предоставляет в <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> классе для поиска и работы со строками.</span><span class="sxs-lookup"><span data-stu-id="162ab-104">The following table lists the functions that Visual Basic provides in the <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType> class to search and manipulate strings.</span></span> <span data-ttu-id="162ab-105">Их можно рассматривать как Visual Basic встроенных функций; то есть вам не нужно вызывать их как явные члены класса, как показано в примерах.</span><span class="sxs-lookup"><span data-stu-id="162ab-105">They can be regarded as Visual Basic intrinsic functions; that is, you do not have to call them as explicit members of a class, as the examples show.</span></span> <span data-ttu-id="162ab-106">Дополнительные методы и в некоторых случаях дополняют методы, доступны в <xref:System.String?displayProperty=nameWithType> классе.</span><span class="sxs-lookup"><span data-stu-id="162ab-106">Additional methods, and in some cases complementary methods, are available in the <xref:System.String?displayProperty=nameWithType> class.</span></span>

|<span data-ttu-id="162ab-107">Метод платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="162ab-107">.NET Framework method</span></span>|<span data-ttu-id="162ab-108">Описание</span><span class="sxs-lookup"><span data-stu-id="162ab-108">Description</span></span>|
|---------------------------|-----------------|
|<span data-ttu-id="162ab-109"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="162ab-109"><xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>|<span data-ttu-id="162ab-110">Возвращает `Integer` значение, представляющее код символа, соответствующий символу.</span><span class="sxs-lookup"><span data-stu-id="162ab-110">Returns an `Integer` value representing the character code corresponding to a character.</span></span>|
|<span data-ttu-id="162ab-111"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="162ab-111"><xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span></span>|<span data-ttu-id="162ab-112">Возвращает знак, связанный с указанным кодом знака.</span><span class="sxs-lookup"><span data-stu-id="162ab-112">Returns the character associated with the specified character code.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|<span data-ttu-id="162ab-113">Возвращает массив (с индексацией от нуля), который содержит подмножество массива типа `String`, выделяемое согласно указанным условиям фильтрации.</span><span class="sxs-lookup"><span data-stu-id="162ab-113">Returns a zero-based array containing a subset of a `String` array based on specified filter criteria.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|<span data-ttu-id="162ab-114">Возвращает строку, отформатированную в соответствии с инструкциями, содержащимися в формате выражения `String`.</span><span class="sxs-lookup"><span data-stu-id="162ab-114">Returns a string formatted according to instructions contained in a format `String` expression.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|<span data-ttu-id="162ab-115">Возвращает выражение в формате денежной единицы с использованием символа денежной единицы, определенного в системной панели управления.</span><span class="sxs-lookup"><span data-stu-id="162ab-115">Returns an expression formatted as a currency value using the currency symbol defined in the system control panel.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|<span data-ttu-id="162ab-116">Возвращает строковое выражение, представляющее значение даты и времени.</span><span class="sxs-lookup"><span data-stu-id="162ab-116">Returns a string expression representing a date/time value.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|<span data-ttu-id="162ab-117">Возвращает выражение в формате числа.</span><span class="sxs-lookup"><span data-stu-id="162ab-117">Returns an expression formatted as a number.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|<span data-ttu-id="162ab-118">Возвращает выражение в виде процента (умноженное на 100) с символом % в конце.</span><span class="sxs-lookup"><span data-stu-id="162ab-118">Returns an expression formatted as a percentage (that is, multiplied by 100) with a trailing % character.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|<span data-ttu-id="162ab-119">Возвращает целое число, указывающее начальную позицию первого вхождения одной строки в другую.</span><span class="sxs-lookup"><span data-stu-id="162ab-119">Returns an integer specifying the start position of the first occurrence of one string within another.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|<span data-ttu-id="162ab-120">Возвращает позицию первого вхождения одной строки в другую, начиная с правого конца строки.</span><span class="sxs-lookup"><span data-stu-id="162ab-120">Returns the position of the first occurrence of one string within another, starting from the right side of the string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|<span data-ttu-id="162ab-121">Возвращает строку, образуемую путем соединения нескольких подстрок, содержащихся в массиве.</span><span class="sxs-lookup"><span data-stu-id="162ab-121">Returns a string created by joining a number of substrings contained in an array.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|<span data-ttu-id="162ab-122">Возвращает строку или символ, преобразованные в нижний регистр.</span><span class="sxs-lookup"><span data-stu-id="162ab-122">Returns a string or character converted to lowercase.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|<span data-ttu-id="162ab-123">Возвращает строку, содержащую указанное число знаков с левой стороны строки.</span><span class="sxs-lookup"><span data-stu-id="162ab-123">Returns a string containing a specified number of characters from the left side of a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|<span data-ttu-id="162ab-124">Возвращает целое число, содержащее количество символов в строке.</span><span class="sxs-lookup"><span data-stu-id="162ab-124">Returns an integer that contains the number of characters in a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|<span data-ttu-id="162ab-125">Возвращает выровненную по левому краю строку запрашиваемой длины, содержащую указанную строку.</span><span class="sxs-lookup"><span data-stu-id="162ab-125">Returns a left-aligned string containing the specified string adjusted to the specified length.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|<span data-ttu-id="162ab-126">Возвращает строку, содержащую копию указанной строки без начальных пробелов.</span><span class="sxs-lookup"><span data-stu-id="162ab-126">Returns a string containing a copy of a specified string with no leading spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|<span data-ttu-id="162ab-127">Возвращает строку, содержащую указанное число символов из строки.</span><span class="sxs-lookup"><span data-stu-id="162ab-127">Returns a string containing a specified number of characters from a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|<span data-ttu-id="162ab-128">Возвращает строку, в которой указанная подстрока заданное число раз заменена другой подстрокой.</span><span class="sxs-lookup"><span data-stu-id="162ab-128">Returns a string in which a specified substring has been replaced with another substring a specified number of times.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|<span data-ttu-id="162ab-129">Возвращает строку, содержащую указанное число знаков с правой стороны строки.</span><span class="sxs-lookup"><span data-stu-id="162ab-129">Returns a string containing a specified number of characters from the right side of a string.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|<span data-ttu-id="162ab-130">Возвращает выровненную по правому краю строку, содержащую указанную строку, настроенную под указанную длину.</span><span class="sxs-lookup"><span data-stu-id="162ab-130">Returns a right-aligned string containing the specified string adjusted to the specified length.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|<span data-ttu-id="162ab-131">Возвращает строку, содержащую копию указанной строки без конечных пробелов.</span><span class="sxs-lookup"><span data-stu-id="162ab-131">Returns a string containing a copy of a specified string with no trailing spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|<span data-ttu-id="162ab-132">Возвращает строку, состоящую из указанного числа пробелов.</span><span class="sxs-lookup"><span data-stu-id="162ab-132">Returns a string consisting of the specified number of spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|<span data-ttu-id="162ab-133">Возвращает одномерный массив (с индексацией от нуля), содержащий указанное число подстрок.</span><span class="sxs-lookup"><span data-stu-id="162ab-133">Returns a zero-based, one-dimensional array containing a specified number of substrings.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|<span data-ttu-id="162ab-134">Возвращает -1, 0 или 1 в зависимости от результата сравнения строк.</span><span class="sxs-lookup"><span data-stu-id="162ab-134">Returns -1, 0, or 1, based on the result of a string comparison.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|<span data-ttu-id="162ab-135">Возвращает строку, преобразованную как указано.</span><span class="sxs-lookup"><span data-stu-id="162ab-135">Returns a string converted as specified.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|<span data-ttu-id="162ab-136">Возвращает строку или объект, состоящие из указанного знака, повторенного определенное количество раз.</span><span class="sxs-lookup"><span data-stu-id="162ab-136">Returns a string or object consisting of the specified character repeated the specified number of times.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|<span data-ttu-id="162ab-137">Возвращает строку, содержащую те же знаки, что и в заданной строке, но в противоположном порядке.</span><span class="sxs-lookup"><span data-stu-id="162ab-137">Returns a string in which the character order of a specified string is reversed.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|<span data-ttu-id="162ab-138">Возвращает строку, содержащую копию указанной строки без начальных или конечных пробелов.</span><span class="sxs-lookup"><span data-stu-id="162ab-138">Returns a string containing a copy of a specified string with no leading or trailing spaces.</span></span>|
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|<span data-ttu-id="162ab-139">Возвращает строку или знак, содержащий указанную строку, преобразованную в верхний регистр.</span><span class="sxs-lookup"><span data-stu-id="162ab-139">Returns a string or character containing the specified string converted to uppercase.</span></span>|

<span data-ttu-id="162ab-140">Можно использовать инструкцию [Option Compare](../statements/option-compare-statement.md) , чтобы задать, сравниваются ли строки с использованием порядка сортировки текста без учета регистра, определенного языковым стандартом системы ( `Text` ) или внутренними двоичными представлениями символов ( `Binary` ).</span><span class="sxs-lookup"><span data-stu-id="162ab-140">You can use the [Option Compare](../statements/option-compare-statement.md) statement to set whether strings are compared using a case-insensitive text sort order determined by your system's locale (`Text`) or by the internal binary representations of the characters (`Binary`).</span></span> <span data-ttu-id="162ab-141">Метод сравнения текста по умолчанию — `Binary`.</span><span class="sxs-lookup"><span data-stu-id="162ab-141">The default text comparison method is `Binary`.</span></span>

## <a name="example-ucase"></a><span data-ttu-id="162ab-142">Пример: Укасе</span><span class="sxs-lookup"><span data-stu-id="162ab-142">Example: UCase</span></span>

<span data-ttu-id="162ab-143">В данном примере функция `UCase` используется для возврата строки в верхнем регистре.</span><span class="sxs-lookup"><span data-stu-id="162ab-143">This example uses the `UCase` function to return an uppercase version of a string.</span></span>
[!code-vb[VbVbalrStrings#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#31)]

## <a name="example-ltrim"></a><span data-ttu-id="162ab-144">Пример: LTrim</span><span class="sxs-lookup"><span data-stu-id="162ab-144">Example: LTrim</span></span>

<span data-ttu-id="162ab-145">В данном примере функция `LTrim` используется, чтобы убрать пробелы в начале, а функция `RTrim` — чтобы убрать пробелы в конце строковой переменной.</span><span class="sxs-lookup"><span data-stu-id="162ab-145">This example uses the `LTrim` function to strip leading spaces and the `RTrim` function to strip trailing spaces from a string variable.</span></span> <span data-ttu-id="162ab-146">Функция `Trim` в примере используется для удаления обоих типов пробелов.</span><span class="sxs-lookup"><span data-stu-id="162ab-146">It uses the `Trim` function to strip both types of spaces.</span></span>

[!code-vb[VbVbalrStrings#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#25)]

## <a name="example-mid"></a><span data-ttu-id="162ab-147">Пример: mid</span><span class="sxs-lookup"><span data-stu-id="162ab-147">Example: Mid</span></span>

<span data-ttu-id="162ab-148">В этом примере `Mid` функция используется для возврата указанного числа символов из строки.</span><span class="sxs-lookup"><span data-stu-id="162ab-148">This example uses the `Mid` function to return a specified number of characters from a string.</span></span>

[!code-vb[VbVbalrStrings#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#17)]

## <a name="example-len"></a><span data-ttu-id="162ab-149">Пример: len</span><span class="sxs-lookup"><span data-stu-id="162ab-149">Example: Len</span></span>

<span data-ttu-id="162ab-150">В данном примере `Len` используется для возврата числа знаков в строке.</span><span class="sxs-lookup"><span data-stu-id="162ab-150">This example uses `Len` to return the number of characters in a string.</span></span>

[!code-vb[VbVbalrStrings#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#33)]

## <a name="example-instr"></a><span data-ttu-id="162ab-151">Пример: InStr</span><span class="sxs-lookup"><span data-stu-id="162ab-151">Example: InStr</span></span>

<span data-ttu-id="162ab-152">В данном примере функция `InStr` используется для возврата позиции первого вхождения одной строки в другую.</span><span class="sxs-lookup"><span data-stu-id="162ab-152">This example uses the `InStr` function to return the position of the first occurrence of one string within another.</span></span>

[!code-vb[VbVbalrStrings#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#8)]

## <a name="example-format"></a><span data-ttu-id="162ab-153">Пример: Format</span><span class="sxs-lookup"><span data-stu-id="162ab-153">Example: Format</span></span>

<span data-ttu-id="162ab-154">В данном примере показаны различные способы использования функции `Format` для форматирования значений с применением как форматов `String`, так и определенных пользователем форматов.</span><span class="sxs-lookup"><span data-stu-id="162ab-154">This example shows various uses of the `Format` function to format values using both `String` formats and user-defined formats.</span></span> <span data-ttu-id="162ab-155">Фактическое отображение системой разделителя даты (`/`), разделителя времени (`:` и индикаторов AM/PM (`t` и `tt`) зависит от региональных параметров, применяемых кодом.</span><span class="sxs-lookup"><span data-stu-id="162ab-155">For the date separator (`/`), time separator (`:`), and the AM/PM indicators (`t` and `tt`), the actual formatted output displayed by your system depends on the locale settings the code is using.</span></span> <span data-ttu-id="162ab-156">При отображении времени и даты в среде разработки используется короткий формат времени и даты региональных установок кода.</span><span class="sxs-lookup"><span data-stu-id="162ab-156">When times and dates are displayed in the development environment, the short time format and short date format of the code locale are used.</span></span>

> [!NOTE]
> <span data-ttu-id="162ab-157">Для языков, использующих 24-часовой формат, индикаторы AM/PM (`t` и `tt`) не отображаются.</span><span class="sxs-lookup"><span data-stu-id="162ab-157">For locales that use a 24-hour clock, the AM/PM indicators (`t` and `tt`) display nothing.</span></span>

[!code-vb[VbVbalrStrings#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#27)]

## <a name="see-also"></a><span data-ttu-id="162ab-158">См. также</span><span class="sxs-lookup"><span data-stu-id="162ab-158">See also</span></span>

- [<span data-ttu-id="162ab-159">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="162ab-159">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="162ab-160">Члены библиотеки времени выполнения Visual Basic</span><span class="sxs-lookup"><span data-stu-id="162ab-160">Visual Basic Runtime Library Members</span></span>](../runtime-library-members.md)
- [<span data-ttu-id="162ab-161">Сводка по работе со строками</span><span class="sxs-lookup"><span data-stu-id="162ab-161">String Manipulation Summary</span></span>](../keywords/string-manipulation-summary.md)
- [<span data-ttu-id="162ab-162">Методы класса System. String</span><span class="sxs-lookup"><span data-stu-id="162ab-162">System.String class methods</span></span>](xref:System.String#methods)
