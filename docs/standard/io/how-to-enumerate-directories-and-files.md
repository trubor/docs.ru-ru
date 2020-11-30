---
title: Практическое руководство. Перечисление каталогов и файлов
description: Сведения о перечислении каталогов и файлов с помощью перечислимых коллекций, которые могут обеспечить более высокую производительность, чем массивы в .NET.
ms.date: 12/27/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
ms.openlocfilehash: 7f565531bc3ed44370da8859ed210e0e25027d78
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734664"
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="3209e-103">Практическое руководство. Перечисление каталогов и файлов</span><span class="sxs-lookup"><span data-stu-id="3209e-103">How to: Enumerate directories and files</span></span>

<span data-ttu-id="3209e-104">Перечислимые коллекции дают более высокую производительность, чем массивы, если вы работаете с большими коллекциями файлов и каталогов.</span><span class="sxs-lookup"><span data-stu-id="3209e-104">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span> <span data-ttu-id="3209e-105">Чтобы перечислить каталоги и файлы, вы можете применить методы, которые возвращают перечисляемую коллекцию имен каталогов или файлов, либо их объекты <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo> или <xref:System.IO.FileSystemInfo>.</span><span class="sxs-lookup"><span data-stu-id="3209e-105">To enumerate directories and files, use methods that return an enumerable collection of directory or file names, or their <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span>  
  
<span data-ttu-id="3209e-106">Если вы хотите найти и вернуть только имена каталогов или файлов, используйте методы перечисления из класса <xref:System.IO.Directory>.</span><span class="sxs-lookup"><span data-stu-id="3209e-106">If you want to search and return only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="3209e-107">Если вы хотите найти и вернуть другие свойства каталогов или файлов, используйте классы <xref:System.IO.DirectoryInfo> и <xref:System.IO.FileSystemInfo>.</span><span class="sxs-lookup"><span data-stu-id="3209e-107">If you want to search and return other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
<span data-ttu-id="3209e-108">Кроме того, можно использовать перечисляемые коллекции из этих методов в качестве параметра <xref:System.Collections.Generic.IEnumerable%601> для конструкторов классов коллекций, таких как <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="3209e-108">You can use enumerable collections from these methods as the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes like <xref:System.Collections.Generic.List%601>.</span></span>  
  
<span data-ttu-id="3209e-109">В следующей таблице обобщаются методы, которые возвращают перечисляемые коллекции файлов и каталогов:</span><span class="sxs-lookup"><span data-stu-id="3209e-109">The following table summarizes the methods that return enumerable collections of files and directories:</span></span>  
  
|<span data-ttu-id="3209e-110">Что нужно найти и вернуть</span><span class="sxs-lookup"><span data-stu-id="3209e-110">To search and return</span></span>|<span data-ttu-id="3209e-111">Используемый метод</span><span class="sxs-lookup"><span data-stu-id="3209e-111">Use method</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="3209e-112">Имена каталогов</span><span class="sxs-lookup"><span data-stu-id="3209e-112">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3209e-113">Сведения о каталогах (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="3209e-113">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3209e-114">Имена файлов</span><span class="sxs-lookup"><span data-stu-id="3209e-114">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3209e-115">Сведения о файлах (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="3209e-115">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3209e-116">Имена записей файловой системы</span><span class="sxs-lookup"><span data-stu-id="3209e-116">File system entry names</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3209e-117">Сведения о записи файловой системы (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="3209e-117">File system entry information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3209e-118">Имена каталогов и файлов</span><span class="sxs-lookup"><span data-stu-id="3209e-118">Directory and file names</span></span> |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> <span data-ttu-id="3209e-119">Несмотря на то, что у вас есть возможность немедленно перечислить все файлы во вложенных каталогах родительского каталога, применив параметр <xref:System.IO.SearchOption.AllDirectories> необязательного перечисления <xref:System.IO.SearchOption>, из-за ошибок <xref:System.UnauthorizedAccessException> перечисление может оказаться неполным.</span><span class="sxs-lookup"><span data-stu-id="3209e-119">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> option of the optional <xref:System.IO.SearchOption> enumeration, <xref:System.UnauthorizedAccessException> errors may make the enumeration incomplete.</span></span> <span data-ttu-id="3209e-120">Вы можете реализовать перехват таких исключений, сначала перечислив каталоги, а затем файлы.</span><span class="sxs-lookup"><span data-stu-id="3209e-120">You can catch these exceptions by first enumerating directories and then enumerating files.</span></span>  
  
## <a name="examples-use-the-directory-class"></a><span data-ttu-id="3209e-121">Примеры Использование класса Directory</span><span class="sxs-lookup"><span data-stu-id="3209e-121">Examples: Use the Directory class</span></span>  
  
<span data-ttu-id="3209e-122">В следующем примере используется метод <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType>, чтобы получить список имен каталогов верхнего уровня из указанного пути.</span><span class="sxs-lookup"><span data-stu-id="3209e-122">The following example uses the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to get a list of the top-level directory names in a specified path.</span></span>  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

<span data-ttu-id="3209e-123">В следующем примере используется метод <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> для рекурсивного перечисления имен всех файлов в каталоге и подкаталогах, соответствующих определенному шаблону.</span><span class="sxs-lookup"><span data-stu-id="3209e-123">The following example uses the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to recursively enumerate all file names in a directory and subdirectories that match a certain pattern.</span></span> <span data-ttu-id="3209e-124">После этого проверяется каждая строка каждого файла и отображаются строки, которые содержат указанную строку, с соответствующими именами файлов и путями к ним.</span><span class="sxs-lookup"><span data-stu-id="3209e-124">It then reads each line of each file and displays the lines that contain a specified string, with their filenames and paths.</span></span>

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a><span data-ttu-id="3209e-125">Примеры Использование класса DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="3209e-125">Examples: Use the DirectoryInfo class</span></span>  
  
<span data-ttu-id="3209e-126">В следующем примере используется метод <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> для получения списка каталогов верхнего уровня, для которых значение <xref:System.IO.FileSystemInfo.CreationTimeUtc> раньше заданного значения <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="3209e-126">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to list a collection of top-level directories whose <xref:System.IO.FileSystemInfo.CreationTimeUtc> is earlier than a certain <xref:System.DateTime> value.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
<span data-ttu-id="3209e-127">В следующем примере используется метод <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> для получения списка всех файлов, для которых значение <xref:System.IO.FileInfo.Length> превышает 10 МБ.</span><span class="sxs-lookup"><span data-stu-id="3209e-127">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to list all files whose <xref:System.IO.FileInfo.Length> exceeds 10MB.</span></span> <span data-ttu-id="3209e-128">В этом примере поиска сначала перечисляются каталоги верхнего уровня, чтобы перехватить все возможные исключения несанкционированного доступа, а затем перечисляются файлы.</span><span class="sxs-lookup"><span data-stu-id="3209e-128">This example first enumerates the top-level directories, to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3209e-129">См. также</span><span class="sxs-lookup"><span data-stu-id="3209e-129">See also</span></span>

- [<span data-ttu-id="3209e-130">Файловый и потоковый ввод-вывод</span><span class="sxs-lookup"><span data-stu-id="3209e-130">File and stream I/O</span></span>](index.md)
