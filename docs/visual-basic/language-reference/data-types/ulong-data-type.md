---
description: Дополнительные сведения о типе данных ULong (Visual Basic)
title: Тип данных ULong
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: 107100b4992be75dab574cbf274b53f506e267f3
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494601"
---
# <a name="ulong-data-type-visual-basic"></a>Тип данных ULong (Visual Basic)

Содержит 64-разрядные (8-байтные) целые числа без знака в диапазоне от 0 до 18446744073709551615 (более 1,84 раза больше 10 ^ 19).

## <a name="remarks"></a>Remarks

Используйте `ULong` тип данных для хранения двоичных данных, которые слишком велики для `UInteger` , или наибольшего возможного целого числа без знака.

Значение по умолчанию для типа `ULong` — 0.

## <a name="literal-assignments"></a>Присваивания литералов

Можно объявить и инициализировать `ULong` переменную, назначив ей десятичный литерал, шестнадцатеричный литерал, Восьмеричный литерал или (начиная с Visual Basic 2017) двоичный литерал. Если целочисленный литерал выходит за пределы диапазона `ULong` (то есть, если он меньше <xref:System.UInt64.MinValue?displayProperty=nameWithType> или больше <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), возникает ошибка компиляции.

В следующем примере целые числа, равные 7 934 076 125 и представленные в виде десятичного, шестнадцатеричного и двоичного литерала, назначаются значениям `ULong`.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE]
> Используйте префикс `&h` или `&H` , чтобы обозначить шестнадцатеричный литерал, префикс `&b` или `&B` обозначить двоичный литерал, а также префикс `&o` или `&O` обозначить Восьмеричный литерал. У десятичных литералов префиксов нет.

Начиная с Visual Basic 2017, можно также использовать символ подчеркивания () в `_` качестве разделителя цифр, чтобы улучшить удобочитаемость, как показано в следующем примере.

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Начиная с Visual Basic 15,5, можно также использовать символ подчеркивания () в `_` качестве начального разделителя между префиксом и шестнадцатеричными, двоичными или восьмеричными цифрами. Пример:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Числовые литералы также могут включать `UL` `ul` [символ типа](../../programming-guide/language-features/data-types/type-characters.md) или для обозначения `ULong` типа данных, как показано в следующем примере.

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>Советы по программированию

- **Отрицательные числа.** Так как `ULong` является неподписанным типом, он не может представлять отрицательное число. При использовании оператора унарного минуса ( `-` ) в выражении, результатом которого является тип `ULong` , Visual Basic преобразует выражение в `Decimal` First.

- **Соответствие CLS.** `ULong`Тип данных не является частью [спецификации](https://www.ecma-international.org/publications-and-standards/standards/ecma-335/) CLS, поэтому CLS-совместимый код не может использовать компонент, который его использует.

- **Вопросы взаимодействия.** Если вы взаимодействуете с компонентами, которые не написаны для платформа .NET Framework, например автоматизации или COM-объекты, помните, что такие типы, как, `ulong` могут иметь разную ширину данных (32 бит) в других средах. При передаче аргумента 32-bit в такой компонент объявите его как `UInteger` вместо `ULong` в управляемом коде Visual Basic.

- **Расширяющие.** `ULong`Тип данных расширяется до `Decimal` , `Single` и `Double` . Это означает, что можно преобразовать `ULong` в любой из этих типов без возникновения <xref:System.OverflowException?displayProperty=nameWithType> ошибки.

- **Символы типа.** При добавлении символов типа литерала `UL` к литералу он применяет его к `ULong` типу данных. `ULong` не имеет символа типа идентификатора.

- **Тип Framework.** В .NET Framework данный тип соответствует структуре <xref:System.UInt64?displayProperty=nameWithType>.

## <a name="see-also"></a>См. также раздел

- <xref:System.UInt64>
- [Типы данных](index.md)
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [Сводка по преобразованию](../keywords/conversion-summary.md)
- [Практическое руководство. Вызов функции Windows, принимающей значение беззнакового типа](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Эффективное использование типов данных](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
