---
title: Руководство по программированию на C#. Использование указателей для копирования массива байтов
description: Сведения об использовании указателей для копирования массива байтов. Изучите пример кода и ознакомьтесь с дополнительными ресурсами.
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: f0122d29729ac8ad634f39f0643902e9bb78a8a5
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103478598"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="c67d2-104">Руководство по программированию на C#. Использование указателей для копирования массива байтов</span><span class="sxs-lookup"><span data-stu-id="c67d2-104">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="c67d2-105">В следующем примере указатели используются для копирования байт из одного массива в другой.</span><span class="sxs-lookup"><span data-stu-id="c67d2-105">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="c67d2-106">В этом примере применяется ключевое слово [unsafe](../../language-reference/keywords/unsafe.md), которое позволяет использовать указатели в методе `Copy`.</span><span class="sxs-lookup"><span data-stu-id="c67d2-106">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="c67d2-107">Оператор [fixed](../../language-reference/keywords/fixed-statement.md) используется для объявления указателей исходного и конечного массивов.</span><span class="sxs-lookup"><span data-stu-id="c67d2-107">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="c67d2-108">Оператор `fixed`*закрепляет* расположение исходного и конечного массивов в памяти, чтобы они не перемещались при сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="c67d2-108">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="c67d2-109">Закрепление этих блоков памяти отменяется, когда завершается обработка блока `fixed`.</span><span class="sxs-lookup"><span data-stu-id="c67d2-109">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="c67d2-110">Поскольку метод `Copy` в этом примере использует ключевое слово `unsafe`, он должен быть скомпилирован с параметром компилятора [**AllowUnsafeBlocks**](../../language-reference/compiler-options/language.md#allowunsafeblocks).</span><span class="sxs-lookup"><span data-stu-id="c67d2-110">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [**AllowUnsafeBlocks**](../../language-reference/compiler-options/language.md#allowunsafeblocks) compiler option.</span></span>

<span data-ttu-id="c67d2-111">В этом примере доступ к элементам обоих массивов выполняется с помощью индексов, а не второго неуправляемого указателя.</span><span class="sxs-lookup"><span data-stu-id="c67d2-111">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="c67d2-112">Объявление указателей `pSource` и `pTarget` закрепляет массивы.</span><span class="sxs-lookup"><span data-stu-id="c67d2-112">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="c67d2-113">Эта возможность доступна начиная с C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="c67d2-113">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="c67d2-114">Пример</span><span class="sxs-lookup"><span data-stu-id="c67d2-114">Example</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="c67d2-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c67d2-115">See also</span></span>

- [<span data-ttu-id="c67d2-116">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="c67d2-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c67d2-117">Небезопасный код и указатели</span><span class="sxs-lookup"><span data-stu-id="c67d2-117">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="c67d2-118">**AllowUnsafeBlocks** (параметры компилятора C#)</span><span class="sxs-lookup"><span data-stu-id="c67d2-118">**AllowUnsafeBlocks** (C# Compiler Options)</span></span>](../../language-reference/compiler-options/language.md#allowunsafeblocks)
- [<span data-ttu-id="c67d2-119">Сборка мусора</span><span class="sxs-lookup"><span data-stu-id="c67d2-119">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
