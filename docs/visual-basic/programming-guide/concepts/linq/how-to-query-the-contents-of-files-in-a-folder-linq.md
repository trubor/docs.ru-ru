---
description: Дополнительные сведения о том, как запрашивать содержимое файлов в папке (LINQ) (Visual Basic).
title: Практическое руководство. Запрос содержимого файлов в папке (LINQ)
ms.date: 07/20/2015
ms.assetid: edacbcd3-f3e4-4429-a8be-28a58dc0dd70
ms.openlocfilehash: 5043f64a0bb38811b6155394b18a88f702515cc5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434996"
---
# <a name="how-to-query-the-contents-of-files-in-a-folder-linq-visual-basic"></a><span data-ttu-id="48ef1-103">Запрос содержимого файлов в папке (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48ef1-103">How to query the contents of files in a folder (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="48ef1-104">В этом примере показано, как запросить все файлы в указанном дереве каталогов, открыть каждый файл и проверить его содержимое.</span><span class="sxs-lookup"><span data-stu-id="48ef1-104">This example shows how to query over all the files in a specified directory tree, open each file, and inspect its contents.</span></span> <span data-ttu-id="48ef1-105">Этот способ позволяет создать индексы для содержимого дерева каталогов или обратить их порядок.</span><span class="sxs-lookup"><span data-stu-id="48ef1-105">This type of technique could be used to create indexes or reverse indexes of the contents of a directory tree.</span></span> <span data-ttu-id="48ef1-106">В этом примере выполняется простой поиск строки.</span><span class="sxs-lookup"><span data-stu-id="48ef1-106">A simple string search is performed in this example.</span></span> <span data-ttu-id="48ef1-107">Более сложные типы сопоставления шаблонов можно выполнять с помощью регулярных выражений.</span><span class="sxs-lookup"><span data-stu-id="48ef1-107">However, more complex types of pattern matching can be performed with a regular expression.</span></span> <span data-ttu-id="48ef1-108">Дополнительные сведения см. [в разделе Практические руководства. Объединение запросов LINQ с помощью регулярных выражений (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="48ef1-108">For more information, see [How to: Combine LINQ Queries with Regular Expressions (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48ef1-109">Пример</span><span class="sxs-lookup"><span data-stu-id="48ef1-109">Example</span></span>  
  
```vb
Imports System.IO

Module Module1  
    'QueryContents  
    Public Sub Main()  
  
        ' Modify this path as necessary.  
        Dim startFolder = "C:\Program Files (x86)\Microsoft Visual Studio 14.0"  

        ' Take a snapshot of the folder contents.
        Dim dir As New DirectoryInfo(startFolder)
        Dim fileList = dir.GetFiles("*.*", SearchOption.AllDirectories)

        Dim searchTerm = "Welcome"

        ' Search the contents of each file.
        ' A regular expression created with the RegEx class
        ' could be used instead of the Contains method.
        Dim queryMatchingFiles = From file In fileList _
                                 Where file.Extension = ".html" _
                                 Let fileText = GetFileText(file.FullName) _
                                 Where fileText.Contains(searchTerm) _
                                 Select file.FullName

        Console.WriteLine("The term " & searchTerm & " was found in:")

        ' Execute the query.
        For Each filename In queryMatchingFiles
            Console.WriteLine(filename)
        Next

        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit")
        Console.ReadKey()

    End Sub

    ' Read the contents of the file. This is done in a separate
    ' function in order to handle potential file system errors.
    Function GetFileText(name As String) As String

        ' If the file has been deleted, the right thing
        ' to do in this case is return an empty string.
        Dim fileContents = String.Empty

        ' If the file has been deleted since we took
        ' the snapshot, ignore it and return the empty string.
        If File.Exists(name) Then
            fileContents = File.ReadAllText(name)
        End If

        Return fileContents

    End Function
End Module
```

## <a name="compile-the-code"></a><span data-ttu-id="48ef1-110">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="48ef1-110">Compile the code</span></span>

<span data-ttu-id="48ef1-111">Создайте Visual Basic проект консольного приложения, скопируйте и вставьте пример кода и измените значение объекта Startup в свойствах проекта.</span><span class="sxs-lookup"><span data-stu-id="48ef1-111">Create a Visual Basic console application project, copy and paste the code sample, and adjust the Startup object value in the project properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="48ef1-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="48ef1-112">See also</span></span>

- [<span data-ttu-id="48ef1-113">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48ef1-113">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="48ef1-114">LINQ и каталоги файлов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48ef1-114">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
