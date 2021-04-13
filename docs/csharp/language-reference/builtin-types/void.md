---
description: Сведения о ключевом слове void в C#
title: Справочник по C#. void
ms.date: 02/11/2020
f1_keywords:
- void_CSharpKeyword
- void
- (void)
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 4a6afbd88f9cabc6818cdc8ba34f14ae18b195a4
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497389"
---
# <a name="void-c-reference"></a><span data-ttu-id="e6eef-103">Справочник по C#. void</span><span class="sxs-lookup"><span data-stu-id="e6eef-103">void (C# reference)</span></span>

<span data-ttu-id="e6eef-104">`void` можно использовать в качестве возвращаемого типа [метода](../../programming-guide/classes-and-structs/methods.md) (или [локальной функции](../../programming-guide/classes-and-structs/local-functions.md)) для определения того, что метод не возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="e6eef-104">You use `void` as the return type of a [method](../../programming-guide/classes-and-structs/methods.md) (or a [local function](../../programming-guide/classes-and-structs/local-functions.md)) to specify that the method doesn't return a value.</span></span>

[!code-csharp[void method](snippets/shared/VoidType.cs#VoidExample)]

<span data-ttu-id="e6eef-105">Вы также можете использовать `void` как ссылочный тип для объявления того, что тип указателя неизвестен.</span><span class="sxs-lookup"><span data-stu-id="e6eef-105">You can also use `void` as a referent type to declare a pointer to an unknown type.</span></span> <span data-ttu-id="e6eef-106">Дополнительные сведения см. в разделе [Типы указателей](../unsafe-code.md#pointer-types).</span><span class="sxs-lookup"><span data-stu-id="e6eef-106">For more information, see [Pointer types](../unsafe-code.md#pointer-types).</span></span>

<span data-ttu-id="e6eef-107">Нельзя использовать `void` в качестве типа переменной.</span><span class="sxs-lookup"><span data-stu-id="e6eef-107">You cannot use `void` as the type of a variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6eef-108">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e6eef-108">See also</span></span>

- [<span data-ttu-id="e6eef-109">справочник по C#</span><span class="sxs-lookup"><span data-stu-id="e6eef-109">C# reference</span></span>](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
