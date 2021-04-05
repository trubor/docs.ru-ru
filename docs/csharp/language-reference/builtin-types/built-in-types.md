---
title: Справочник по C#. Встроенные типы
description: Сведения о встроенных типах значений и ссылочных типах C#.
ms.date: 03/15/2021
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.openlocfilehash: 4b92add8189c6205408ec78c281eaacf04173047
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637069"
---
# <a name="built-in-types-c-reference"></a>Встроенные типы (справочник по C#)

В следующей таблице приведены встроенные типы [значений](value-types.md) языка C#:

|Ключевое слово типа C#|Тип .NET|
|--------------|-------------------------|
|[`bool`](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|
|[`byte`](integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|
|[`sbyte`](integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|
|[`char`](char.md)|<xref:System.Char?displayProperty=nameWithType>|
|[`decimal`](floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|
|[`double`](floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|
|[`float`](floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|
|[`int`](integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|
|[`uint`](integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|
|[`nint`](nint-nuint.md)|<xref:System.IntPtr?displayProperty=nameWithType>|
|[`nuint`](nint-nuint.md)|<xref:System.UIntPtr?displayProperty=nameWithType>|
|[`long`](integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|
|[`ulong`](integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|
|[`short`](integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|
|[`ushort`](integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|

В следующей таблице приведены встроенные [ссылочные](../keywords/reference-types.md) типы языка C#:

|Ключевое слово типа C#|Тип .NET|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|
|[`dynamic`](reference-types.md#the-dynamic-type)|<xref:System.Object?displayProperty=nameWithType>|

В таблицах выше каждое ключевое слово типа C# в левом столбце (кроме [nint, nuint](nint-nuint.md) и [dynamic](reference-types.md#the-dynamic-type)) является псевдонимом для соответствующего типа .NET. Они взаимозаменяемые. Например, следующие объявления объявляют переменные одного типа:

```csharp
int a = 123;
System.Int32 b = 123;
```

Типы `nint` и `nuint` в последних двух строках первой таблицы являются целыми числами собственного размера. В коде такие числа представлены определенными типами .NET, но в каждом случае ключевое слово и тип .NET не взаимозаменяемы. Для `nint` и `nuint` компилятор предоставляет преобразования и операции, как для целочисленных типов. Они отличаются от преобразований и операций для типов указателей `System.IntPtr` и `System.UIntPtr`. Дополнительные сведения см. в статье о [типах `nint` и `nuint`](nint-nuint.md).

Ключевое слово [`void`](void.md) представляет отсутствие типа. Оно используется в качестве возвращаемого типа метода, который не возвращает значение.

## <a name="see-also"></a>См. также

- [справочник по C#](../index.md)
- [Значения по умолчанию типов C#](default-values.md)
