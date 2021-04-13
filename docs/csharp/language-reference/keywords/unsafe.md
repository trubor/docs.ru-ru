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
# <a name="unsafe-c-reference"></a><span data-ttu-id="7c223-103">unsafe (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="7c223-103">unsafe (C# Reference)</span></span>

<span data-ttu-id="7c223-104">Ключевое слово `unsafe` обозначает небезопасный контекст, необходимый для выполнения любых операций с применением указателей.</span><span class="sxs-lookup"><span data-stu-id="7c223-104">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="7c223-105">Дополнительные сведения см. в разделе [Небезопасный код и указатели](../unsafe-code.md).</span><span class="sxs-lookup"><span data-stu-id="7c223-105">For more information, see [Unsafe Code and Pointers](../unsafe-code.md).</span></span>

<span data-ttu-id="7c223-106">В объявлении типа или члена типа можно использовать модификатор `unsafe`.</span><span class="sxs-lookup"><span data-stu-id="7c223-106">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="7c223-107">Все текстовое пространство типа или члена типа считается небезопасным контекстом.</span><span class="sxs-lookup"><span data-stu-id="7c223-107">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="7c223-108">Например, следующий метод объявлен с модификатором `unsafe`:</span><span class="sxs-lookup"><span data-stu-id="7c223-108">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="7c223-109">Область небезопасного контекста простирается от списка параметров до конца метода, поэтому в списке параметров можно также использовать указатели:</span><span class="sxs-lookup"><span data-stu-id="7c223-109">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="7c223-110">Кроме того, небезопасный блок позволяет добавлять небезопасный код в блок.</span><span class="sxs-lookup"><span data-stu-id="7c223-110">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="7c223-111">Пример:</span><span class="sxs-lookup"><span data-stu-id="7c223-111">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="7c223-112">Для компиляции небезопасного кода нужно задать параметр [**AllowUnsafeBlocks**](../compiler-options/language.md#allowunsafeblocks).</span><span class="sxs-lookup"><span data-stu-id="7c223-112">To compile unsafe code, you must specify the [**AllowUnsafeBlocks**](../compiler-options/language.md#allowunsafeblocks) compiler option.</span></span> <span data-ttu-id="7c223-113">Небезопасный код не проверяется средой CLR.</span><span class="sxs-lookup"><span data-stu-id="7c223-113">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="7c223-114">Пример</span><span class="sxs-lookup"><span data-stu-id="7c223-114">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="7c223-115">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="7c223-115">C# language specification</span></span>

<span data-ttu-id="7c223-116">Дополнительные сведения см. в разделе [Небезопасный код](~/_csharplang/spec/unsafe-code.md) в [Спецификации языка C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="7c223-116">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="7c223-117">Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.</span><span class="sxs-lookup"><span data-stu-id="7c223-117">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c223-118">См. также</span><span class="sxs-lookup"><span data-stu-id="7c223-118">See also</span></span>

- [<span data-ttu-id="7c223-119">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="7c223-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7c223-120">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="7c223-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7c223-121">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="7c223-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7c223-122">Оператор fixed</span><span class="sxs-lookup"><span data-stu-id="7c223-122">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="7c223-123">Небезопасный код и указатели</span><span class="sxs-lookup"><span data-stu-id="7c223-123">Unsafe Code and Pointers</span></span>](../unsafe-code.md)
- [<span data-ttu-id="7c223-124">Буферы фиксированного размера</span><span class="sxs-lookup"><span data-stu-id="7c223-124">Fixed Size Buffers</span></span>](../unsafe-code.md#fixed-size-buffers)
