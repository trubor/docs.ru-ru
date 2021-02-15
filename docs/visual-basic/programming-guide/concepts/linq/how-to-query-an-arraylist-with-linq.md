---
description: Дополнительные сведения см. в статье как выполнять запросы к ArrayList с помощью LINQ (Visual Basic)
title: Практическое руководство. Выполнение запроса к ArrayList с помощью LINQ
ms.date: 07/20/2015
ms.assetid: 176358a9-d765-4b57-9557-7feb4428138d
ms.openlocfilehash: df7c6e1cee6d8e37074ce209f3bea97a402d8dbe
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428523"
---
# <a name="how-to-query-an-arraylist-with-linq-visual-basic"></a><span data-ttu-id="7f3dd-103">Как выполнить запрос к ArrayList с помощью LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f3dd-103">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>

<span data-ttu-id="7f3dd-104">При использовании LINQ для запросов к неуниверсальным коллекциям <xref:System.Collections.IEnumerable>, таким как <xref:System.Collections.ArrayList>, необходимо явно объявить тип переменной диапазона, чтобы отразить конкретный тип объектов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="7f3dd-104">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="7f3dd-105">Например, если у вас есть <xref:System.Collections.ArrayList> `Student` объекты, [предложение from](../../../language-reference/queries/from-clause.md) должно выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="7f3dd-105">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [From Clause](../../../language-reference/queries/from-clause.md) should look like this:</span></span>

```vb
Dim query = From student As Student In arrList
'...
```

<span data-ttu-id="7f3dd-106">Указав тип переменной диапазона, вы приводите каждый элемент в <xref:System.Collections.ArrayList> к `Student`.</span><span class="sxs-lookup"><span data-stu-id="7f3dd-106">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>

<span data-ttu-id="7f3dd-107">Использование явным образом типизированной переменной диапазона в выражении запроса эквивалентно вызову метода <xref:System.Linq.Enumerable.Cast%2A>.</span><span class="sxs-lookup"><span data-stu-id="7f3dd-107">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="7f3dd-108">Если выполнить приведение не удается, <xref:System.Linq.Enumerable.Cast%2A> создает исключение.</span><span class="sxs-lookup"><span data-stu-id="7f3dd-108"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="7f3dd-109">Методы <xref:System.Linq.Enumerable.Cast%2A> и <xref:System.Linq.Enumerable.OfType%2A> стандартного оператора запроса используются для работы с неуниверсальными типами <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="7f3dd-109"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="7f3dd-110">В Visual Basic необходимо явно вызвать <xref:System.Linq.Enumerable.Cast%2A> метод для источника данных, чтобы обеспечить конкретный тип переменной диапазона.</span><span class="sxs-lookup"><span data-stu-id="7f3dd-110">In Visual Basic, you must explicitly call the <xref:System.Linq.Enumerable.Cast%2A> method on the data source to ensure a specific range variable type.</span></span> <span data-ttu-id="7f3dd-111">Дополнительные сведения см. [в разделе связи типов в операциях запроса (Visual Basic)](type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="7f3dd-111">For more information, see [Type Relationships in Query Operations (Visual Basic)](type-relationships-in-query-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="7f3dd-112">Пример</span><span class="sxs-lookup"><span data-stu-id="7f3dd-112">Example</span></span>

<span data-ttu-id="7f3dd-113">В следующем примере показан простой запрос к объекту <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="7f3dd-113">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="7f3dd-114">Обратите внимание на то, что в этом примере инициализаторы объектов используются, когда код вызывает метод <xref:System.Collections.ArrayList.Add%2A>, но это не обязательно.</span><span class="sxs-lookup"><span data-stu-id="7f3dd-114">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>

```vb
Imports System.Collections
Imports System.Linq

Module Module1

    Public Class Student
        Public Property FirstName As String
        Public Property LastName As String
        Public Property Scores As Integer()
    End Class

    Sub Main()

        Dim student1 As New Student With {.FirstName = "Svetlana",
                                     .LastName = "Omelchenko",
                                     .Scores = New Integer() {98, 92, 81, 60}}
        Dim student2 As New Student With {.FirstName = "Claire",
                                    .LastName = "O'Donnell",
                                    .Scores = New Integer() {75, 84, 91, 39}}
        Dim student3 As New Student With {.FirstName = "Cesar",
                                    .LastName = "Garcia",
                                    .Scores = New Integer() {97, 89, 85, 82}}
        Dim student4 As New Student With {.FirstName = "Sven",
                                    .LastName = "Mortensen",
                                    .Scores = New Integer() {88, 94, 65, 91}}

        Dim arrList As New ArrayList()
        arrList.Add(student1)
        arrList.Add(student2)
        arrList.Add(student3)
        arrList.Add(student4)

        ' Use an explicit type for non-generic collections
        Dim query = From student As Student In arrList
                    Where student.Scores(0) > 95
                    Select student

        For Each student As Student In query
            Console.WriteLine(student.LastName & ": " & student.Scores(0))
        Next
        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Module
' Output:
'   Omelchenko: 98
'   Garcia: 97
```

## <a name="see-also"></a><span data-ttu-id="7f3dd-115">См. также</span><span class="sxs-lookup"><span data-stu-id="7f3dd-115">See also</span></span>

- [<span data-ttu-id="7f3dd-116">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f3dd-116">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
