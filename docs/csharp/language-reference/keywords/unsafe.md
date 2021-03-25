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
ms.openlocfilehash: 5be895621966dd10b2b1b0f53ebf0f3c688f1ef0
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480653"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="53cf6-103">unsafe (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="53cf6-103">unsafe (C# Reference)</span></span>

<span data-ttu-id="53cf6-104">Ключевое слово `unsafe` обозначает небезопасный контекст, необходимый для выполнения любых операций с применением указателей.</span><span class="sxs-lookup"><span data-stu-id="53cf6-104">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="53cf6-105">Дополнительные сведения см. в разделе [Небезопасный код и указатели](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="53cf6-105">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="53cf6-106">В объявлении типа или члена типа можно использовать модификатор `unsafe`.</span><span class="sxs-lookup"><span data-stu-id="53cf6-106">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="53cf6-107">Все текстовое пространство типа или члена типа считается небезопасным контекстом.</span><span class="sxs-lookup"><span data-stu-id="53cf6-107">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="53cf6-108">Например, следующий метод объявлен с модификатором `unsafe`:</span><span class="sxs-lookup"><span data-stu-id="53cf6-108">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="53cf6-109">Область небезопасного контекста простирается от списка параметров до конца метода, поэтому в списке параметров можно также использовать указатели:</span><span class="sxs-lookup"><span data-stu-id="53cf6-109">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="53cf6-110">Кроме того, небезопасный блок позволяет добавлять небезопасный код в блок.</span><span class="sxs-lookup"><span data-stu-id="53cf6-110">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="53cf6-111">Пример:</span><span class="sxs-lookup"><span data-stu-id="53cf6-111">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="53cf6-112">Для компиляции небезопасного кода нужно задать параметр [**AllowUnsafeBlocks**](../compiler-options/language.md#allowunsafeblocks).</span><span class="sxs-lookup"><span data-stu-id="53cf6-112">To compile unsafe code, you must specify the [**AllowUnsafeBlocks**](../compiler-options/language.md#allowunsafeblocks) compiler option.</span></span> <span data-ttu-id="53cf6-113">Небезопасный код не проверяется средой CLR.</span><span class="sxs-lookup"><span data-stu-id="53cf6-113">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="53cf6-114">Пример</span><span class="sxs-lookup"><span data-stu-id="53cf6-114">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="53cf6-115">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="53cf6-115">C# language specification</span></span>

<span data-ttu-id="53cf6-116">Дополнительные сведения см. в разделе [Небезопасный код](~/_csharplang/spec/unsafe-code.md) в [Спецификации языка C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="53cf6-116">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="53cf6-117">Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.</span><span class="sxs-lookup"><span data-stu-id="53cf6-117">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="53cf6-118">См. также</span><span class="sxs-lookup"><span data-stu-id="53cf6-118">See also</span></span>

- [<span data-ttu-id="53cf6-119">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="53cf6-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="53cf6-120">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="53cf6-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="53cf6-121">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="53cf6-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="53cf6-122">Оператор fixed</span><span class="sxs-lookup"><span data-stu-id="53cf6-122">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="53cf6-123">Небезопасный код и указатели</span><span class="sxs-lookup"><span data-stu-id="53cf6-123">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="53cf6-124">Буферы фиксированного размера</span><span class="sxs-lookup"><span data-stu-id="53cf6-124">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
