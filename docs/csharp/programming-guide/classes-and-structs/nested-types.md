---
title: Руководство по программированию на C#. Вложенные типы
description: Тип, определенный внутри класса, структуры или интерфейса, называется в C# вложенным типом.
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 853138beed6ad9ddffa789f0080ca1fd2ba9d700
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511922"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="aabcd-103">Вложенные типы (Руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="aabcd-103">Nested Types (C# Programming Guide)</span></span>

<span data-ttu-id="aabcd-104">Тип, определенный внутри [класса](../../language-reference/keywords/class.md), [структуры](../../language-reference/builtin-types/struct.md) или [интерфейса](../../language-reference/keywords/interface.md), называется вложенным типом.</span><span class="sxs-lookup"><span data-stu-id="aabcd-104">A type defined within a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) is called a nested type.</span></span> <span data-ttu-id="aabcd-105">Пример</span><span class="sxs-lookup"><span data-stu-id="aabcd-105">For example</span></span>

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

<span data-ttu-id="aabcd-106">Независимо от того, является ли внешний тип классом, интерфейсом или структурой, вложенным типам по умолчанию присваивается модификатор [private](../../language-reference/keywords/private.md), из-за чего они доступны только из содержащего их типа.</span><span class="sxs-lookup"><span data-stu-id="aabcd-106">Regardless of whether the outer type is a class, interface, or struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="aabcd-107">В предыдущем примере класс `Nested` недоступен для внешних типов.</span><span class="sxs-lookup"><span data-stu-id="aabcd-107">In the previous example, the `Nested` class is inaccessible to external types.</span></span>

<span data-ttu-id="aabcd-108">Также можно указать [модификатор доступа](../../language-reference/keywords/access-modifiers.md), определяющий доступность вложенного типа, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="aabcd-108">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="aabcd-109">Вложенные типы **класса** могут иметь модификаторы [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) или [private protected](../../language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="aabcd-109">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span>

   <span data-ttu-id="aabcd-110">Тем не менее при определении вложенного класса `protected`, `protected internal` или `private protected` внутри [запечатанного класса](../../language-reference/keywords/sealed.md) возникает предупреждение компилятора [CS0628](../../misc/cs0628.md) "Новый защищенный член объявлен в запечатанном классе".</span><span class="sxs-lookup"><span data-stu-id="aabcd-110">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>

   <span data-ttu-id="aabcd-111">Также учитывайте, что внешняя доступность вложенного типа нарушает правило качества кода [CA1034](../../../fundamentals/code-analysis/quality-rules/ca1034.md) "Вложенные типы не должны быть видимыми".</span><span class="sxs-lookup"><span data-stu-id="aabcd-111">Also be aware that making a nested type externally visible violates the code quality rule [CA1034](../../../fundamentals/code-analysis/quality-rules/ca1034.md) "Nested types should not be visible".</span></span>

- <span data-ttu-id="aabcd-112">Вложенные типы **структуры** могут иметь модификаторы [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md) или [private](../../language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="aabcd-112">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>

<span data-ttu-id="aabcd-113">В следующем примере класс `Nested` определяется как открытый:</span><span class="sxs-lookup"><span data-stu-id="aabcd-113">The following example makes the `Nested` class public:</span></span>

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

<span data-ttu-id="aabcd-114">Вложенный (внутренний) тип может получить доступ к вмещающему (внешнему) типу.</span><span class="sxs-lookup"><span data-stu-id="aabcd-114">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="aabcd-115">Чтобы получить доступ к вмещающему типу, передайте его в качестве аргумента в конструктор вложенного типа.</span><span class="sxs-lookup"><span data-stu-id="aabcd-115">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="aabcd-116">Пример:</span><span class="sxs-lookup"><span data-stu-id="aabcd-116">For example:</span></span>

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

<span data-ttu-id="aabcd-117">Вложенный тип имеет доступ ко всем членам, которые доступны вмещающему типу.</span><span class="sxs-lookup"><span data-stu-id="aabcd-117">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="aabcd-118">Он может получать доступ к закрытым и защищенным членам вмещающего типа, включая любые наследуемые защищенные члены.</span><span class="sxs-lookup"><span data-stu-id="aabcd-118">It can access private and protected members of the containing type, including any inherited protected members.</span></span>

<span data-ttu-id="aabcd-119">В предыдущем объявлении полным именем класса `Nested` является `Container.Nested`.</span><span class="sxs-lookup"><span data-stu-id="aabcd-119">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="aabcd-120">Это имя используется для создания нового экземпляра вложенного класса, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="aabcd-120">This is the name used to create a new instance of the nested class, as follows:</span></span>

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a><span data-ttu-id="aabcd-121">См. также</span><span class="sxs-lookup"><span data-stu-id="aabcd-121">See also</span></span>

- [<span data-ttu-id="aabcd-122">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="aabcd-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="aabcd-123">Классы и структуры</span><span class="sxs-lookup"><span data-stu-id="aabcd-123">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="aabcd-124">Модификаторы доступа</span><span class="sxs-lookup"><span data-stu-id="aabcd-124">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="aabcd-125">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="aabcd-125">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="aabcd-126">Правило CA1034</span><span class="sxs-lookup"><span data-stu-id="aabcd-126">CA1034 rule</span></span>](../../../fundamentals/code-analysis/quality-rules/ca1034.md)
