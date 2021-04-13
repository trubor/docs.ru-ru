---
description: Справочник по C#. Ключевое слово unsafe
title: Справочник по C#. Ключевое слово unsafe
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: e7ee7e3c721a4141160b907076533effa2848085
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498442"
---
# <a name="unsafe-c-reference"></a>unsafe (Справочник по C#)

Ключевое слово `unsafe` обозначает небезопасный контекст, необходимый для выполнения любых операций с применением указателей. Дополнительные сведения см. в разделе [Небезопасный код и указатели](../unsafe-code.md).

В объявлении типа или члена типа можно использовать модификатор `unsafe`. Все текстовое пространство типа или члена типа считается небезопасным контекстом. Например, следующий метод объявлен с модификатором `unsafe`:

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

Область небезопасного контекста простирается от списка параметров до конца метода, поэтому в списке параметров можно также использовать указатели:

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

Кроме того, небезопасный блок позволяет добавлять небезопасный код в блок. Пример:

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

Для компиляции небезопасного кода нужно задать параметр [**AllowUnsafeBlocks**](../compiler-options/language.md#allowunsafeblocks). Небезопасный код не проверяется средой CLR.

## <a name="example"></a>Пример

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a>Спецификация языка C#

Дополнительные сведения см. в разделе [Небезопасный код](~/_csharplang/spec/unsafe-code.md) в [Спецификации языка C#](/dotnet/csharp/language-reference/language-specification/introduction). Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Руководство по программированию на C#](../../programming-guide/index.md)
- [Ключевые слова в C#](index.md)
- [Оператор fixed](fixed-statement.md)
- [Небезопасный код и указатели](../unsafe-code.md)
- [Буферы фиксированного размера](../unsafe-code.md#fixed-size-buffers)
