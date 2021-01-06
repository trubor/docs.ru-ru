---
title: Практическое руководство. Инициализация объектов с помощью инициализатора объектов (руководство по программированию на C#)
description: Узнайте, как использовать инициализаторы объектов для инициализации объектов типов в C# без вызова конструктора. Используйте инициализатор объектов для определения анонимного типа.
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 0c2d38713a1fdefd922234a02e23518c0f00add5
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512786"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="de348-104">Практическое руководство. Инициализация объектов с помощью инициализатора объектов (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="de348-104">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="de348-105">Инициализаторы объектов можно использовать для декларативной инициализации объектов типов без явного вызова конструктора для типа.</span><span class="sxs-lookup"><span data-stu-id="de348-105">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="de348-106">Следующие примеры демонстрируют использование инициализаторов объектов с именованными объектами.</span><span class="sxs-lookup"><span data-stu-id="de348-106">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="de348-107">Компилятор выполняет обработку инициализаторов объектов, сначала получая доступ к конструктору экземпляра без параметров, а затем обрабатывая инициализации членов.</span><span class="sxs-lookup"><span data-stu-id="de348-107">The compiler processes object initializers by first accessing the parameterless instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="de348-108">Таким образом, если конструктор без параметров объявляется как `private` в классе, произойдет сбой инициализаторов объектов, требующих открытого доступа.</span><span class="sxs-lookup"><span data-stu-id="de348-108">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="de348-109">При определении анонимного типа использовать инициализатор объекта обязательно.</span><span class="sxs-lookup"><span data-stu-id="de348-109">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="de348-110">Дополнительные сведения см. в разделе [Практическое руководство. Возвращение поднаборов свойств элементов в запросе](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="de348-110">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="de348-111">Пример</span><span class="sxs-lookup"><span data-stu-id="de348-111">Example</span></span>  

<span data-ttu-id="de348-112">В следующем примере показана инициализация нового типа `StudentName` с помощью инициализаторов объектов.</span><span class="sxs-lookup"><span data-stu-id="de348-112">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="de348-113">В этом примере задаются свойства в типе `StudentName`:</span><span class="sxs-lookup"><span data-stu-id="de348-113">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="de348-114">Инициализаторы объектов можно использовать для задания индексаторов в объекте.</span><span class="sxs-lookup"><span data-stu-id="de348-114">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="de348-115">В следующем примере определяется класс `BaseballTeam`, который использует индексатор для получения и задания игроков в различных положениях.</span><span class="sxs-lookup"><span data-stu-id="de348-115">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="de348-116">Инициализатор может назначать игроков в зависимости от сокращенного обозначения положения или номера, используемого для каждой позиции в бейсбольных карточках.</span><span class="sxs-lookup"><span data-stu-id="de348-116">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="de348-117">См. также</span><span class="sxs-lookup"><span data-stu-id="de348-117">See also</span></span>

- [<span data-ttu-id="de348-118">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="de348-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="de348-119">Инициализаторы объектов и коллекций</span><span class="sxs-lookup"><span data-stu-id="de348-119">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
