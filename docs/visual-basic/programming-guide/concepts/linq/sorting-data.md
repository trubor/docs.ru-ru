---
description: 'Дополнительные сведения: Сортировка данных (Visual Basic)'
title: Сортировка данных
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: 83e05b2af1b3421d004a87630cd5df43f2a21ae4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468555"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="6daf0-103">Сортировка данных (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6daf0-103">Sorting Data (Visual Basic)</span></span>

<span data-ttu-id="6daf0-104">Операция сортировки упорядочивает элементы последовательности на основе одного или нескольких атрибутов.</span><span class="sxs-lookup"><span data-stu-id="6daf0-104">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="6daf0-105">Первый критерий сортировки выполняет первичную сортировку элементов.</span><span class="sxs-lookup"><span data-stu-id="6daf0-105">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="6daf0-106">Указав второй критерий поиска, можно сортировать элементы внутри каждой группы первичной сортировки.</span><span class="sxs-lookup"><span data-stu-id="6daf0-106">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>

<span data-ttu-id="6daf0-107">На следующем рисунке показаны результаты операции сортировки в алфавитном порядке в последовательности символов.</span><span class="sxs-lookup"><span data-stu-id="6daf0-107">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>

![Рисунок с операциями сортировки в алфавитном порядке.](./media/sorting-data/alphabetical-sort-operation.png)

<span data-ttu-id="6daf0-109">Далее перечислены методы стандартных операторов запроса, которые выполняют сортировку данных.</span><span class="sxs-lookup"><span data-stu-id="6daf0-109">The standard query operator methods that sort data are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="6daf0-110">Методы</span><span class="sxs-lookup"><span data-stu-id="6daf0-110">Methods</span></span>

|<span data-ttu-id="6daf0-111">Имя метода</span><span class="sxs-lookup"><span data-stu-id="6daf0-111">Method Name</span></span>|<span data-ttu-id="6daf0-112">Описание</span><span class="sxs-lookup"><span data-stu-id="6daf0-112">Description</span></span>|<span data-ttu-id="6daf0-113">Синтаксис выражения запроса Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6daf0-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="6daf0-114">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="6daf0-114">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="6daf0-115">OrderBy</span><span class="sxs-lookup"><span data-stu-id="6daf0-115">OrderBy</span></span>|<span data-ttu-id="6daf0-116">Сортировка значений в возрастающем порядке.</span><span class="sxs-lookup"><span data-stu-id="6daf0-116">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="6daf0-117">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="6daf0-117">OrderByDescending</span></span>|<span data-ttu-id="6daf0-118">Сортировка значений в убывающем порядке.</span><span class="sxs-lookup"><span data-stu-id="6daf0-118">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="6daf0-119">ThenBy</span><span class="sxs-lookup"><span data-stu-id="6daf0-119">ThenBy</span></span>|<span data-ttu-id="6daf0-120">Дополнительная сортировка по возрастанию.</span><span class="sxs-lookup"><span data-stu-id="6daf0-120">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="6daf0-121">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="6daf0-121">ThenByDescending</span></span>|<span data-ttu-id="6daf0-122">Дополнительная сортировка по убыванию.</span><span class="sxs-lookup"><span data-stu-id="6daf0-122">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="6daf0-123">Reverse</span><span class="sxs-lookup"><span data-stu-id="6daf0-123">Reverse</span></span>|<span data-ttu-id="6daf0-124">Изменение порядка элементов в коллекции на обратный.</span><span class="sxs-lookup"><span data-stu-id="6daf0-124">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="6daf0-125">Не применяется</span><span class="sxs-lookup"><span data-stu-id="6daf0-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="6daf0-126">Примеры синтаксиса выражений запросов</span><span class="sxs-lookup"><span data-stu-id="6daf0-126">Query Expression Syntax Examples</span></span>

### <a name="primary-sort-examples"></a><span data-ttu-id="6daf0-127">Примеры основной сортировки</span><span class="sxs-lookup"><span data-stu-id="6daf0-127">Primary Sort Examples</span></span>

#### <a name="primary-ascending-sort"></a><span data-ttu-id="6daf0-128">Основная сортировка по возрастанию</span><span class="sxs-lookup"><span data-stu-id="6daf0-128">Primary Ascending Sort</span></span>

<span data-ttu-id="6daf0-129">В следующем примере показано использование предложения `Order By` в запросе LINQ для сортировки строк в массиве по длине строки в порядке возрастания.</span><span class="sxs-lookup"><span data-stu-id="6daf0-129">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
' quick
' brown
' jumps
```

#### <a name="primary-descending-sort"></a><span data-ttu-id="6daf0-130">Основная сортировка по убыванию</span><span class="sxs-lookup"><span data-stu-id="6daf0-130">Primary Descending Sort</span></span>

<span data-ttu-id="6daf0-131">В следующем примере показано использование предложения `Order By Descending` в запросе LINQ для сортировки строк по их первой букве в порядке убывания.</span><span class="sxs-lookup"><span data-stu-id="6daf0-131">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' quick
' jumps
' fox
' brown
```

### <a name="secondary-sort-examples"></a><span data-ttu-id="6daf0-132">Примеры дополнительной сортировки</span><span class="sxs-lookup"><span data-stu-id="6daf0-132">Secondary Sort Examples</span></span>

#### <a name="secondary-ascending-sort"></a><span data-ttu-id="6daf0-133">Дополнительная сортировка по возрастанию</span><span class="sxs-lookup"><span data-stu-id="6daf0-133">Secondary Ascending Sort</span></span>

<span data-ttu-id="6daf0-134">В следующем примере показано использование предложения `Order By` в запросе LINQ для выполнения основной и дополнительной сортировки строк в массиве.</span><span class="sxs-lookup"><span data-stu-id="6daf0-134">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="6daf0-135">Строки сортируются основным образом по длине и дополнительно — по первой букве строки; в обоих случаях в возрастающем порядке.</span><span class="sxs-lookup"><span data-stu-id="6daf0-135">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1)
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' brown
' jumps
' quick
```

#### <a name="secondary-descending-sort"></a><span data-ttu-id="6daf0-136">Дополнительная сортировка по убыванию</span><span class="sxs-lookup"><span data-stu-id="6daf0-136">Secondary Descending Sort</span></span>

<span data-ttu-id="6daf0-137">В следующем примере показано использование предложения `Order By Descending` в запросе LINQ для выполнения основной сортировки по возрастанию и дополнительной сортировки по убыванию.</span><span class="sxs-lookup"><span data-stu-id="6daf0-137">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="6daf0-138">Строки сортируются основным образом по длине и дополнительно — по первой букве строки.</span><span class="sxs-lookup"><span data-stu-id="6daf0-138">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' quick
' jumps
' brown
```

## <a name="see-also"></a><span data-ttu-id="6daf0-139">См. также</span><span class="sxs-lookup"><span data-stu-id="6daf0-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="6daf0-140">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6daf0-140">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="6daf0-141">Предложение ORDER BY</span><span class="sxs-lookup"><span data-stu-id="6daf0-141">Order By Clause</span></span>](../../../language-reference/queries/order-by-clause.md)
- <span data-ttu-id="6daf0-142">[How to: Sort Query Results](../../language-features/linq/how-to-sort-query-results-by-using-linq.md) (Практическое руководство. Сортировка результатов запроса)</span><span class="sxs-lookup"><span data-stu-id="6daf0-142">[How to: Sort Query Results](../../language-features/linq/how-to-sort-query-results-by-using-linq.md)</span></span>
- [<span data-ttu-id="6daf0-143">Практическое руководство. Сортировка или фильтрация текстовых данных по любому слову или полю (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6daf0-143">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
