---
title: 'Критическое изменение: значение точности при анализе стандартных числовых форматов'
description: Ознакомьтесь с критическим изменением .NET 6 в основных библиотеках .NET, в результате которого анализ стандартного числового формата теперь обеспечивает более высокую точность.
ms.date: 02/26/2021
ms.openlocfilehash: ad1555493bbc6198541365132cc421db7c01a5a2
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256924"
---
# <a name="standard-numeric-format-parsing-precision"></a><span data-ttu-id="5bd5e-103">Значение точности при анализе стандартных числовых форматов</span><span class="sxs-lookup"><span data-stu-id="5bd5e-103">Standard numeric format parsing precision</span></span>

<span data-ttu-id="5bd5e-104">Теперь .NET поддерживает более высокую точность при форматировании чисел в виде строк с помощью `ToString` и `TryFormat`.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-104">.NET now supports greater precision values when formatting numbers as strings using `ToString` and `TryFormat`.</span></span>

## <a name="change-description"></a><span data-ttu-id="5bd5e-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="5bd5e-105">Change description</span></span>

<span data-ttu-id="5bd5e-106">При форматировании чисел в виде строк *описатель точности* в [строке формата](../../../../standard/base-types/standard-numeric-format-strings.md) представляет количество цифр в результирующей строке.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-106">When formatting numbers as strings, the *precision specifier* in the [format string](../../../../standard/base-types/standard-numeric-format-strings.md) represents the number of digits in the resulting string.</span></span> <span data-ttu-id="5bd5e-107">В зависимости от *описателя формата*, который является [символом в начале строки](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers), точность может представлять общее число цифр, число значащих цифр или число десятичных цифр.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-107">Depending on the *format specifier*, which is the [character at the beginning of the string](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers), the precision can represent the total number of digits, the number of significant digits, or the number of decimal digits.</span></span>

<span data-ttu-id="5bd5e-108">В предыдущих версиях .NET стандартная логика анализа числового формата ограничивалась точностью до 99 или меньше.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-108">In previous .NET versions, the standard numeric format parsing logic is limited to a precision of 99 or less.</span></span> <span data-ttu-id="5bd5e-109">Некоторые числовые типы имеют большую точность, но `ToString(string format)` не раскрывает их правильно.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-109">Some numeric types have more precision, but `ToString(string format)` does not expose it correctly.</span></span> <span data-ttu-id="5bd5e-110">Если указать точность более 99, например, `32.ToString("C100")`, строка формата интерпретируется как [строка настраиваемого числового формата](../../../../standard/base-types/custom-numeric-format-strings.md), а не "валюта с точностью 100".</span><span class="sxs-lookup"><span data-stu-id="5bd5e-110">If you specify a precision greater than 99, for example, `32.ToString("C100")`, the format string is interpreted as a [custom numeric format string](../../../../standard/base-types/custom-numeric-format-strings.md) instead of "currency with precision 100".</span></span> <span data-ttu-id="5bd5e-111">В строках настраиваемого числового формата символы обрабатываются как [символьные литералы](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals).</span><span class="sxs-lookup"><span data-stu-id="5bd5e-111">In custom numeric format strings, characters are interpreted as [character literals](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals).</span></span> <span data-ttu-id="5bd5e-112">Кроме того, строка формата, содержащая недопустимый описатель формата, интерпретируется по-разному в зависимости от значения точности.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-112">In addition, a format string that contains an invalid format specifier is interpreted differently depending on the precision value.</span></span> <span data-ttu-id="5bd5e-113">`H99` создает исключение <xref:System.FormatException> для недопустимого описателя формата, хотя `H100` интерпретируется как строка настраиваемого числового формата.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-113">`H99` throws a <xref:System.FormatException> for the invalid format specifier, while `H100` is interpreted as a custom numeric format string.</span></span>

<span data-ttu-id="5bd5e-114">Начиная с .NET 6 поддерживается точность до <xref:System.Int32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-114">Starting in .NET 6, .NET supports precision up to <xref:System.Int32.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5bd5e-115">Строка формата, состоящая из описателя формата с любым количеством цифр, интерпретируется как строка стандартного числового формата с точностью.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-115">A format string that consists of a format specifier with any number of digits is interpreted as a standard numeric format string with precision.</span></span> <span data-ttu-id="5bd5e-116">Исключение <xref:System.FormatException> создается при выполнении одного или сразу двух из следующих условий:</span><span class="sxs-lookup"><span data-stu-id="5bd5e-116">A <xref:System.FormatException> is thrown for either or both of the following conditions:</span></span>

- <span data-ttu-id="5bd5e-117">символ описателя формата не является [стандартным описателем формата](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers);</span><span class="sxs-lookup"><span data-stu-id="5bd5e-117">The format specifier character is not a [standard format specifier](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers).</span></span>
- <span data-ttu-id="5bd5e-118">точность больше <xref:System.Int32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-118">The precision is greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="5bd5e-119">Это изменение было реализовано в логике анализа, которая влияет на все числовые типы.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-119">This change was implemented in the parsing logic that affects all numeric types.</span></span>

<span data-ttu-id="5bd5e-120">В следующей таблице показаны изменения в поведении для различных строк формата.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-120">The following table shows the behavior changes for various format strings.</span></span>

| <span data-ttu-id="5bd5e-121">Строка форматирования</span><span class="sxs-lookup"><span data-stu-id="5bd5e-121">Format string</span></span> | <span data-ttu-id="5bd5e-122">Прежнее поведение</span><span class="sxs-lookup"><span data-stu-id="5bd5e-122">Previous behavior</span></span> | <span data-ttu-id="5bd5e-123">Поведение .NET 6+</span><span class="sxs-lookup"><span data-stu-id="5bd5e-123">.NET 6+ behavior</span></span> |
| - | - | - |
| `C2` | <span data-ttu-id="5bd5e-124">Обозначает валюту с двумя десятичными цифрами</span><span class="sxs-lookup"><span data-stu-id="5bd5e-124">Denotes currency with two decimal digits</span></span> | <span data-ttu-id="5bd5e-125">Обозначает валюту с двумя десятичными цифрами (*без изменений*)</span><span class="sxs-lookup"><span data-stu-id="5bd5e-125">Denotes currency with two decimal digits (*no change*)</span></span> |
| `C100` | <span data-ttu-id="5bd5e-126">Обозначает строку настраиваемого числового формата, которая выводит "C100"</span><span class="sxs-lookup"><span data-stu-id="5bd5e-126">Denotes custom numeric format string that prints "C100"</span></span> | <span data-ttu-id="5bd5e-127">Обозначает валюту со 100 десятичными цифрами</span><span class="sxs-lookup"><span data-stu-id="5bd5e-127">Denotes currency with 100 decimal digits</span></span> |
| `H99` | <span data-ttu-id="5bd5e-128">Вызывается исключение <xref:System.FormatException> из-за недопустимого описателя стандартного формата "H"</span><span class="sxs-lookup"><span data-stu-id="5bd5e-128">Throws <xref:System.FormatException> due to invalid standard format specifier "H"</span></span> | <span data-ttu-id="5bd5e-129">Вызывается исключение <xref:System.FormatException> из-за недопустимого описателя стандартного формата "H" (*без изменений*)</span><span class="sxs-lookup"><span data-stu-id="5bd5e-129">Throws <xref:System.FormatException> due to invalid standard format specifier "H" (*no change*)</span></span> |
| `H100` | <span data-ttu-id="5bd5e-130">Обозначает строку настраиваемого числового формата</span><span class="sxs-lookup"><span data-stu-id="5bd5e-130">Denotes custom numeric format string</span></span> | <span data-ttu-id="5bd5e-131">Вызывается исключение <xref:System.FormatException> из-за недопустимого описателя стандартного формата "H"</span><span class="sxs-lookup"><span data-stu-id="5bd5e-131">Throws <xref:System.FormatException> due to invalid standard format specifier "H"</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="5bd5e-132">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="5bd5e-132">Version introduced</span></span>

<span data-ttu-id="5bd5e-133">6.0, предварительная версия 2</span><span class="sxs-lookup"><span data-stu-id="5bd5e-133">6.0 Preview 2</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="5bd5e-134">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="5bd5e-134">Reason for change</span></span>

<span data-ttu-id="5bd5e-135">Это изменение исправляет непредвиденное поведение при использовании большой точности для синтаксического анализа числовых форматов.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-135">This change corrects unexpected behavior when using higher precision for numeric format parsing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="5bd5e-136">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="5bd5e-136">Recommended action</span></span>

<span data-ttu-id="5bd5e-137">В большинстве случаев никаких действий не требуется, и в результирующих строках отображается правильная точность.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-137">In most cases, no action is necessary and the correct precision will be shown in the resulting strings.</span></span>

<span data-ttu-id="5bd5e-138">Однако если вы хотите вернуться к предыдущему поведению, когда описатель формата интерпретируется как литеральный символ при превышении точности 99, можно заключить этот символ в одинарные кавычки или экранировать его обратной косой чертой.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-138">However, if you want to revert to the previous behavior where the format specifier is interpreted as a literal character when the precision is greater than 99, you can wrap that character in single quotes or escape it with a backslash.</span></span> <span data-ttu-id="5bd5e-139">Например, в предыдущих версиях .NET `42.ToString("G999")` возвращает `G999`.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-139">For example, in previous .NET versions, `42.ToString("G999")` returns `G999`.</span></span> <span data-ttu-id="5bd5e-140">Чтобы сохранить это поведение, измените строку формата на `"'G'999"` или `"\\G999"`.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-140">To maintain that behavior, change the format string to `"'G'999"` or `"\\G999"`.</span></span> <span data-ttu-id="5bd5e-141">Это будет работать на платформах .NET Framework, .NET Core и .NET 5+.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-141">This will work on .NET Framework, .NET Core, and .NET 5+.</span></span>

<span data-ttu-id="5bd5e-142">Следующие строки формата будут по прежнему интерпретироваться как строки настраиваемых числовых форматов:</span><span class="sxs-lookup"><span data-stu-id="5bd5e-142">The following format strings will continue to be interpreted as custom numeric format strings:</span></span>

- <span data-ttu-id="5bd5e-143">Начинающиеся с любого символа, который не является алфавитным символом ASCII, например, `$` или `è`.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-143">Start with any character that is not an ASCII alphabetical character, for example, `$` or `è`.</span></span>
- <span data-ttu-id="5bd5e-144">Начинающиеся с алфавитного символа ASCII, за которым не следует цифра ASCII, например `A$`.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-144">Start with an ASCII alphabetical character that's not followed by an ASCII digit, for example, `A$`.</span></span>
- <span data-ttu-id="5bd5e-145">Начинающиеся с алфавитного символа ASCII, за которым следует последовательность цифр ASCII, а затем любой символ, который не является цифрой ASCII, например `A12A`.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-145">Start with an ASCII alphabetical character, followed by an ASCII digit sequence, and then any character that is not an ASCII digit character, for example, `A12A`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="5bd5e-146">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="5bd5e-146">Affected APIs</span></span>

<span data-ttu-id="5bd5e-147">Это изменение было реализовано в логике анализа, которая влияет на все числовые типы.</span><span class="sxs-lookup"><span data-stu-id="5bd5e-147">This change was implemented in the parsing logic that affects all numeric types.</span></span>

- <xref:System.Numerics.BigInteger.ToString(System.String)?displayProperty=fullName>
- <xref:System.Numerics.BigInteger.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Numerics.BigInteger.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int32.ToString(System.String)?displayProperty=fullName>
- <xref:System.Int32.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt32.ToString(System.String)?displayProperty=fullName>
- <xref:System.UInt32.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Byte.ToString(System.String)?displayProperty=fullName>
- <xref:System.Byte.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Byte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.SByte.ToString(System.String)?displayProperty=fullName>
- <xref:System.SByte.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.SByte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int16.ToString(System.String)?displayProperty=fullName>
- <xref:System.Int16.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt16.ToString(System.String)?displayProperty=fullName>
- <xref:System.UInt16.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int64.ToString(System.String)?displayProperty=fullName>
- <xref:System.Int64.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Int64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt64.ToString(System.String)?displayProperty=fullName>
- <xref:System.UInt64.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.UInt64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Half.ToString(System.String)?displayProperty=fullName>
- <xref:System.Half.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Half.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Single.ToString(System.String)?displayProperty=fullName>
- <xref:System.Single.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Single.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Double.ToString(System.String)?displayProperty=fullName>
- <xref:System.Double.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Double.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Decimal.ToString(System.String)?displayProperty=fullName>
- <xref:System.Decimal.ToString(System.String,System.IFormatProvider)?displayProperty=fullName>
- <xref:System.Decimal.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)?displayProperty=fullName>

## <a name="see-also"></a><span data-ttu-id="5bd5e-148">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5bd5e-148">See also</span></span>

- [<span data-ttu-id="5bd5e-149">Строки стандартных числовых форматов</span><span class="sxs-lookup"><span data-stu-id="5bd5e-149">Standard numeric format strings</span></span>](../../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="5bd5e-150">Символьные литералы в строках настраиваемого формата</span><span class="sxs-lookup"><span data-stu-id="5bd5e-150">Character literals in custom format strings</span></span>](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals)

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.Numerics.BigInteger.ToString(System.String)`
- `M:System.Numerics.BigInteger.ToString(System.String,System.IFormatProvider)`
- `M:System.Numerics.BigInteger.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Int32.ToString(System.String)`
- `M:System.Int32.ToString(System.String,System.IFormatProvider)`
- `M:System.Int32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.UInt32.ToString(System.String)`
- `M:System.UInt32.ToString(System.String,System.IFormatProvider)`
- `M:System.UInt32.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Byte.ToString(System.String)`
- `M:System.Byte.ToString(System.String,System.IFormatProvider)`
- `M:System.Byte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.SByte.ToString(System.String)`
- `M:System.SByte.ToString(System.String,System.IFormatProvider)`
- `M:System.SByte.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Int16.ToString(System.String)`
- `M:System.Int16.ToString(System.String,System.IFormatProvider)`
- `M:System.Int16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.UInt16.ToString(System.String)`
- `M:System.UInt16.ToString(System.String,System.IFormatProvider)`
- `M:System.UInt16.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Int64.ToString(System.String)`
- `M:System.Int64.ToString(System.String,System.IFormatProvider)`
- `M:System.Int64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.UInt64.ToString(System.String)`
- `M:System.UInt64.ToString(System.String,System.IFormatProvider)`
- `M:System.UInt64.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Half.ToString(System.String)`
- `M:System.Half.ToString(System.String,System.IFormatProvider)`
- `M:System.Half.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Single.ToString(System.String)`
- `M:System.Single.ToString(System.String,System.IFormatProvider)`
- `M:System.Single.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Double.ToString(System.String)`
- `M:System.Double.ToString(System.String,System.IFormatProvider)`
- `M:System.Double.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`
- `M:System.Decimal.ToString(System.String)`
- `M:System.Decimal.ToString(System.String,System.IFormatProvider)`
- `M:System.Decimal.TryFormat(System.Span{System.Char},System.Int32@,System.ReadOnlySpan{System.Char},System.IFormatProvider)`

-->
