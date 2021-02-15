---
description: 'Дополнительные сведения: интерполяция строк (Visual Basic Reference)'
title: Интерполированные строки
ms.date: 10/31/2017
ms.openlocfilehash: c054401070079bdf85181619ef43c246feea5e18
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429666"
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="a3ba8-103">Строки с интерполяцией (Visual Basic ссылка)</span><span class="sxs-lookup"><span data-stu-id="a3ba8-103">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="a3ba8-104">Используется для создания строк.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-104">Used to construct strings.</span></span>  <span data-ttu-id="a3ba8-105">Интерполированное строковое выражение выглядит как строка шаблона, которая содержит *интерполированные выражения*.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-105">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="a3ba8-106">Интерполированная строка возвращает строку, которая заменяет содержащиеся в ней интерполированные выражения строковыми представлениями.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-106">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="a3ba8-107">Эта функция доступна в Visual Basic 14 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-107">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="a3ba8-108">Аргументы интерполированной строки понять проще, чем [строку составного формата](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="a3ba8-108">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="a3ba8-109">Например, интерполированная строка</span><span class="sxs-lookup"><span data-stu-id="a3ba8-109">For example, the interpolated string</span></span>

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

<span data-ttu-id="a3ba8-110">содержит два интерполированных выражения "{name}" и "{hours:hh}".</span><span class="sxs-lookup"><span data-stu-id="a3ba8-110">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="a3ba8-111">Эквивалентная строка составного формата имеет следующий вид:</span><span class="sxs-lookup"><span data-stu-id="a3ba8-111">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours)
```

<span data-ttu-id="a3ba8-112">Структура интерполированной строки выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="a3ba8-112">The structure of an interpolated string is:</span></span>

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

<span data-ttu-id="a3ba8-113">где:</span><span class="sxs-lookup"><span data-stu-id="a3ba8-113">where:</span></span>

- <span data-ttu-id="a3ba8-114">*field-width* — это целое число со знаком, указывающее количество символов в поле.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-114">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="a3ba8-115">Если оно является положительным, поле выравнивается по правому краю, если оно отрицательное — по левому краю.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-115">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span>

- <span data-ttu-id="a3ba8-116">*format-string* — это строка формата, соответствующая типу форматируемого объекта.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-116">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="a3ba8-117">Например, для <xref:System.DateTime> значения может использоваться [строка стандартного формата даты и времени](../../../../standard/base-types/standard-date-and-time-format-strings.md) , например "d" или "d".</span><span class="sxs-lookup"><span data-stu-id="a3ba8-117">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](../../../../standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a3ba8-118">Между `$` и `"` в начале строки не может быть пробела.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-118">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="a3ba8-119">Это приводит к ошибке компилятора.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-119">Doing so causes a compiler error.</span></span>

<span data-ttu-id="a3ba8-120">Интерполированную строку можно использовать везде, где допустимо применять строковый литерал.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-120">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="a3ba8-121">Интерполированная строка вычисляется каждый раз, когда выполняется код с интерполированной строкой.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-121">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="a3ba8-122">Это позволяет разделить определение и вычисление интерполированной строки.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-122">This allows you to separate the definition and evaluation of an interpolated string.</span></span>

<span data-ttu-id="a3ba8-123">Чтобы включить в интерполированную строку фигурные скобки ("{" или "}"), используйте две фигурные скобки — "{{" или "}}".</span><span class="sxs-lookup"><span data-stu-id="a3ba8-123">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="a3ba8-124">Дополнительные сведения см в разделе «Неявные преобразования».</span><span class="sxs-lookup"><span data-stu-id="a3ba8-124">See the Implicit Conversions section for more details.</span></span>

<span data-ttu-id="a3ba8-125">Если интерполированная строка содержит другие символы со специальным значением в интерполированной строке, например, знак кавычки ("), двоеточие (:) или запятая (,), их необходимо экранировать, если они встречаются в обычном тексте, или они должны быть включены в выражение, разделенное круглыми скобками, если они являются языковыми элементами, включенными в интерполированное выражение.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-125">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="a3ba8-126">В следующем примере кавычки используются для включения их в результирующую строку:</span><span class="sxs-lookup"><span data-stu-id="a3ba8-126">The following example escapes quotation marks to include them in the result string:</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a><span data-ttu-id="a3ba8-127">Неявные преобразования</span><span class="sxs-lookup"><span data-stu-id="a3ba8-127">Implicit Conversions</span></span>

<span data-ttu-id="a3ba8-128">Существует три преобразования неявных типов из интерполированных строк.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-128">There are three implicit type conversions from an interpolated string:</span></span>

1. <span data-ttu-id="a3ba8-129">Преобразование интерполированной строки в <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-129">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="a3ba8-130">В следующем примере возвращается строка, интерполированные строковые выражения которой были заменены их строковыми представлениями.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-130">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="a3ba8-131">Пример:</span><span class="sxs-lookup"><span data-stu-id="a3ba8-131">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   <span data-ttu-id="a3ba8-132">Это окончательный результат интерпретации строк.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-132">This is the final result of a string interpretation.</span></span> <span data-ttu-id="a3ba8-133">Все вхождения двойных фигурных скобок ("{{" и "}}") преобразуются в одиночную фигурную скобку.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-133">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span>

2. <span data-ttu-id="a3ba8-134">Преобразование интерполированной строки в переменную <xref:System.IFormattable>, которая позволяет создавать несколько результирующих строк с содержимым для конкретного языка из одного экземпляра <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-134">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="a3ba8-135">Это полезно для включения правильных форматов чисел и дат для отдельных языков.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-135">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="a3ba8-136">Все вхождения двойных фигурных скобок ("{{" и "}}") остаются двойными фигурными скобками до тех пор, пока строка не будет отформатирована путем явного или неявного вызова метода <xref:System.Object.ToString>.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-136">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="a3ba8-137">Все содержащиеся в них выражения интерполяции преобразуются в {0} , {1} и т. д.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-137">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   <span data-ttu-id="a3ba8-138">В следующем примере используется отражение для отображения членов, а также значений поля и свойства переменной <xref:System.IFormattable>, созданной из интерполированной строки.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-138">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="a3ba8-139">Кроме того, переменная <xref:System.IFormattable> передается в метод <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-139">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   <span data-ttu-id="a3ba8-140">Обратите внимание, что интерполированную строку можно проверить только с помощью отражения.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-140">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="a3ba8-141">Если она передается методу форматирования строк, например <xref:System.Console.WriteLine(System.String)>, элементы формата разрешаются и возвращается результирующая строка.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-141">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span>

3. <span data-ttu-id="a3ba8-142">Преобразование строки с интерполяцией в <xref:System.FormattableString> переменную, представляющую строку составного формата.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-142">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="a3ba8-143">Проверка строки составного формата и способа ее отрисовки в виде результирующей строки может, например, обеспечивать защиту от атак путем внедрения кода, если выполнялось построение запроса.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-143">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="a3ba8-144">А <xref:System.FormattableString> также включает в себя:</span><span class="sxs-lookup"><span data-stu-id="a3ba8-144">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="a3ba8-145">Перегрузка <xref:System.FormattableString.ToString>, которая формирует результирующую строку для <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-145">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>

      - <span data-ttu-id="a3ba8-146"><xref:System.FormattableString.Invariant%2A>Метод, создающий строку для <xref:System.Globalization.CultureInfo.InvariantCulture> .</span><span class="sxs-lookup"><span data-stu-id="a3ba8-146">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>

      - <span data-ttu-id="a3ba8-147">Метод <xref:System.FormattableString.ToString(System.IFormatProvider)>, который формирует результирующую строку для указанного языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-147">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="a3ba8-148">Все вхождения двойных фигурных скобок ("{{" и "}}") остаются в виде двойных фигурных скобок до тех пор, пока не будет выполнено форматирование.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-148">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="a3ba8-149">Все содержащиеся в них выражения интерполяции преобразуются в {0} , {1} и т. д.</span><span class="sxs-lookup"><span data-stu-id="a3ba8-149">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a><span data-ttu-id="a3ba8-150">См. также</span><span class="sxs-lookup"><span data-stu-id="a3ba8-150">See also</span></span>

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [<span data-ttu-id="a3ba8-151">Справочник по языку Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a3ba8-151">Visual Basic Language Reference</span></span>](index.md)
