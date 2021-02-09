---
description: 'Подробнее о следующем: Практическое руководство. Получение коллекции содержащихся в каталоге файлов в Visual Basic'
title: Практическое руководство. Получение коллекции содержащихся в каталоге файлов
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: bd799390c0ad0868f51387ba12e8612fe8948297
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797540"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="f643a-103">Практическое руководство. Получение коллекции содержащихся в каталоге файлов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f643a-103">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>

<span data-ttu-id="f643a-104">Перегрузка метода <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> вернет доступную только для чтения коллекцию строк, представляющих собой имена файлов в каталоге:</span><span class="sxs-lookup"><span data-stu-id="f643a-104">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
- <span data-ttu-id="f643a-105">Перегрузка метода <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> позволяет найти простой файл в указанном каталоге без поиска подкаталогов.</span><span class="sxs-lookup"><span data-stu-id="f643a-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
- <span data-ttu-id="f643a-106">Перегрузка метода <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> позволяет указать дополнительные параметры поиска.</span><span class="sxs-lookup"><span data-stu-id="f643a-106">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="f643a-107">Для указания шаблона поиска можно использовать параметр `wildCards`.</span><span class="sxs-lookup"><span data-stu-id="f643a-107">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="f643a-108">Чтобы включить подкаталоги в поиск, присвойте параметру `searchType` значение <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f643a-108">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f643a-109">Если файлы, соответствующие указанному шаблону, не найдены, возвращается пустая коллекция.</span><span class="sxs-lookup"><span data-stu-id="f643a-109">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="f643a-110">Составление списка файлов в каталоге</span><span class="sxs-lookup"><span data-stu-id="f643a-110">To list files in a directory</span></span>  
  
- <span data-ttu-id="f643a-111">Используйте перегрузки одного из методов <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType>, указывая имя и путь к каталогу для поиска в параметре `directory`.</span><span class="sxs-lookup"><span data-stu-id="f643a-111">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="f643a-112">В следующем примере возвращаются и добавляются в список `ListBox1` все файлы, находящиеся в каталоге.</span><span class="sxs-lookup"><span data-stu-id="f643a-112">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a><span data-ttu-id="f643a-113">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="f643a-113">Robust Programming</span></span>  

 <span data-ttu-id="f643a-114">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="f643a-114">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="f643a-115">Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="f643a-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="f643a-116">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="f643a-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="f643a-117">`directory` не существует (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="f643a-117">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="f643a-118">`directory` указывает на существующий файл (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="f643a-118">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="f643a-119">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="f643a-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="f643a-120">Имя файла или каталога в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="f643a-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="f643a-121">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="f643a-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="f643a-122">У пользователя отсутствуют необходимые разрешения (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="f643a-122">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f643a-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="f643a-123">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [<span data-ttu-id="f643a-124">Практическое руководство. Поиск файлов по конкретному шаблону</span><span class="sxs-lookup"><span data-stu-id="f643a-124">How to: Find Files with a Specific Pattern</span></span>](how-to-find-files-with-a-specific-pattern.md)
- [<span data-ttu-id="f643a-125">Практическое руководство. Поиск подкаталогов по заданному шаблону</span><span class="sxs-lookup"><span data-stu-id="f643a-125">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
