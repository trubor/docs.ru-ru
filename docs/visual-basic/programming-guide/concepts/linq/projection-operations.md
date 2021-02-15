---
description: 'Дополнительные сведения: проекция операций (Visual Basic)'
title: Операции проецирования
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: 5531bec915f3a9ee521e0d67941b8f1d49e90524
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466462"
---
# <a name="projection-operations-visual-basic"></a><span data-ttu-id="f6340-103">Операции проекции (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6340-103">Projection Operations (Visual Basic)</span></span>

<span data-ttu-id="f6340-104">Проекцией называют операцию преобразования объекта в новую форму, которая часто состоит только из тех его свойств, которые будут использоваться впоследствии.</span><span class="sxs-lookup"><span data-stu-id="f6340-104">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="f6340-105">С помощью проекции можно создать новый тип, построенный из каждого объекта.</span><span class="sxs-lookup"><span data-stu-id="f6340-105">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="f6340-106">Вы можете проецировать свойство и выполнять над ним математические функции.</span><span class="sxs-lookup"><span data-stu-id="f6340-106">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="f6340-107">Также можно проецировать исходный объект, не изменяя его.</span><span class="sxs-lookup"><span data-stu-id="f6340-107">You can also project the original object without changing it.</span></span>

<span data-ttu-id="f6340-108">Методы стандартных операторов запросов, которые выполняют проецирование, перечислены в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="f6340-108">The standard query operator methods that perform projection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="f6340-109">Методы</span><span class="sxs-lookup"><span data-stu-id="f6340-109">Methods</span></span>

|<span data-ttu-id="f6340-110">Имя метода</span><span class="sxs-lookup"><span data-stu-id="f6340-110">Method Name</span></span>|<span data-ttu-id="f6340-111">Описание</span><span class="sxs-lookup"><span data-stu-id="f6340-111">Description</span></span>|<span data-ttu-id="f6340-112">Синтаксис выражения запроса Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6340-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="f6340-113">Дополнительные сведения</span><span class="sxs-lookup"><span data-stu-id="f6340-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="f6340-114">Выбрать</span><span class="sxs-lookup"><span data-stu-id="f6340-114">Select</span></span>|<span data-ttu-id="f6340-115">Проецирует значения, основанные на функции преобразования.</span><span class="sxs-lookup"><span data-stu-id="f6340-115">Projects values that are based on a transform function.</span></span>|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|
|<span data-ttu-id="f6340-116">SelectMany</span><span class="sxs-lookup"><span data-stu-id="f6340-116">SelectMany</span></span>|<span data-ttu-id="f6340-117">Проецирует последовательности значений, основанных на функции преобразования, а затем выравнивает их в одну последовательность.</span><span class="sxs-lookup"><span data-stu-id="f6340-117">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="f6340-118">Использование нескольких предложений `From`</span><span class="sxs-lookup"><span data-stu-id="f6340-118">Use multiple `From` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="f6340-119">Примеры синтаксиса выражений запросов</span><span class="sxs-lookup"><span data-stu-id="f6340-119">Query Expression Syntax Examples</span></span>

### <a name="select"></a><span data-ttu-id="f6340-120">Выбрать</span><span class="sxs-lookup"><span data-stu-id="f6340-120">Select</span></span>

<span data-ttu-id="f6340-121">В приведенном ниже примере предложение `Select` используется для проецирования первой буквы из каждой строки в списке строк.</span><span class="sxs-lookup"><span data-stu-id="f6340-121">The following example uses the `Select` clause to project the first letter from each string in a list of strings.</span></span>

```vb
Dim words = New List(Of String) From {"an", "apple", "a", "day"}

Dim query = From word In words
            Select word.Substring(0, 1)

Dim sb As New System.Text.StringBuilder()
For Each letter As String In query
    sb.AppendLine(letter)
Next

' Display the output.
MsgBox(sb.ToString())

' This code produces the following output:

' a
' a
' a
' d
```

### <a name="selectmany"></a><span data-ttu-id="f6340-122">SelectMany</span><span class="sxs-lookup"><span data-stu-id="f6340-122">SelectMany</span></span>

<span data-ttu-id="f6340-123">В следующем примере используется несколько `From` предложений для проецирования каждого слова из каждой строки в списке строк.</span><span class="sxs-lookup"><span data-stu-id="f6340-123">The following example uses multiple `From` clauses to project each word from each string in a list of strings.</span></span>

```vb
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}

Dim query = From phrase In phrases
            From word In phrase.Split(" "c)
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the output.
MsgBox(sb.ToString())

' This code produces the following output:

' an
' apple
' a
' day
' the
' quick
' brown
' fox
```

## <a name="select-versus-selectmany"></a><span data-ttu-id="f6340-124">Select или SelectMany</span><span class="sxs-lookup"><span data-stu-id="f6340-124">Select versus SelectMany</span></span>

<span data-ttu-id="f6340-125">Задача обоих методов `Select()` и `SelectMany()` заключается в создании результирующего значения (или значений) из исходных значений.</span><span class="sxs-lookup"><span data-stu-id="f6340-125">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="f6340-126">`Select()` создает один результат для каждого исходного значения.</span><span class="sxs-lookup"><span data-stu-id="f6340-126">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="f6340-127">Таким образом, общий результат является коллекцией, имеющей то же количество элементов, что и исходная коллекция.</span><span class="sxs-lookup"><span data-stu-id="f6340-127">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="f6340-128">`SelectMany()`, напротив, создает общий результат, содержащий соединенные подколлекции из каждого исходного значения.</span><span class="sxs-lookup"><span data-stu-id="f6340-128">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="f6340-129">Функция преобразования, которая передается в качестве аргумента методу `SelectMany()`, должна возвращать перечисляемую последовательность значений для каждого исходного значения.</span><span class="sxs-lookup"><span data-stu-id="f6340-129">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="f6340-130">Эти перечисляемые последовательности затем объединяются `SelectMany()` для создания одной большой последовательности.</span><span class="sxs-lookup"><span data-stu-id="f6340-130">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>

<span data-ttu-id="f6340-131">На двух рисунках, приведенных ниже, показаны принципиальные различия между работой этих двух методов.</span><span class="sxs-lookup"><span data-stu-id="f6340-131">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="f6340-132">В обоих случаях предполагается, что функция выбора (преобразования) выбирает массив цветов из каждого исходного значения.</span><span class="sxs-lookup"><span data-stu-id="f6340-132">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>

<span data-ttu-id="f6340-133">На этом рисунке представлено, как `Select()` возвращает коллекцию, которая имеет то же количество элементов, что и исходная коллекция.</span><span class="sxs-lookup"><span data-stu-id="f6340-133">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>

![График, отображающий действие Select&#40;&#41;](./media/projection-operations/select-action-graphic.png)

<span data-ttu-id="f6340-135">На этом рисунке показано, как `SelectMany()` объединяет промежуточные последовательности массивов в один конечный результат, содержащий все значения из промежуточных массивов.</span><span class="sxs-lookup"><span data-stu-id="f6340-135">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>

![График, отображающий действие SelectMany&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )

### <a name="code-example"></a><span data-ttu-id="f6340-137">Пример кода</span><span class="sxs-lookup"><span data-stu-id="f6340-137">Code Example</span></span>

<span data-ttu-id="f6340-138">В приведенном ниже примере сравнивается действие `Select()` и `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="f6340-138">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="f6340-139">Код создает "букет" из цветов путем получения первых двух элементов из каждого списка названий цветов в исходной коллекции.</span><span class="sxs-lookup"><span data-stu-id="f6340-139">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="f6340-140">В этом примере отдельное значение, используемое функцией преобразования <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>, представляет собой коллекцию значений.</span><span class="sxs-lookup"><span data-stu-id="f6340-140">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="f6340-141">Этот требует дополнительного цикла `For Each` для перечисления каждой строки в каждой подпоследовательности.</span><span class="sxs-lookup"><span data-stu-id="f6340-141">This requires the extra `For Each` loop in order to enumerate each string in each sub-sequence.</span></span>

```vb
Class Bouquet
    Public Flowers As List(Of String)
End Class

Sub SelectVsSelectMany()
    Dim bouquets = New List(Of Bouquet) From {
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}

    Dim output As New System.Text.StringBuilder

    ' Select()
    Dim query1 = bouquets.Select(Function(b) b.Flowers)

    output.AppendLine("Using Select():")
    For Each flowerList In query1
        For Each str As String In flowerList
            output.AppendLine(str)
        Next
    Next

    ' SelectMany()
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)

    output.AppendLine(vbCrLf & "Using SelectMany():")
    For Each str As String In query2
        output.AppendLine(str)
    Next

    ' Display the output
    MsgBox(output.ToString())

    ' This code produces the following output:
    '
    ' Using Select():
    ' sunflower
    ' daisy
    ' daffodil
    ' larkspur
    ' tulip
    ' rose
    ' orchid
    ' gladiolis
    ' lily
    ' snapdragon
    ' aster
    ' protea
    ' larkspur
    ' lilac
    ' iris
    ' dahlia

    ' Using SelectMany()
    ' sunflower
    ' daisy
    ' daffodil
    ' larkspur
    ' tulip
    ' rose
    ' orchid
    ' gladiolis
    ' lily
    ' snapdragon
    ' aster
    ' protea
    ' larkspur
    ' lilac
    ' iris
    ' dahlia

End Sub
```

## <a name="see-also"></a><span data-ttu-id="f6340-142">См. также</span><span class="sxs-lookup"><span data-stu-id="f6340-142">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="f6340-143">Общие сведения о стандартных операторах запроса (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6340-143">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="f6340-144">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="f6340-144">Select Clause</span></span>](../../../language-reference/queries/select-clause.md)
- <span data-ttu-id="f6340-145">[How to: Combine Data with Joins](../../language-features/linq/how-to-combine-data-with-linq-by-using-joins.md) (Практическое руководство. Объединение данных с помощью соединений)</span><span class="sxs-lookup"><span data-stu-id="f6340-145">[How to: Combine Data with Joins](../../language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)</span></span>
- [<span data-ttu-id="f6340-146">Как заполнить коллекции объектов из нескольких источников (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6340-146">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="f6340-147">Практическое руководство. Возвращение результата запроса LINQ в виде определенного типа</span><span class="sxs-lookup"><span data-stu-id="f6340-147">How to: Return a LINQ Query Result as a Specific Type</span></span>](../../language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)
- [<span data-ttu-id="f6340-148">Инструкции. Разбиение файла на несколько файлов с помощью групп (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6340-148">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
