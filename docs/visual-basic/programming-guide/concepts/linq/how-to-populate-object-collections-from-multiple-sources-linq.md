---
description: Дополнительные сведения см. в статье как заполнить коллекции объектов из нескольких источников (LINQ) (Visual Basic)
title: Практическое руководство. Заполнение коллекций объектов из нескольких источников (LINQ)
ms.date: 06/22/2018
ms.assetid: 63062a22-e6a9-42c0-b357-c7c965f58f33
ms.openlocfilehash: a1a02382efb31895edb880d2137f08d79dc4e97b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477558"
---
# <a name="how-to-populate-object-collections-from-multiple-sources-linq-visual-basic"></a><span data-ttu-id="6192f-103">Как заполнить коллекции объектов из нескольких источников (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6192f-103">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="6192f-104">В этом примере показано, как объединить данные из разных источников в последовательность новых типов.</span><span class="sxs-lookup"><span data-stu-id="6192f-104">This example shows how to merge data from different sources into a sequence of new types.</span></span>

> [!NOTE]
> <span data-ttu-id="6192f-105">Не пытайтесь объединить данные в памяти или данные в файловой системе с данными, которые остаются в базе данных.</span><span class="sxs-lookup"><span data-stu-id="6192f-105">Don't try to join in-memory data or data in the file system with data that is still in a database.</span></span> <span data-ttu-id="6192f-106">Такие междоменные соединения могут повлечь за собой непредвиденные результаты из-за разных способов, с помощью которых операции соединения могут определяться для запросов к базам данных и другим типам источников.</span><span class="sxs-lookup"><span data-stu-id="6192f-106">Such cross-domain joins can yield undefined results because of different ways in which join operations might be defined for database queries and other types of sources.</span></span> <span data-ttu-id="6192f-107">Кроме того, существует риск, что такая операция может вызвать исключение нехватки памяти, если объем данных в базе данных достаточно большой.</span><span class="sxs-lookup"><span data-stu-id="6192f-107">Additionally, there is a risk that such an operation could cause an out-of-memory exception if the amount of data in the database is large enough.</span></span> <span data-ttu-id="6192f-108">Чтобы объединить данные из базы данных с данными в памяти, сначала вызовите `ToList` или `ToArray` для запроса к базе данных, а затем выполните присоединение для возвращенной коллекции.</span><span class="sxs-lookup"><span data-stu-id="6192f-108">To join data from a database to in-memory data, first call `ToList` or `ToArray` on the database query, and then perform the join on the returned collection.</span></span>

## <a name="to-create-the-data-file"></a><span data-ttu-id="6192f-109">Создание файла данных</span><span class="sxs-lookup"><span data-stu-id="6192f-109">To create the data file</span></span>

- <span data-ttu-id="6192f-110">Скопируйте файлы names.csv и scores.csv в папку проекта, как описано в разделе [как присоединиться к содержимому из разнородных файлов (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md).</span><span class="sxs-lookup"><span data-stu-id="6192f-110">Copy the names.csv and scores.csv files into your project folder, as described in [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="6192f-111">Пример</span><span class="sxs-lookup"><span data-stu-id="6192f-111">Example</span></span>

<span data-ttu-id="6192f-112">Следующий пример демонстрирует использование именованного типа `Student` для хранения объединенных данных из двух коллекций строк в памяти, которые имитируют данные электронной таблицы в формате CSV.</span><span class="sxs-lookup"><span data-stu-id="6192f-112">The following example shows how to use a named type `Student` to store merged data from two in-memory collections of strings that simulate spreadsheet data in .csv format.</span></span> <span data-ttu-id="6192f-113">Первая коллекция строк представляет имена и идентификаторы учащихся, а вторая коллекция — идентификатор учащегося (в первом столбце) и результаты четырех экзаменов.</span><span class="sxs-lookup"><span data-stu-id="6192f-113">The first collection of strings represents the student names and IDs, and the second collection represents the student ID (in the first column) and four exam scores.</span></span> <span data-ttu-id="6192f-114">Идентификатор используется в качестве внешнего ключа.</span><span class="sxs-lookup"><span data-stu-id="6192f-114">The ID is used as the foreign key.</span></span>

```vb
Imports System.Collections.Generic
Imports System.Linq

Class Student
    Public FirstName As String
    Public LastName As String
    Public ID As Integer
    Public ExamScores As List(Of Integer)
End Class

Class PopulateCollection

    Shared Sub Main()

        ' Merge content from spreadsheets into a list of Student objects.

        ' These data files are defined in How to: Join Content from
        ' Dissimilar Files (LINQ).

        ' Each line of names.csv consists of a last name, a first name, and an
        ' ID number, separated by commas. For example, Omelchenko,Svetlana,111
        Dim names As String() = System.IO.File.ReadAllLines("../../../names.csv")

        ' Each line of scores.csv consists of an ID number and four test
        ' scores, separated by commas. For example, 111, 97, 92, 81, 60
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' The following query merges the content of two dissimilar spreadsheets
        ' based on common ID values.
        ' Multiple From clauses are used instead of a Join clause
        ' in order to store the results of scoreLine.Split.
        ' Note the dynamic creation of a list of integers for the
        ' ExamScores member. The first item is skipped in the split string
        ' because it is the student ID, not an exam score.
        Dim queryNamesScores = From nameLine In names
                          Let splitName = nameLine.Split(New Char() {","})
                          From scoreLine In scores
                          Let splitScoreLine = scoreLine.Split(New Char() {","})
                          Where Convert.ToInt32(splitName(2)) = Convert.ToInt32(splitScoreLine(0))
                          Select New Student() With {
                               .FirstName = splitName(1), .LastName = splitName(0), .ID = splitName(2),
                               .ExamScores = (From scoreAsText In splitScoreLine Skip 1
                                             Select Convert.ToInt32(scoreAsText)).ToList()}

        ' Optional. Store the query results for faster access in future
        ' queries. This could be useful with very large data files.
        Dim students As List(Of Student) = queryNamesScores.ToList()

        ' Display each student's name and exam score average.
        For Each s In students
            Console.WriteLine("The average score of " & s.FirstName & " " &
                              s.LastName & " is " & s.ExamScores.Average())
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class

' Output:
' The average score of Svetlana Omelchenko is 82.5
' The average score of Claire O'Donnell is 72.25
' The average score of Sven Mortensen is 84.5
' The average score of Cesar Garcia is 88.25
' The average score of Debra Garcia is 67
' The average score of Fadi Fakhouri is 92.25
' The average score of Hanying Feng is 88
' The average score of Hugo Garcia is 85.75
' The average score of Lance Tucker is 81.75
' The average score of Terry Adams is 85.25
' The average score of Eugene Zabokritski is 83
' The average score of Michael Tucker is 92
```

<span data-ttu-id="6192f-115">В предложении [предложения SELECT](../../../language-reference/queries/select-clause.md) инициализатор объекта используется для создания экземпляра каждого нового `Student` объекта с использованием данных из двух источников.</span><span class="sxs-lookup"><span data-stu-id="6192f-115">In the [Select Clause](../../../language-reference/queries/select-clause.md) clause, an object initializer is used to instantiate each new `Student` object by using the data from the two sources.</span></span>

<span data-ttu-id="6192f-116">Если не требуется хранить результаты запроса, анонимные типы могут быть более удобными, чем именованные типы.</span><span class="sxs-lookup"><span data-stu-id="6192f-116">If you don't have to store the results of a query, anonymous types can be more convenient than named types.</span></span> <span data-ttu-id="6192f-117">Именованные типы необходимы, если результаты запроса передаются за пределы метода, в котором выполняется запрос.</span><span class="sxs-lookup"><span data-stu-id="6192f-117">Named types are required if you pass the query results outside the method in which the query is executed.</span></span> <span data-ttu-id="6192f-118">Следующий пример кода выполняет ту же задачу, что и в предыдущем примере, но использует анонимные типы вместо именованных типов:</span><span class="sxs-lookup"><span data-stu-id="6192f-118">The following example performs the same task as the previous example, but uses anonymous types instead of named types:</span></span>

```vb
' Merge the data by using an anonymous type.
' Note the dynamic creation of a list of integers for the
' ExamScores member. We skip 1 because the first string
' in the array is the student ID, not an exam score.
Dim queryNamesScores2 =
    From nameLine In names
    Let splitName = nameLine.Split(New Char() {","})
    From scoreLine In scores
    Let splitScoreLine = scoreLine.Split(New Char() {","})
    Where Convert.ToInt32(splitName(2)) = Convert.ToInt32(splitScoreLine(0))
    Select New With
           {.Last = splitName(0),
            .First = splitName(1),
            .ExamScores = (From scoreAsText In splitScoreLine Skip 1
                           Select Convert.ToInt32(scoreAsText)).ToList()}

' Display each student's name and exam score average.
For Each s In queryNamesScores2
    Console.WriteLine("The average score of " & s.First & " " &
                      s.Last & " is " & s.ExamScores.Average())
Next
```

## <a name="see-also"></a><span data-ttu-id="6192f-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6192f-119">See also</span></span>

- [<span data-ttu-id="6192f-120">LINQ и строки (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6192f-120">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
