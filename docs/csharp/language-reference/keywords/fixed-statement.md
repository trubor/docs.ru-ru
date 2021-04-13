---
description: Справочник по C#. Оператор fixed
title: Справочник по C#. Оператор fixed
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 2af9c4311e8326d6df933ec5d4c38354fe021e5c
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497571"
---
# <a name="fixed-statement-c-reference"></a>Оператор fixed (Справочник по C#)

Оператор `fixed` не позволяет сборщику мусора переносить перемещаемую переменную. Оператор `fixed` допускается только в [небезопасном](unsafe.md) контексте. Можно также использовать ключевое слово `fixed` для создания [буферов фиксированного размера](../unsafe-code.md#fixed-size-buffers).

Оператор `fixed` задает указатель на управляемую переменную и "закрепляет" эту переменную во время выполнения оператора. Указатели на перемещаемые управляемые переменные полезны только в контексте `fixed`. Без контекста `fixed` при сборке мусора эти переменные могут переноситься непредсказуемым образом. Компилятор C# позволяет присвоить указатель только управляемой переменной в операторе `fixed`.

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#1)]

Вы можете инициализировать указатель, используя массив, строку, буфер фиксированного размера или адрес переменной. Следующий пример иллюстрирует использование переменных адресов, массивов и строк:

[!code-csharp[Initializing fixed size buffers](snippets/FixedKeywordExamples.cs#2)]

Начиная с C# 7.3, оператор `fixed` работает с дополнительными типами, помимо массивов, строк, буферов фиксированного размера и неуправляемых переменных. Любой тип, реализующий метод `GetPinnableReference`, можно зафиксировать. `GetPinnableReference` должен вернуть переменную `ref`[неуправляемого типа](../builtin-types/unmanaged-types.md). Типы .NET <xref:System.Span%601?displayProperty=nameWithType> и <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, представленные в .NET Core 2.0, используют этот шаблон и могут быть зафиксированы. Это показано в следующем примере:

[!code-csharp[Accessing fixed memory](snippets/FixedKeywordExamples.cs#FixedSpan)]

При создании типов, которые должны участвовать в этом шаблоне, перейдите по ссылке <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> для примера реализации шаблона.

В одном операторе можно инициализировать несколько указателей одного типа.

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Чтобы инициализировать указатели разных типов, просто вложите операторы `fixed`, как показано в приведенном ниже примере.

[!code-csharp[Initializing multiple pointers](snippets/FixedKeywordExamples.cs#3)]

После выполнения кода в операторе закрепление всех переменных отменяется, и они могут пройти сборку мусора. Таким образом, не следует использовать указатели на эти переменные за пределами оператора `fixed`. Переменные, объявленные в операторе `fixed`, относятся к этому оператору, что упрощает выполнение следующего выражения.

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

Указатели, инициализированные в операторах `fixed`, являются переменными только для чтения. Чтобы изменить значение указателя, необходимо объявить переменную второго указателя и изменить ее. Переменную, объявленную в операторе `fixed`, изменить невозможно.

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

Вы можете выделить память в стеке, где на нее не будет распространяться сборка мусора, поэтому ее не нужно будет закреплять. Для этого используйте [выражение `stackalloc`](../operators/stackalloc.md).

## <a name="c-language-specification"></a>Спецификация языка C#

Подробные сведения см. в разделе [The fixed statement](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) (Оператор fixed) [спецификации языка C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Ключевые слова в C#](index.md)
- [unsafe](unsafe.md)
- [Типы указателей](../unsafe-code.md#pointer-types)
- [Буферы фиксированного размера](../unsafe-code.md#fixed-size-buffers)
