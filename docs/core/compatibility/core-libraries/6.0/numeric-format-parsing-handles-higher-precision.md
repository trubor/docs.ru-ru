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
# <a name="standard-numeric-format-parsing-precision"></a>Значение точности при анализе стандартных числовых форматов

Теперь .NET поддерживает более высокую точность при форматировании чисел в виде строк с помощью `ToString` и `TryFormat`.

## <a name="change-description"></a>Описание изменений

При форматировании чисел в виде строк *описатель точности* в [строке формата](../../../../standard/base-types/standard-numeric-format-strings.md) представляет количество цифр в результирующей строке. В зависимости от *описателя формата*, который является [символом в начале строки](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers), точность может представлять общее число цифр, число значащих цифр или число десятичных цифр.

В предыдущих версиях .NET стандартная логика анализа числового формата ограничивалась точностью до 99 или меньше. Некоторые числовые типы имеют большую точность, но `ToString(string format)` не раскрывает их правильно. Если указать точность более 99, например, `32.ToString("C100")`, строка формата интерпретируется как [строка настраиваемого числового формата](../../../../standard/base-types/custom-numeric-format-strings.md), а не "валюта с точностью 100". В строках настраиваемого числового формата символы обрабатываются как [символьные литералы](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals). Кроме того, строка формата, содержащая недопустимый описатель формата, интерпретируется по-разному в зависимости от значения точности. `H99` создает исключение <xref:System.FormatException> для недопустимого описателя формата, хотя `H100` интерпретируется как строка настраиваемого числового формата.

Начиная с .NET 6 поддерживается точность до <xref:System.Int32.MaxValue?displayProperty=nameWithType>. Строка формата, состоящая из описателя формата с любым количеством цифр, интерпретируется как строка стандартного числового формата с точностью. Исключение <xref:System.FormatException> создается при выполнении одного или сразу двух из следующих условий:

- символ описателя формата не является [стандартным описателем формата](../../../../standard/base-types/standard-numeric-format-strings.md#standard-format-specifiers);
- точность больше <xref:System.Int32.MaxValue?displayProperty=nameWithType>.

Это изменение было реализовано в логике анализа, которая влияет на все числовые типы.

В следующей таблице показаны изменения в поведении для различных строк формата.

| Строка форматирования | Прежнее поведение | Поведение .NET 6+ |
| - | - | - |
| `C2` | Обозначает валюту с двумя десятичными цифрами | Обозначает валюту с двумя десятичными цифрами (*без изменений*) |
| `C100` | Обозначает строку настраиваемого числового формата, которая выводит "C100" | Обозначает валюту со 100 десятичными цифрами |
| `H99` | Вызывается исключение <xref:System.FormatException> из-за недопустимого описателя стандартного формата "H" | Вызывается исключение <xref:System.FormatException> из-за недопустимого описателя стандартного формата "H" (*без изменений*) |
| `H100` | Обозначает строку настраиваемого числового формата | Вызывается исключение <xref:System.FormatException> из-за недопустимого описателя стандартного формата "H" |

## <a name="version-introduced"></a>Представленная версия

6.0, предварительная версия 2

## <a name="reason-for-change"></a>Причина изменения

Это изменение исправляет непредвиденное поведение при использовании большой точности для синтаксического анализа числовых форматов.

## <a name="recommended-action"></a>Рекомендованное действие

В большинстве случаев никаких действий не требуется, и в результирующих строках отображается правильная точность.

Однако если вы хотите вернуться к предыдущему поведению, когда описатель формата интерпретируется как литеральный символ при превышении точности 99, можно заключить этот символ в одинарные кавычки или экранировать его обратной косой чертой. Например, в предыдущих версиях .NET `42.ToString("G999")` возвращает `G999`. Чтобы сохранить это поведение, измените строку формата на `"'G'999"` или `"\\G999"`. Это будет работать на платформах .NET Framework, .NET Core и .NET 5+.

Следующие строки формата будут по прежнему интерпретироваться как строки настраиваемых числовых форматов:

- Начинающиеся с любого символа, который не является алфавитным символом ASCII, например, `$` или `è`.
- Начинающиеся с алфавитного символа ASCII, за которым не следует цифра ASCII, например `A$`.
- Начинающиеся с алфавитного символа ASCII, за которым следует последовательность цифр ASCII, а затем любой символ, который не является цифрой ASCII, например `A12A`.

## <a name="affected-apis"></a>Затронутые API

Это изменение было реализовано в логике анализа, которая влияет на все числовые типы.

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

## <a name="see-also"></a>См. также раздел

- [Строки стандартных числовых форматов](../../../../standard/base-types/standard-numeric-format-strings.md)
- [Символьные литералы в строках настраиваемого формата](../../../../standard/base-types/custom-numeric-format-strings.md#character-literals)

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
