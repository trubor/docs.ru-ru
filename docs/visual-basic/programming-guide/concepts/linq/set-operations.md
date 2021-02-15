---
description: 'Дополнительные сведения: задание операций (Visual Basic)'
title: Операции над множествами
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: 9c75c9e029ba260917f59c7d2ea0341c157bf406
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471673"
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="65bec-103">Операции с наборами (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65bec-103">Set Operations (Visual Basic)</span></span>

<span data-ttu-id="65bec-104">Операции над множествами в LINQ — это операции запросов, результирующие наборы которых основываются на наличии или отсутствии эквивалентных элементов в одной или другой коллекции (или наборе).</span><span class="sxs-lookup"><span data-stu-id="65bec-104">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>

<span data-ttu-id="65bec-105">Методы стандартных операторов запросов, которые выполняют операции над множествами, перечислены в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="65bec-105">The standard query operator methods that perform set operations are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="65bec-106">Методы</span><span class="sxs-lookup"><span data-stu-id="65bec-106">Methods</span></span>

|<span data-ttu-id="65bec-107">Имя метода</span><span class="sxs-lookup"><span data-stu-id="65bec-107">Method Name</span></span>|<span data-ttu-id="65bec-108">Описание</span><span class="sxs-lookup"><span data-stu-id="65bec-108">Description</span></span>|<span data-ttu-id="65bec-109">Синтаксис выражения запроса Visual Basic</span><span class="sxs-lookup"><span data-stu-id="65bec-109">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="65bec-110">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="65bec-110">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="65bec-111">Distinct</span><span class="sxs-lookup"><span data-stu-id="65bec-111">Distinct</span></span>|<span data-ttu-id="65bec-112">Удаляет повторяющиеся значения из коллекции.</span><span class="sxs-lookup"><span data-stu-id="65bec-112">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|<span data-ttu-id="65bec-113">Исключения</span><span class="sxs-lookup"><span data-stu-id="65bec-113">Except</span></span>|<span data-ttu-id="65bec-114">Возвращает разность множеств, т. е. элементы одной коллекции, которые отсутствуют во второй.</span><span class="sxs-lookup"><span data-stu-id="65bec-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="65bec-115">Не применяется</span><span class="sxs-lookup"><span data-stu-id="65bec-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|<span data-ttu-id="65bec-116">Пересечение</span><span class="sxs-lookup"><span data-stu-id="65bec-116">Intersect</span></span>|<span data-ttu-id="65bec-117">Возвращает пересечение множеств, т. е. элементы, присутствующие в каждой из двух коллекций.</span><span class="sxs-lookup"><span data-stu-id="65bec-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="65bec-118">Не применяется</span><span class="sxs-lookup"><span data-stu-id="65bec-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|<span data-ttu-id="65bec-119">Объединение</span><span class="sxs-lookup"><span data-stu-id="65bec-119">Union</span></span>|<span data-ttu-id="65bec-120">Возвращает объединение множеств, т. е. уникальные элементы, присутствующие в одной из двух коллекций.</span><span class="sxs-lookup"><span data-stu-id="65bec-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="65bec-121">Не применяется</span><span class="sxs-lookup"><span data-stu-id="65bec-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a><span data-ttu-id="65bec-122">Сравнение операций над множествами</span><span class="sxs-lookup"><span data-stu-id="65bec-122">Comparison of Set Operations</span></span>

### <a name="distinct"></a><span data-ttu-id="65bec-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="65bec-123">Distinct</span></span>

<span data-ttu-id="65bec-124">На следующем рисунке показано поведение метода <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> применительно к последовательности символов.</span><span class="sxs-lookup"><span data-stu-id="65bec-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="65bec-125">Возвращаемая последовательность содержит уникальные элементы из входной последовательности.</span><span class="sxs-lookup"><span data-stu-id="65bec-125">The returned sequence contains the unique elements from the input sequence.</span></span>

![График, демонстрирующий поведение Distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a><span data-ttu-id="65bec-127">Исключения</span><span class="sxs-lookup"><span data-stu-id="65bec-127">Except</span></span>

<span data-ttu-id="65bec-128">На следующем рисунке показано поведение <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65bec-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="65bec-129">Возвращаемая последовательность содержит только те элементы из первой входной последовательности, которых нет во второй.</span><span class="sxs-lookup"><span data-stu-id="65bec-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>

<span data-ttu-id="65bec-130">![График, отображающий действие Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Демонстрирует поведение Except.")</span><span class="sxs-lookup"><span data-stu-id="65bec-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>

### <a name="intersect"></a><span data-ttu-id="65bec-131">Пересечение</span><span class="sxs-lookup"><span data-stu-id="65bec-131">Intersect</span></span>

<span data-ttu-id="65bec-132">На следующем рисунке показано поведение <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65bec-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="65bec-133">Возвращаемая последовательность содержит элементы, общие для обеих входных последовательностей.</span><span class="sxs-lookup"><span data-stu-id="65bec-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>

![График, отображающий пересечение двух последовательностей.](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a><span data-ttu-id="65bec-135">Объединение</span><span class="sxs-lookup"><span data-stu-id="65bec-135">Union</span></span>

<span data-ttu-id="65bec-136">На следующем рисунке показана операция объединения двух последовательностей символов.</span><span class="sxs-lookup"><span data-stu-id="65bec-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="65bec-137">Возвращаемая последовательность содержит уникальные элементы из обеих входных последовательностей.</span><span class="sxs-lookup"><span data-stu-id="65bec-137">The returned sequence contains the unique elements from both input sequences.</span></span>

![График, показывающий объединение двух последовательностей.](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a><span data-ttu-id="65bec-139">Пример синтаксиса выражения запроса</span><span class="sxs-lookup"><span data-stu-id="65bec-139">Query Expression Syntax Example</span></span>

<span data-ttu-id="65bec-140">В следующем примере `Distinct` предложение в запросе LINQ используется для возврата уникальных чисел из списка целых чисел.</span><span class="sxs-lookup"><span data-stu-id="65bec-140">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a><span data-ttu-id="65bec-141">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="65bec-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="65bec-142">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65bec-142">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="65bec-143">Предложение Distinct</span><span class="sxs-lookup"><span data-stu-id="65bec-143">Distinct Clause</span></span>](../../../language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="65bec-144">Практические руководства. объединение и сравнение коллекций строк (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65bec-144">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="65bec-145">Как найти разность множеств между двумя списками (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65bec-145">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)
