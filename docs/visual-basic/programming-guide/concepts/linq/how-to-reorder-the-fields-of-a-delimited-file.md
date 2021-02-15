---
description: Дополнительные сведения о том, как изменить порядок полей файла с разделителями (LINQ) (Visual Basic).
title: Практическое руководство. Изменение порядка полей файла с разделителями (LINQ)
ms.date: 07/20/2015
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
ms.openlocfilehash: bfb06c396dbe33628ea146622c9c4ebe9534aae4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100435009"
---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a><span data-ttu-id="b02ee-103">Как изменить порядок полей файла с разделителями (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b02ee-103">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="b02ee-104">CSV-файл — это текстовый файл, который часто используется для хранения данных электронных таблиц или других табличных данных, представленных строками и столбцами.</span><span class="sxs-lookup"><span data-stu-id="b02ee-104">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="b02ee-105">Использование метода <xref:System.String.Split%2A> для разделения полей упрощает создание запросов к CSV-файлам и управление ими с помощью LINQ.</span><span class="sxs-lookup"><span data-stu-id="b02ee-105">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="b02ee-106">Фактически та же технология может использоваться для изменения порядка частей любой структурированной строки текста, а не только CSV-файлов.</span><span class="sxs-lookup"><span data-stu-id="b02ee-106">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>

<span data-ttu-id="b02ee-107">В следующем примере предполагается, что три столбца представляют "фамилию", "имя" и "идентификатор" учащихся.</span><span class="sxs-lookup"><span data-stu-id="b02ee-107">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="b02ee-108">Поля группируются в алфавитном порядке по фамилии учащихся.</span><span class="sxs-lookup"><span data-stu-id="b02ee-108">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="b02ee-109">Запрос создает новую последовательность, в которой столбец идентификатора отображается первым, за ним следует второй столбец, который объединяет имя и фамилию учащегося.</span><span class="sxs-lookup"><span data-stu-id="b02ee-109">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="b02ee-110">Порядок строк изменен в соответствии с полем идентификатора.</span><span class="sxs-lookup"><span data-stu-id="b02ee-110">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="b02ee-111">Результаты сохраняются в новый файл, и исходные данные не изменяются.</span><span class="sxs-lookup"><span data-stu-id="b02ee-111">The results are saved into a new file and the original data is not modified.</span></span>

### <a name="to-create-the-data-file"></a><span data-ttu-id="b02ee-112">Создание файла данных</span><span class="sxs-lookup"><span data-stu-id="b02ee-112">To create the data file</span></span>

1. <span data-ttu-id="b02ee-113">Скопируйте следующие строки в обычный текстовый файл с именем spreadsheet1.csv.</span><span class="sxs-lookup"><span data-stu-id="b02ee-113">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="b02ee-114">Сохраните файл в папке проекта.</span><span class="sxs-lookup"><span data-stu-id="b02ee-114">Save the file in your project folder.</span></span>

    ```csv
    Adams,Terry,120
    Fakhouri,Fadi,116
    Feng,Hanying,117
    Garcia,Cesar,114
    Garcia,Debra,115
    Garcia,Hugo,118
    Mortensen,Sven,113
    O'Donnell,Claire,112
    Omelchenko,Svetlana,111
    Tucker,Lance,119
    Tucker,Michael,122
    Zabokritski,Eugene,121
    ```

## <a name="example"></a><span data-ttu-id="b02ee-115">Пример</span><span class="sxs-lookup"><span data-stu-id="b02ee-115">Example</span></span>

```vb
Class CSVFiles

    Shared Sub Main()

        ' Create the IEnumerable data source.
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")

        ' Execute the query. Put field 2 first, then
        ' reverse and combine fields 0 and 1 from the old field
        Dim lineQuery = From line In lines
                        Let x = line.Split(New Char() {","})
                        Order By x(2)
                        Select x(2) & ", " & (x(1) & " " & x(0))

        ' Execute the query and write out the new file. Note that WriteAllLines
        ' takes a string array, so ToArray is called on the query.
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())

        ' Keep console window open in debug mode.
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")
        Console.ReadKey()
    End Sub
End Class
' Output to spreadsheet2.csv:
' 111, Svetlana Omelchenko
' 112, Claire O'Donnell
' 113, Sven Mortensen
' 114, Cesar Garcia
' 115, Debra Garcia
' 116, Fadi Fakhouri
' 117, Hanying Feng
' 118, Hugo Garcia
' 119, Lance Tucker
' 120, Terry Adams
' 121, Eugene Zabokritski
' 122, Michael Tucker
```

## <a name="see-also"></a><span data-ttu-id="b02ee-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b02ee-116">See also</span></span>

- [<span data-ttu-id="b02ee-117">LINQ и строки (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b02ee-117">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="b02ee-118">LINQ и каталоги файлов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b02ee-118">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
- [<span data-ttu-id="b02ee-119">Как создать XML из CSV-файлов</span><span class="sxs-lookup"><span data-stu-id="b02ee-119">How to: Generate XML from CSV Files</span></span>](../../../../standard/linq/generate-xml-csv-files.md)
