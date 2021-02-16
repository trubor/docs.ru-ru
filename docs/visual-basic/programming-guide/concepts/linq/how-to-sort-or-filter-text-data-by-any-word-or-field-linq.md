---
description: Дополнительные сведения см. в статье как сортировать или фильтровать текстовые данные по любому слову или полю (LINQ) (Visual Basic)
title: Практическое руководство. Сортировка или фильтрация текстовых данных по любому слову или полю (LINQ)
ms.date: 07/20/2015
ms.assetid: 9df137fe-335b-46e0-aecf-ea8a9eddd4e3
ms.openlocfilehash: 49fff8df58b41acf7c8a63b94e8d1c85eefec8ab
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434931"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-visual-basic"></a><span data-ttu-id="0a2ad-103">Практическое руководство. Сортировка или фильтрация текстовых данных по любому слову или полю (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a2ad-103">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="0a2ad-104">В следующем примере демонстрируется сортировка строк структурированного текста, таких как значения, разделенные запятыми, по любому полю в строке.</span><span class="sxs-lookup"><span data-stu-id="0a2ad-104">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="0a2ad-105">Поле можно указывать в среде выполнения динамически.</span><span class="sxs-lookup"><span data-stu-id="0a2ad-105">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="0a2ad-106">Допустим, поля в файле scores.csv содержат идентификационные номера учащихся и баллы, которые они набрали в результате четырех тестов.</span><span class="sxs-lookup"><span data-stu-id="0a2ad-106">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>

### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="0a2ad-107">Создание файла с данными</span><span class="sxs-lookup"><span data-stu-id="0a2ad-107">To create a file that contains data</span></span>

<span data-ttu-id="0a2ad-108">Скопируйте scores.csv данные из раздела [как присоединиться к содержимому из разных файлов (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md) и сохранить его в папке решения.</span><span class="sxs-lookup"><span data-stu-id="0a2ad-108">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>

## <a name="example"></a><span data-ttu-id="0a2ad-109">Пример</span><span class="sxs-lookup"><span data-stu-id="0a2ad-109">Example</span></span>

```vb
Class SortLines

    Shared Sub Main()
        Dim scores As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' Change this to any value from 0 to 4
        Dim sortField As Integer = 1

        Console.WriteLine("Sorted highest to lowest by field " & sortField)

        ' Demonstrates how to return query from a method.
        ' The query is executed here.
        For Each str As String In SortQuery(scores, sortField)
            Console.WriteLine(str)
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()

    End Sub

    Shared Function SortQuery(
        ByVal source As IEnumerable(Of String),
        ByVal num As Integer) As IEnumerable(Of String)

        Dim scoreQuery = From line In source
                         Let fields = line.Split(New Char() {","})
                         Order By fields(num) Descending
                         Select line

        Return scoreQuery
    End Function
End Class
' Output:
' Sorted highest to lowest by field 1
' 116, 99, 86, 90, 94
' 120, 99, 82, 81, 79
' 111, 97, 92, 81, 60
' 114, 97, 89, 85, 82
' 121, 96, 85, 91, 60
' 122, 94, 92, 91, 91
' 117, 93, 92, 80, 87
' 118, 92, 90, 83, 78
' 113, 88, 94, 65, 91
' 112, 75, 84, 91, 39
' 119, 68, 79, 88, 92
' 115, 35, 72, 91, 70
```

<span data-ttu-id="0a2ad-110">В этом примере также показано, как вернуть переменную запроса из функции.</span><span class="sxs-lookup"><span data-stu-id="0a2ad-110">This example also demonstrates how to return a query variable from a Function.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="0a2ad-111">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="0a2ad-111">Compile the code</span></span>

<span data-ttu-id="0a2ad-112">Создайте проект консольного приложения Visual Basic с `Imports` инструкцией для пространства имен System. LINQ.</span><span class="sxs-lookup"><span data-stu-id="0a2ad-112">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a2ad-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0a2ad-113">See also</span></span>

- [<span data-ttu-id="0a2ad-114">LINQ и строки (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a2ad-114">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
