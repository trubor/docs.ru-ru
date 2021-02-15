---
description: 'Дополнительные сведения: секционирование данных (Visual Basic)'
title: Секционирование данных
ms.date: 07/20/2015
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
ms.openlocfilehash: 264a81d1217c7f5034058761033171b9c232fae2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100465617"
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="92241-103">Секционирование данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92241-103">Partitioning Data (Visual Basic)</span></span>

<span data-ttu-id="92241-104">Секционированием в LINQ называют операцию разделения входной последовательности на два раздела без изменения порядка элементов, а затем возвращения одного из разделов.</span><span class="sxs-lookup"><span data-stu-id="92241-104">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="92241-105">На следующем рисунке показаны результаты трех различных операций секционирования в последовательности символов.</span><span class="sxs-lookup"><span data-stu-id="92241-105">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="92241-106">Первая операция возвращает первые три элемента в последовательности.</span><span class="sxs-lookup"><span data-stu-id="92241-106">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="92241-107">Вторая операция пропускает первые три элемента и возвращает остальные элементы.</span><span class="sxs-lookup"><span data-stu-id="92241-107">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="92241-108">Третья операция пропускает первые два элемента в последовательности и возвращает три следующих элемента.</span><span class="sxs-lookup"><span data-stu-id="92241-108">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Рисунок иллюстрирующий три операции секционирования LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="92241-110">Далее перечислены методы стандартных операторов запроса, которые секционируют последовательности.</span><span class="sxs-lookup"><span data-stu-id="92241-110">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="92241-111">Операторы</span><span class="sxs-lookup"><span data-stu-id="92241-111">Operators</span></span>  
  
|<span data-ttu-id="92241-112">Имя оператора</span><span class="sxs-lookup"><span data-stu-id="92241-112">Operator Name</span></span>|<span data-ttu-id="92241-113">Описание</span><span class="sxs-lookup"><span data-stu-id="92241-113">Description</span></span>|<span data-ttu-id="92241-114">Синтаксис выражения запроса Visual Basic</span><span class="sxs-lookup"><span data-stu-id="92241-114">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="92241-115">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="92241-115">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="92241-116">Skip</span><span class="sxs-lookup"><span data-stu-id="92241-116">Skip</span></span>|<span data-ttu-id="92241-117">Пропускает элементы до указанной позиции в последовательности.</span><span class="sxs-lookup"><span data-stu-id="92241-117">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="92241-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="92241-118">SkipWhile</span></span>|<span data-ttu-id="92241-119">Пропускает элементы, пока элемент не удовлетворит условию функции предиката.</span><span class="sxs-lookup"><span data-stu-id="92241-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="92241-120">Take</span><span class="sxs-lookup"><span data-stu-id="92241-120">Take</span></span>|<span data-ttu-id="92241-121">Возвращает элементы на указанную позицию в последовательности.</span><span class="sxs-lookup"><span data-stu-id="92241-121">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="92241-122">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="92241-122">TakeWhile</span></span>|<span data-ttu-id="92241-123">Принимает элементы, пока элемент не удовлетворит условию функции предиката.</span><span class="sxs-lookup"><span data-stu-id="92241-123">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="92241-124">Примеры синтаксиса выражений запросов</span><span class="sxs-lookup"><span data-stu-id="92241-124">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="92241-125">Пропустить</span><span class="sxs-lookup"><span data-stu-id="92241-125">Skip</span></span>  

 <span data-ttu-id="92241-126">В следующем примере кода используется `Skip` предложение в Visual Basic для пропуска первых четырех строк в массиве строк перед возвратом оставшихся строк в массиве.</span><span class="sxs-lookup"><span data-stu-id="92241-126">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#1)]  
  
### <a name="skipwhile"></a><span data-ttu-id="92241-127">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="92241-127">SkipWhile</span></span>  

 <span data-ttu-id="92241-128">В следующем примере кода используется `Skip While` предложение в Visual Basic для пропуска строк в массиве, в то время как первая буква строки — "a".</span><span class="sxs-lookup"><span data-stu-id="92241-128">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="92241-129">Остальные строки в массиве возвращаются.</span><span class="sxs-lookup"><span data-stu-id="92241-129">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#2)]  
  
### <a name="take"></a><span data-ttu-id="92241-130">Take</span><span class="sxs-lookup"><span data-stu-id="92241-130">Take</span></span>  

 <span data-ttu-id="92241-131">В следующем примере кода используется `Take` предложение в Visual Basic для возврата первых двух строк в массиве строк.</span><span class="sxs-lookup"><span data-stu-id="92241-131">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#3)]  
  
### <a name="takewhile"></a><span data-ttu-id="92241-132">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="92241-132">TakeWhile</span></span>  

 <span data-ttu-id="92241-133">В следующем примере кода используется `Take While` предложение в Visual Basic для возврата строк из массива, в то время как длина строки не должна превышать 5.</span><span class="sxs-lookup"><span data-stu-id="92241-133">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQPartitioning/VB/Partitioning.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="92241-134">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="92241-134">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="92241-135">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92241-135">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="92241-136">Предложение Skip</span><span class="sxs-lookup"><span data-stu-id="92241-136">Skip Clause</span></span>](../../../language-reference/queries/skip-clause.md)
- [<span data-ttu-id="92241-137">Предложение Skip While</span><span class="sxs-lookup"><span data-stu-id="92241-137">Skip While Clause</span></span>](../../../language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="92241-138">Предложение Take</span><span class="sxs-lookup"><span data-stu-id="92241-138">Take Clause</span></span>](../../../language-reference/queries/take-clause.md)
- [<span data-ttu-id="92241-139">Предложение Take While</span><span class="sxs-lookup"><span data-stu-id="92241-139">Take While Clause</span></span>](../../../language-reference/queries/take-while-clause.md)
