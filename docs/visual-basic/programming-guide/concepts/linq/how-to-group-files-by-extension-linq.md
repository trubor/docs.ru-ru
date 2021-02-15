---
description: Дополнительные сведения см. в статье как группировать файлы по расширению (LINQ) (Visual Basic).
title: Практическое руководство. Группировка файлов по расширению (LINQ)
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: 6736b4ff99d88f8e5b2b40aeb670d88589db02b1
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472999"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a><span data-ttu-id="7cc51-103">Пошаговое руководство. Группировка файлов по расширению (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7cc51-103">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="7cc51-104">В этом примере показано, как можно использовать LINQ для выполнения расширенного группирования и сортировки списков файлов или папок.</span><span class="sxs-lookup"><span data-stu-id="7cc51-104">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="7cc51-105">Кроме того, здесь показывается, как разбить на страницы выходные данные в окне консоли с помощью методов <xref:System.Linq.Enumerable.Skip%2A> и <xref:System.Linq.Enumerable.Take%2A>.</span><span class="sxs-lookup"><span data-stu-id="7cc51-105">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cc51-106">Пример</span><span class="sxs-lookup"><span data-stu-id="7cc51-106">Example</span></span>  

 <span data-ttu-id="7cc51-107">Следующий запрос демонстрирует группирование содержимого указанного дерева каталогов по расширению файла.</span><span class="sxs-lookup"><span data-stu-id="7cc51-107">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```vb  
Module GroupByExtension  
    Public Sub Main()  
  
        ' Root folder to query, along with all subfolders.  
        Dim startFolder As String = "C:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        ' Used in WriteLine() to skip over startfolder in output lines.  
        Dim rootLength As Integer = startFolder.Length  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the query.  
        Dim queryGroupByExt = From file In fileList _  
                          Group By file.Extension.ToLower() Into fileGroup = Group _  
                          Order By ToLower _  
                          Select fileGroup  
  
        ' Execute the query. By storing the result we can  
        ' page the display with good performance.  
        Dim groupByExtList = queryGroupByExt.ToList()  
  
        ' Display one group at a time. If the number of
        ' entries is greater than the number of lines  
        ' in the console window, then page the output.  
        Dim trimLength = startFolder.Length  
        PageOutput(groupByExtList, trimLength)  
  
    End Sub  
  
    ' Pages console display for large query results. No more than one group per page.  
    ' This sub specifically works with group queries of FileInfo objects  
    ' but can be modified for any type.  
    Sub PageOutput(ByVal groupQuery, ByVal charsToSkip)  
  
        ' "3" = 1 line for extension key + 1 for "Press any key" + 1 for input cursor.  
        Dim numLines As Integer = Console.WindowHeight - 3  
        ' Flag to indicate whether there are more results to display  
        Dim goAgain As Boolean = True  
  
        For Each fg As IEnumerable(Of System.IO.FileInfo) In groupQuery  
            ' Start a new extension at the top of a page.  
            Dim currentLine As Integer = 0  
  
            Do While (currentLine < fg.Count())  
                Console.Clear()  
                Console.WriteLine(fg(0).Extension)  
  
                ' Get the next page of results  
                ' No more than one filename per page  
                Dim resultPage = From file In fg _  
                                Skip currentLine Take numLines  
  
                ' Execute the query. Trim the display output.  
                For Each line In resultPage  
                    Console.WriteLine(vbTab & line.FullName.Substring(charsToSkip))  
                Next  
  
                ' Advance the current position  
                currentLine = numLines + currentLine  
  
                ' Give the user a chance to break out of the loop  
                Console.WriteLine("Press any key for next page or the 'End' key to exit.")  
                Dim key As ConsoleKey = Console.ReadKey().Key  
                If key = ConsoleKey.End Then  
                    goAgain = False  
                    Exit For  
                End If  
            Loop  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7cc51-108">Вывод этой программы может быть длинным в зависимости от объема данных локальной файловой системы и значения `startFolder`.</span><span class="sxs-lookup"><span data-stu-id="7cc51-108">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="7cc51-109">В этом примере демонстрируется постраничный просмотр, который позволяет просматривать все результаты.</span><span class="sxs-lookup"><span data-stu-id="7cc51-109">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="7cc51-110">Те же методы могут применяться для приложений Windows и веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="7cc51-110">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="7cc51-111">Обратите внимание, что поскольку код разбивает элементы в группе на страницы, требуется вложенный цикл `For Each`.</span><span class="sxs-lookup"><span data-stu-id="7cc51-111">Notice that because the code pages the items in a group, a nested `For Each` loop is required.</span></span> <span data-ttu-id="7cc51-112">Также существует некоторая дополнительная логика для вычисления текущей позиции в списке и предоставления пользователю возможности остановить разбиение по страницам и выйти из программы.</span><span class="sxs-lookup"><span data-stu-id="7cc51-112">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="7cc51-113">В данном конкретном случае запрос разбиения на страницы выполняется для кэшированных результатов исходного запроса.</span><span class="sxs-lookup"><span data-stu-id="7cc51-113">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="7cc51-114">В других контекстах, например LINQ to SQL, подобное кэширование не требуется.</span><span class="sxs-lookup"><span data-stu-id="7cc51-114">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="7cc51-115">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="7cc51-115">Compile the code</span></span>  

<span data-ttu-id="7cc51-116">Создайте проект консольного приложения Visual Basic с `Imports` инструкцией для пространства имен System. LINQ.</span><span class="sxs-lookup"><span data-stu-id="7cc51-116">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7cc51-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7cc51-117">See also</span></span>

- [<span data-ttu-id="7cc51-118">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7cc51-118">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="7cc51-119">LINQ и каталоги файлов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7cc51-119">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
