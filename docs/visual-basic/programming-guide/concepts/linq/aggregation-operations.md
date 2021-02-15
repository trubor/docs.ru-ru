---
description: 'Дополнительные сведения: операции агрегирования (Visual Basic)'
title: Операции агрегирования
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 2ef41faf03100814e062ec98afb8fe17b1ef64bc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462169"
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="a95f7-103">Операции агрегирования (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a95f7-103">Aggregation Operations (Visual Basic)</span></span>

<span data-ttu-id="a95f7-104">Статистическая операция вычисляет одно значение по коллекции значений.</span><span class="sxs-lookup"><span data-stu-id="a95f7-104">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="a95f7-105">Например, статистической обработкой является вычисление средней дневной температуры с использованием значений дневной температуры за месяц.</span><span class="sxs-lookup"><span data-stu-id="a95f7-105">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="a95f7-106">На приведенном ниже рисунке показаны результаты двух различных операций агрегирования с последовательностью чисел.</span><span class="sxs-lookup"><span data-stu-id="a95f7-106">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="a95f7-107">Первая операция суммирует числа.</span><span class="sxs-lookup"><span data-stu-id="a95f7-107">The first operation sums the numbers.</span></span> <span data-ttu-id="a95f7-108">Вторая операция возвращает максимальное значение в последовательности.</span><span class="sxs-lookup"><span data-stu-id="a95f7-108">The second operation returns the maximum value in the sequence.</span></span>  
  
 ![Рисунок, показывающий операции агрегирования LINQ.](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 <span data-ttu-id="a95f7-110">В следующем разделе перечислены методы стандартных операторов запросов, которые выполняют операции агрегирования.</span><span class="sxs-lookup"><span data-stu-id="a95f7-110">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a95f7-111">Методы</span><span class="sxs-lookup"><span data-stu-id="a95f7-111">Methods</span></span>  
  
|<span data-ttu-id="a95f7-112">Имя метода</span><span class="sxs-lookup"><span data-stu-id="a95f7-112">Method Name</span></span>|<span data-ttu-id="a95f7-113">Описание</span><span class="sxs-lookup"><span data-stu-id="a95f7-113">Description</span></span>|<span data-ttu-id="a95f7-114">Синтаксис выражения запроса Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a95f7-114">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="a95f7-115">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="a95f7-115">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="a95f7-116">Статистическое выражение</span><span class="sxs-lookup"><span data-stu-id="a95f7-116">Aggregate</span></span>|<span data-ttu-id="a95f7-117">Выполняет пользовательскую операцию агрегирования со значениями коллекции.</span><span class="sxs-lookup"><span data-stu-id="a95f7-117">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="a95f7-118">Не применяется</span><span class="sxs-lookup"><span data-stu-id="a95f7-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a95f7-119">Метод Average</span><span class="sxs-lookup"><span data-stu-id="a95f7-119">Average</span></span>|<span data-ttu-id="a95f7-120">Вычисляет среднее значение коллекции значений.</span><span class="sxs-lookup"><span data-stu-id="a95f7-120">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a95f7-121">Count</span><span class="sxs-lookup"><span data-stu-id="a95f7-121">Count</span></span>|<span data-ttu-id="a95f7-122">Подсчитывает число элементов в коллекции (при необходимости только те элементы, которые удовлетворяют функции предиката).</span><span class="sxs-lookup"><span data-stu-id="a95f7-122">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a95f7-123">LongCount</span><span class="sxs-lookup"><span data-stu-id="a95f7-123">LongCount</span></span>|<span data-ttu-id="a95f7-124">Подсчитывает число элементов в большой коллекции (при необходимости только те элементы, которые удовлетворяют функции предиката).</span><span class="sxs-lookup"><span data-stu-id="a95f7-124">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a95f7-125">Максимум</span><span class="sxs-lookup"><span data-stu-id="a95f7-125">Max</span></span>|<span data-ttu-id="a95f7-126">Определяет максимальное значение в коллекции.</span><span class="sxs-lookup"><span data-stu-id="a95f7-126">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a95f7-127">Минимум</span><span class="sxs-lookup"><span data-stu-id="a95f7-127">Min</span></span>|<span data-ttu-id="a95f7-128">Определяет минимальное значение в коллекции.</span><span class="sxs-lookup"><span data-stu-id="a95f7-128">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="a95f7-129">Sum</span><span class="sxs-lookup"><span data-stu-id="a95f7-129">Sum</span></span>|<span data-ttu-id="a95f7-130">Вычисляет сумму значений в коллекции.</span><span class="sxs-lookup"><span data-stu-id="a95f7-130">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="a95f7-131">Примеры синтаксиса выражений запросов</span><span class="sxs-lookup"><span data-stu-id="a95f7-131">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="a95f7-132">Среднее значение</span><span class="sxs-lookup"><span data-stu-id="a95f7-132">Average</span></span>  

 <span data-ttu-id="a95f7-133">В следующем примере кода используется `Aggregate Into Average` предложение в Visual Basic для вычисления средней температуры в массиве чисел, представляющих температуру.</span><span class="sxs-lookup"><span data-stu-id="a95f7-133">The following code example uses the `Aggregate Into Average` clause in Visual Basic to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a><span data-ttu-id="a95f7-134">Count</span><span class="sxs-lookup"><span data-stu-id="a95f7-134">Count</span></span>  

 <span data-ttu-id="a95f7-135">В следующем примере кода используется `Aggregate Into Count` предложение в Visual Basic для подсчета количества значений в массиве, которые больше или равны 80.</span><span class="sxs-lookup"><span data-stu-id="a95f7-135">The following code example uses the `Aggregate Into Count` clause in Visual Basic to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a><span data-ttu-id="a95f7-136">LongCount</span><span class="sxs-lookup"><span data-stu-id="a95f7-136">LongCount</span></span>  

 <span data-ttu-id="a95f7-137">В следующем примере кода предложение используется `Aggregate Into LongCount` для подсчета количества значений в массиве.</span><span class="sxs-lookup"><span data-stu-id="a95f7-137">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a><span data-ttu-id="a95f7-138">Max</span><span class="sxs-lookup"><span data-stu-id="a95f7-138">Max</span></span>  

 <span data-ttu-id="a95f7-139">В следующем примере кода предложение используется `Aggregate Into Max` для вычисления максимальной температуры в массиве чисел, представляющих температуру.</span><span class="sxs-lookup"><span data-stu-id="a95f7-139">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a><span data-ttu-id="a95f7-140">Min</span><span class="sxs-lookup"><span data-stu-id="a95f7-140">Min</span></span>  

 <span data-ttu-id="a95f7-141">В следующем примере кода предложение используется `Aggregate Into Min` для вычисления минимальной температуры в массиве чисел, представляющих температуру.</span><span class="sxs-lookup"><span data-stu-id="a95f7-141">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a><span data-ttu-id="a95f7-142">SUM</span><span class="sxs-lookup"><span data-stu-id="a95f7-142">Sum</span></span>  

 <span data-ttu-id="a95f7-143">В следующем примере кода предложение используется `Aggregate Into Sum` для вычисления общей суммы расходов из массива значений, представляющих расходы.</span><span class="sxs-lookup"><span data-stu-id="a95f7-143">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="a95f7-144">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a95f7-144">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="a95f7-145">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a95f7-145">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="a95f7-146">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="a95f7-146">Aggregate Clause</span></span>](../../../language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="a95f7-147">Руководство. Вычисление значений столбцов в текстовом файле CSV (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a95f7-147">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
- <span data-ttu-id="a95f7-148">[How to: Count, Sum, or Average Data](../../language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md) (Практическое руководство. Выполнение функций Count, Sum и Average)</span><span class="sxs-lookup"><span data-stu-id="a95f7-148">[How to: Count, Sum, or Average Data](../../language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)</span></span>
- <span data-ttu-id="a95f7-149">[How to: Find the Minimum or Maximum Value in a Query Result](../../language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md) (Практическое руководство. Нахождение минимального или максимального значения в результатах запроса)</span><span class="sxs-lookup"><span data-stu-id="a95f7-149">[How to: Find the Minimum or Maximum Value in a Query Result](../../language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)</span></span>
- [<span data-ttu-id="a95f7-150">Практическое руководство. Запрос самого большого файла или файлов в дереве папок (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a95f7-150">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [<span data-ttu-id="a95f7-151">Как запросить общее число байтов в наборе папок (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a95f7-151">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
