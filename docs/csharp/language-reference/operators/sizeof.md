---
description: Справочник по C#. Оператор sizeof
title: Справочник по C#. Оператор sizeof
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 6685cdb4fba2460ee4a47b004aa6911ab76235a4
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497376"
---
# <a name="sizeof-operator-c-reference"></a>Справочник по C#. Оператор sizeof

Оператор `sizeof` позволяет получать число байт, занятых переменной заданного типа. Аргумент оператора `sizeof` должен быть именем [неуправляемого типа](../builtin-types/unmanaged-types.md) или параметром типа, к которому применяется [ограничение](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint), указывающее, что он является неуправляемым типом.

Для использования оператора `sizeof` требуется [небезопасный](../keywords/unsafe.md) контекст. Однако выражения, приведенные в следующей таблице, вычисляются во время компиляции для получения соответствующих константных значений и им не требуется небезопасный контекст.

|Выражение|Константа|
|---------|---------------|
|`sizeof(sbyte)`|1|
|`sizeof(byte)`|1|
|`sizeof(short)`|2|
|`sizeof(ushort)`|2|
|`sizeof(int)`|4|
|`sizeof(uint)`|4|
|`sizeof(long)`|8|
|`sizeof(ulong)`|8|
|`sizeof(char)`|2|
|`sizeof(float)`|4|
|`sizeof(double)`|8|
|`sizeof(decimal)`|16|
|`sizeof(bool)`|1|

Небезопасный контекст также не требуется, если операнд оператора `sizeof` является именем [перечисляемого](../builtin-types/enum.md) типа.

В следующем примере иллюстрируется использование оператора `sizeof`.

[!code-csharp[sizeof examples](snippets/shared/SizeOfOperator.cs)]

Оператор `sizeof` возвращает число байт, выделяемых средой CLR в управляемой памяти. Для типов [структуры](../builtin-types/struct.md) в это значение входит любое заполнение, как показано в предыдущем примере. Результат использования оператора `sizeof` может отличаться от результата работы метода <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, который возвращает размер типа в *неуправляемой* памяти.

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в разделе [Оператор sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator)[спецификации языка C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>См. также раздел

- [справочник по C#](../index.md)
- [Операторы и выражения C#](index.md)
- [Операторы, связанные с указателем](pointer-related-operators.md)
- [Типы указателей](../unsafe-code.md#pointer-types)
- [Типы, связанные с памятью и диапазонами](../../../standard/memory-and-spans/index.md)
- [Универсальные шаблоны в .NET](../../../standard/generics/index.md)
