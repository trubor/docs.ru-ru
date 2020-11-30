---
description: Справочник по C#. Предложение select
title: Справочник по C#. Предложение select
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: d67c99cc841c08a63cc83843a07a46e80199b9d1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "89136906"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="de699-103">Предложение "select" (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="de699-103">select clause (C# Reference)</span></span>

<span data-ttu-id="de699-104">В выражении запроса предложение `select` задает тип значений, которые будут получены при выполнении запроса.</span><span class="sxs-lookup"><span data-stu-id="de699-104">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="de699-105">Получаемый результат зависит от вычисления всех предыдущих предложений и любых выражений в самом предложении `select`.</span><span class="sxs-lookup"><span data-stu-id="de699-105">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="de699-106">Выражение запроса должно оканчиваться предложением `select` или [group](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="de699-106">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="de699-107">В следующем примере показано простое предложение `select` в выражении запроса.</span><span class="sxs-lookup"><span data-stu-id="de699-107">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="de699-108">Тип последовательности, создаваемой предложением `select`, определяет тип переменной запроса `queryHighScores`.</span><span class="sxs-lookup"><span data-stu-id="de699-108">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="de699-109">В самом простом случае предложение `select` просто задает переменную диапазона.</span><span class="sxs-lookup"><span data-stu-id="de699-109">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="de699-110">В этом случае возвращаемая последовательность содержит элементы того же типа, что и источник данных.</span><span class="sxs-lookup"><span data-stu-id="de699-110">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="de699-111">Дополнительные сведения см. в разделе [Связи типов в операциях запроса LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="de699-111">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="de699-112">Тем не менее предложение `select` также реализует эффективный механизм для преобразования (или *проецирования*) данных источника в новые типы.</span><span class="sxs-lookup"><span data-stu-id="de699-112">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="de699-113">Дополнительные сведения см. в разделе [Преобразования данных с помощью LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="de699-113">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="de699-114">Пример</span><span class="sxs-lookup"><span data-stu-id="de699-114">Example</span></span>

<span data-ttu-id="de699-115">В следующем примере показаны различные формы, которые может принимать предложение `select`.</span><span class="sxs-lookup"><span data-stu-id="de699-115">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="de699-116">В каждом запросе обратите внимание на связь между предложением `select` и типом *переменной запроса* (`studentQuery1`, `studentQuery2` и т. д.).</span><span class="sxs-lookup"><span data-stu-id="de699-116">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="de699-117">Как показано в `studentQuery8` в предыдущем примере, в некоторых случаях требуется, чтобы элементы возвращаемой последовательности содержали только подмножество свойств элементов источника.</span><span class="sxs-lookup"><span data-stu-id="de699-117">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="de699-118">Максимально уменьшая размер возвращаемой последовательности, вы можете снизить требования к памяти и, соответственно, повысить скорость выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="de699-118">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="de699-119">Это можно сделать, создав анонимный тип в предложении `select` и используя инициализатор объекта для его инициализации с соответствующими свойствами из элементов источника.</span><span class="sxs-lookup"><span data-stu-id="de699-119">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="de699-120">Пример того, как это сделать, см. в разделе [Инициализаторы объектов и коллекций](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="de699-120">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="de699-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="de699-121">Remarks</span></span>

<span data-ttu-id="de699-122">Во время компиляции предложение `select` преобразуется в вызов метода <xref:System.Linq.Enumerable.Select%2A> стандартного оператора запроса.</span><span class="sxs-lookup"><span data-stu-id="de699-122">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="de699-123">См. также</span><span class="sxs-lookup"><span data-stu-id="de699-123">See also</span></span>

- [<span data-ttu-id="de699-124">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="de699-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="de699-125">Ключевые слова запроса (LINQ)</span><span class="sxs-lookup"><span data-stu-id="de699-125">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="de699-126">предложение from</span><span class="sxs-lookup"><span data-stu-id="de699-126">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="de699-127">partial (метод) (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="de699-127">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="de699-128">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="de699-128">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="de699-129">LINQ в C#</span><span class="sxs-lookup"><span data-stu-id="de699-129">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="de699-130">LINQ</span><span class="sxs-lookup"><span data-stu-id="de699-130">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
