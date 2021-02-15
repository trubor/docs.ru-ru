---
description: Дополнительные сведения см. в статье как запросить самый крупный файл или файлы в дереве каталогов (LINQ) (Visual Basic)
title: Практическое руководство. Запрос самого большого файла или файлов в дереве папок (LINQ)
ms.date: 07/20/2015
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
ms.openlocfilehash: 5ceebd94ed74f9df05ad8f610d1cc79d6eb45b83
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100435074"
---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a><span data-ttu-id="0ebd9-103">Практическое руководство. Запрос самого большого файла или файлов в дереве папок (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ebd9-103">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="0ebd9-104">В этом примере показано пять запросов, связанных с размером файла в байтах.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-104">This example shows five queries related to file size in bytes:</span></span>  
  
- <span data-ttu-id="0ebd9-105">Извлечение размера в байтах наибольшего файла.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-105">How to retrieve the size in bytes of the largest file.</span></span>  
  
- <span data-ttu-id="0ebd9-106">Извлечение размера в байтах наименьшего файла.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-106">How to retrieve the size in bytes of the smallest file.</span></span>  
  
- <span data-ttu-id="0ebd9-107">Извлечение объекта <xref:System.IO.FileInfo> наибольшего или наименьшего файла из одной или нескольких папок в указанной корневой папке.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-107">How to retrieve the <xref:System.IO.FileInfo> object largest or smallest file from one or more folders under a specified root folder.</span></span>  
  
- <span data-ttu-id="0ebd9-108">Извлечение последовательности, например 10 наибольших файлов.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-108">How to retrieve a sequence such as the 10 largest files.</span></span>  
  
- <span data-ttu-id="0ebd9-109">Упорядочение файлов в группы на основании их размера в байтах, игнорируя файлы меньше заданного размера.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-109">How to order files into groups based on their file size in bytes, ignoring files that are less than a specified size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ebd9-110">Пример</span><span class="sxs-lookup"><span data-stu-id="0ebd9-110">Example</span></span>  

 <span data-ttu-id="0ebd9-111">Следующий пример содержит пять отдельных запросов, которые показывают, как запрашивать и группировать файлы на основании их размера в байтах.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-111">The following example contains five separate queries that show how to query and group files, depending on their file size in bytes.</span></span> <span data-ttu-id="0ebd9-112">Эти примеры можно легко изменить, чтобы создать запрос на основании других свойств объекта <xref:System.IO.FileInfo>.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-112">You can easily modify these examples to base the query on some other property of the <xref:System.IO.FileInfo> object.</span></span>  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="0ebd9-113">Чтобы вернуть один или несколько полных объектов <xref:System.IO.FileInfo>, запрос должен сначала проверить каждый из них в источнике данных, а затем отсортировать их по значению свойства Length.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-113">To return one or more complete <xref:System.IO.FileInfo> objects, the query first must examine each one in the data source, and then sort them by the value of their Length property.</span></span> <span data-ttu-id="0ebd9-114">Затем он может вернуть один объект или последовательность объектов с максимальной длиной.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-114">Then it can return the single one or the sequence with the greatest lengths.</span></span> <span data-ttu-id="0ebd9-115"><xref:System.Linq.Enumerable.First%2A> возвращает первый элемент в списке.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-115">Use <xref:System.Linq.Enumerable.First%2A> to return the first element in a list.</span></span> <span data-ttu-id="0ebd9-116"><xref:System.Linq.Enumerable.Take%2A> возвращает первые n элементов.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-116">Use <xref:System.Linq.Enumerable.Take%2A> to return the first n number of elements.</span></span> <span data-ttu-id="0ebd9-117">Укажите порядок сортировки по убыванию для размещения наименьших элементов в начале списка.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-117">Specify a descending sort order to put the smallest elements at the start of the list.</span></span>  
  
 <span data-ttu-id="0ebd9-118">Запрос вызывает отдельный метод, чтобы получить размер файла в байтах для обработки возможных исключений, которые будут вызваны при удалении файла в другом потоке за период времени с момента создания объекта <xref:System.IO.FileInfo> в вызове `GetFiles`.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-118">The query calls out to a separate method to obtain the file size in bytes in order to consume the possible exception that will be raised in the case where a file was deleted on another thread in the time period since the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="0ebd9-119">Даже если объект <xref:System.IO.FileInfo> уже создан, может возникнуть исключение, так как объект <xref:System.IO.FileInfo> будет пытаться обновить свойство <xref:System.IO.FileInfo.Length%2A>, используя самый последний размер в байтах при первом обращении к свойству.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-119">Even through the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property by using the most current size in bytes the first time the property is accessed.</span></span> <span data-ttu-id="0ebd9-120">Поместив эту операцию в блок try-catch вне запроса, будет выполнено правило исключения использования операций в запросах, которые могут вызвать побочные эффекты.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-120">By putting this operation in a try-catch block outside the query, we follow the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="0ebd9-121">В целом, необходимо соблюдать осторожность при перехвате исключений, чтобы убедиться, что приложение не остается в неизвестном состоянии.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-121">In general, great care must be taken when consuming exceptions, to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="0ebd9-122">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="0ebd9-122">Compile the code</span></span>  

<span data-ttu-id="0ebd9-123">Создайте проект консольного приложения Visual Basic с `Imports` инструкцией для пространства имен System. LINQ.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-123">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0ebd9-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0ebd9-124">See also</span></span>

- [<span data-ttu-id="0ebd9-125">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ebd9-125">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="0ebd9-126">LINQ и каталоги файлов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ebd9-126">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
