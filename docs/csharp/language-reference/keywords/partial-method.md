---
description: Справочник по C#. Метод partial
title: Справочник по C#. Метод partial
ms.date: 03/23/2021
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 240ad6f2f5792e4db9b032e36991f3c398f1d2f9
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111014"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="4c626-103">Метод partial (Справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="4c626-103">partial method (C# Reference)</span></span>

<span data-ttu-id="4c626-104">Сигнатура разделяемого метода определяется в одной части разделяемого типа, а его реализация — в другой части этого типа.</span><span class="sxs-lookup"><span data-stu-id="4c626-104">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="4c626-105">С помощью разделяемых методов разработчики классов могут при необходимости реализовывать ловушки методов, которые схожи с обработчиками событий.</span><span class="sxs-lookup"><span data-stu-id="4c626-105">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="4c626-106">Если реализация не предоставлена, компилятор удаляет сигнатуру во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="4c626-106">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="4c626-107">В отношении разделяемых методов применяются следующие условия:</span><span class="sxs-lookup"><span data-stu-id="4c626-107">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="4c626-108">Объявления должны начинаться с контекстного ключевого слова [partial](../../language-reference/keywords/partial-type.md).</span><span class="sxs-lookup"><span data-stu-id="4c626-108">Declarations must begin with the contextual keyword [partial](../../language-reference/keywords/partial-type.md).</span></span>

- <span data-ttu-id="4c626-109">Сигнатуры в обеих частях разделяемого типа должны совпадать.</span><span class="sxs-lookup"><span data-stu-id="4c626-109">Signatures in both parts of the partial type must match.</span></span>

<span data-ttu-id="4c626-110">Разделяемый метод может не иметь реализацию в следующих случаях.</span><span class="sxs-lookup"><span data-stu-id="4c626-110">A partial method isn't required to have an implementation in the following cases:</span></span>

- <span data-ttu-id="4c626-111">У него нет модификаторов доступа (включая [private](../../language-reference/keywords/private.md) по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="4c626-111">It doesn't have any accessibility modifiers (including the default [private](../../language-reference/keywords/private.md)).</span></span>

- <span data-ttu-id="4c626-112">Он возвращает значение [void](../../language-reference/builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="4c626-112">It returns [void](../../language-reference/builtin-types/void.md).</span></span>

- <span data-ttu-id="4c626-113">У него нет параметров [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="4c626-113">It doesn't have any [out](../../language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>

- <span data-ttu-id="4c626-114">У него нет ни одного из следующих модификаторов: [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), [sealed](../../language-reference/keywords/sealed.md), [new](../../language-reference/keywords/new-modifier.md) или [extern](../../language-reference/keywords/extern.md).</span><span class="sxs-lookup"><span data-stu-id="4c626-114">It doesn't have any of the following modifiers [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), [sealed](../../language-reference/keywords/sealed.md), [new](../../language-reference/keywords/new-modifier.md), or [extern](../../language-reference/keywords/extern.md).</span></span>

<span data-ttu-id="4c626-115">Любой метод, не соответствующий всем этим ограничениям (например, метод `public virtual partial void`), должен предоставлять реализацию.</span><span class="sxs-lookup"><span data-stu-id="4c626-115">Any method that doesn't conform to all those restrictions (for example, `public virtual partial void` method), must provide an implementation.</span></span>

<span data-ttu-id="4c626-116">В следующем примере показан разделяемый метод, определенный в двух частях разделяемого класса:</span><span class="sxs-lookup"><span data-stu-id="4c626-116">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="4c626-117">Разделяемые методы также могут быть удобны в сочетании с генераторами источника.</span><span class="sxs-lookup"><span data-stu-id="4c626-117">Partial methods can also be useful in combination with source generators.</span></span> <span data-ttu-id="4c626-118">Например, можно определить регулярное выражение, используя следующий шаблон.</span><span class="sxs-lookup"><span data-stu-id="4c626-118">For example a regex could be defined using the following pattern:</span></span>

```csharp
[RegexGenerated("(dog|cat|fish)")]
partial bool IsPetMatch(string input);
```

<span data-ttu-id="4c626-119">Дополнительные сведения см. в разделе [Разделяемые классы и методы](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4c626-119">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c626-120">См. также</span><span class="sxs-lookup"><span data-stu-id="4c626-120">See also</span></span>

- [<span data-ttu-id="4c626-121">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="4c626-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4c626-122">Тип partial</span><span class="sxs-lookup"><span data-stu-id="4c626-122">partial type</span></span>](partial-type.md)
