---
description: Сведения о неявных и явных преобразованиях между встроенными числовыми типами в C#
title: Встроенные числовые преобразования — справочник по C#
ms.date: 03/17/2021
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: 5ff0289f5365a7d3d334dd0130b3b0efcdf34c60
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759694"
---
# <a name="built-in-numeric-conversions-c-reference"></a>Встроенные числовые преобразования (справочник по C#)

C# предоставляет набор [целочисленных](integral-numeric-types.md) типов и типы [с плавающей запятой](floating-point-numeric-types.md). Существует преобразование между любыми двумя числовыми типами: неявное или явное. Для выполнения явного преобразования необходимо использовать [выражение приведения](../operators/type-testing-and-cast.md#cast-expression).

## <a name="implicit-numeric-conversions"></a>Неявные числовые преобразования

В следующей таблице приведены предопределенные неявные преобразования между встроенными числовыми типами:

|Исходный тип|Кому|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`short`, `int`, `long`, `float`, `double`, `decimal` или `nint`|
|[byte](integral-numeric-types.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, `decimal`, `nint` или `nuint`|
|[short](integral-numeric-types.md)|`int`, `long`, `float`, `double` или `decimal` либо `nint`|
|[ushort](integral-numeric-types.md)|`int`, `uint`, `long`, `ulong`, `float`, `double` или `decimal`, `nint` или `nuint`|
|[int](integral-numeric-types.md)|`long`, `float`, `double` или `decimal`, `nint`|
|[uint](integral-numeric-types.md)|`long`, `ulong`, `float`, `double` или `decimal` либо `nuint`|
|[long](integral-numeric-types.md)|`float`, `double`или `decimal`|
|[ulong](integral-numeric-types.md)|`float`, `double`или `decimal`|
|[float](floating-point-numeric-types.md)|`double`|
|[nint](nint-nuint.md)|`long`, `float`, `double` или `decimal`|
|[nuint](nint-nuint.md)|`ulong`, `float`, `double` или `decimal`|

> [!NOTE]
> Неявные преобразования из `int`, `uint`, `long`, `ulong`, `nint` или `nuint` в `float` и из `long`, `ulong`, `nint` или `nuint` в `double` могут приводить к потере точности, но не к потере порядка величин. Другие неявные числовые преобразования никогда не теряют никаких сведений.

Также обратите внимание на следующее.

- Любой [целочисленный тип](integral-numeric-types.md) неявно преобразуется в любой [числовой тип с плавающей запятой](floating-point-numeric-types.md).

- Не поддерживается неявное преобразование в типы `byte` и `sbyte`. Не поддерживается неявное преобразование из типов `double` и `decimal`.

- Не поддерживается неявное преобразование между типом `decimal` и типами `float` или `double`.

- Значение константного выражения типа `int` (например, значение, представленное целочисленным литералом) может быть неявно преобразовано в `sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, `nint` или `nuint`, если оно находится в диапазоне целевого типа:

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  Как показано в предыдущем примере, если значение константы выходит за пределы диапазона целевого типа, возникает ошибка компилятора [CS0031](../../misc/cs0031.md).

## <a name="explicit-numeric-conversions"></a>Явные числовые преобразования

В следующей таблице показаны предопределенные явные преобразования между встроенными числовыми типами, для которых нет [неявного преобразования](#implicit-numeric-conversions):

|Исходный тип|Кому|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`byte`, `ushort`, `uint` или `ulong` либо `nuint`|
|[byte](integral-numeric-types.md)|`sbyte`|
|[short](integral-numeric-types.md)|`sbyte`, `byte`, `ushort`, `uint`, `ulong` или `nuint`|
|[ushort](integral-numeric-types.md)|`sbyte`, `byte`или `short`|
|[int](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong` или `nuint`|
|[uint](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort` или `int`|
|[long](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, `nint` или `nuint`|
|[ulong](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `nint` или `nuint`|
|[float](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `decimal`, `nint` или `nuint`|
|[double](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `decimal`, `nint` или `nuint`|
|[decimal](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, `nint` или `nuint`|
|[nint](nint-nuint.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong` или `nuint`|
|[nuint](nint-nuint.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long` или `nint`|

> [!NOTE]
> Явное числовое преобразование может привести к утрате данных или созданию исключения, обычно <xref:System.OverflowException>.

Также обратите внимание на следующее.

- При преобразовании значения целочисленного типа в другой целочисленный тип результат зависит от переполнения [контекста проверки](../keywords/checked-and-unchecked.md). В проверенном контексте преобразование выполняется успешно, если исходное значение находится в диапазоне конечного типа. В противном случае возникает исключение <xref:System.OverflowException>. В непроверяемом контексте преобразование всегда завершается успешно и выполняется следующим образом.

  - Если исходный тип больше целевого, исходное значение усекается путем отбрасывания его "лишних" самых значимых битов. Результат затем обрабатывается как значение целевого типа.

  - Если исходный тип меньше целевого, исходное значение дополняется знаками или нулями, чтобы иметь тот же размер, что и целевой тип. Знаки добавляются, если исходный тип имеет знак. Если у исходного типа нет знака, добавляются нули. Результат затем обрабатывается как значение целевого типа.

  - Если исходный тип совпадает по размеру с целевым, исходное значение обрабатывается как значение целевого типа.

- При преобразовании значения `decimal` в целочисленный тип оно округляется в сторону нуля до ближайшего целого значения. Если итоговое целое значение находится вне диапазона целевого типа, возникает исключение <xref:System.OverflowException>.

- При преобразовании значения `double` или `float` в целочисленный тип оно округляется в сторону нуля до ближайшего целого значения. Если полученное целое значение выходит за пределы диапазона целевого типа, результат будет зависеть от [контекста проверки](../keywords/checked-and-unchecked.md) переполнения. В проверенном контексте возникает исключение <xref:System.OverflowException>, а в непроверенном контексте результатом будет неопределенное значение целевого типа.

- При преобразовании из `double` в `float` значение `double` округляется до ближайшего значения `float`. Если значение `double` слишком мало или слишком велико для типа `float`, результатом будет ноль или бесконечность соответственно.

- При преобразовании из `float` или `double` в `decimal` исходное значение преобразуется в представление `decimal` и при необходимости округляется до ближайшего числа после 28-го десятичного разряда. В зависимости от исходного значения возможны следующие результаты:

  - Если исходное значение слишком мало для представления в виде `decimal`, результатом будет ноль.

  - Если исходное значение не является числом (NaN), равно бесконечности или слишком велико для представления в виде `decimal`, возникает исключение <xref:System.OverflowException>.

- При преобразовании из `decimal` в `float` или `double` исходное значение округляется до ближайшего значения `float` или `double` соответственно.

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в следующих разделах статьи [Спецификация языка C#](~/_csharplang/spec/introduction.md):

- [Неявные числовые преобразования](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [Явные числовые преобразования](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Приведение и преобразование типов](../../programming-guide/types/casting-and-type-conversions.md)
