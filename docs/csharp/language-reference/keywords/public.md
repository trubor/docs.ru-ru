---
description: Справочник по C#. Ключевое слово public
title: Справочник по C#. Ключевое слово public
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 90c1d2a1d9efcdf57f914f4318bf7a743d3f37ec
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938472"
---
# <a name="public-c-reference"></a><span data-ttu-id="83f83-103">public (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="83f83-103">public (C# Reference)</span></span>

<span data-ttu-id="83f83-104">Ключевое слово `public` является модификатором доступа для типов и членов типов.</span><span class="sxs-lookup"><span data-stu-id="83f83-104">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="83f83-105">Общий доступ является уровнем доступа с максимальными правами.</span><span class="sxs-lookup"><span data-stu-id="83f83-105">Public access is the most permissive access level.</span></span> <span data-ttu-id="83f83-106">Ограничений доступа к общим членам не существует, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="83f83-106">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="83f83-107">Дополнительные сведения см. в разделах [Модификаторы доступа](../../programming-guide/classes-and-structs/access-modifiers.md) и [Уровни доступности](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="83f83-107">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="83f83-108">Пример</span><span class="sxs-lookup"><span data-stu-id="83f83-108">Example</span></span>

<span data-ttu-id="83f83-109">В следующем примере объявляются два класса: `PointTest` и `Program`.</span><span class="sxs-lookup"><span data-stu-id="83f83-109">In the following example, two classes are declared, `PointTest` and `Program`.</span></span> <span data-ttu-id="83f83-110">Доступ к открытым членам `x` и `y` класса `PointTest` осуществляется непосредственно из класса `Program`.</span><span class="sxs-lookup"><span data-stu-id="83f83-110">The public members `x` and `y` of `PointTest` are accessed directly from `Program`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="83f83-111">Если уровень доступа `public` изменить на [private](private.md) или [protected](protected.md), будет выводится следующее сообщение об ошибке:</span><span class="sxs-lookup"><span data-stu-id="83f83-111">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="83f83-112">"PointTest.y" недоступен из-за его уровня защиты.</span><span class="sxs-lookup"><span data-stu-id="83f83-112">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="83f83-113">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="83f83-113">C# language specification</span></span>  

<span data-ttu-id="83f83-114">Дополнительные сведения см. в разделе [Объявленная доступность](~/_csharplang/spec/basic-concepts.md#declared-accessibility) в [Спецификации языка C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="83f83-114">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="83f83-115">Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.</span><span class="sxs-lookup"><span data-stu-id="83f83-115">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="83f83-116">См. также</span><span class="sxs-lookup"><span data-stu-id="83f83-116">See also</span></span>

- [<span data-ttu-id="83f83-117">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="83f83-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="83f83-118">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="83f83-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="83f83-119">Модификаторы доступа</span><span class="sxs-lookup"><span data-stu-id="83f83-119">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="83f83-120">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="83f83-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="83f83-121">Модификаторы доступа</span><span class="sxs-lookup"><span data-stu-id="83f83-121">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="83f83-122">Уровни доступности</span><span class="sxs-lookup"><span data-stu-id="83f83-122">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="83f83-123">Модификаторы</span><span class="sxs-lookup"><span data-stu-id="83f83-123">Modifiers</span></span>](index.md)
- [<span data-ttu-id="83f83-124">private</span><span class="sxs-lookup"><span data-stu-id="83f83-124">private</span></span>](private.md)
- [<span data-ttu-id="83f83-125">protected</span><span class="sxs-lookup"><span data-stu-id="83f83-125">protected</span></span>](protected.md)
- [<span data-ttu-id="83f83-126">internal</span><span class="sxs-lookup"><span data-stu-id="83f83-126">internal</span></span>](internal.md)
