---
description: 'Подробнее о следующем: Практическое руководство. Копирование файлов в каталог с использованием шаблона в Visual Basic'
title: Практическое руководство. Копирование файлов с определенным шаблоном в каталог
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: 2a5163e6420d747a724fec9b8ede8dbcc6a938be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797631"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="0c816-103">Практическое руководство. Копирование файлов в каталог с использованием шаблона в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0c816-103">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>

<span data-ttu-id="0c816-104">Метод <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> возвращает доступную только для чтения коллекцию строк, представляющих имена путей для файлов.</span><span class="sxs-lookup"><span data-stu-id="0c816-104">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="0c816-105">Для указания определенного шаблона можно использовать параметр `wildCards` .</span><span class="sxs-lookup"><span data-stu-id="0c816-105">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="0c816-106">Если соответствующие файлы не найдены, возвращается пустая коллекция.</span><span class="sxs-lookup"><span data-stu-id="0c816-106">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="0c816-107">Для копирования файлов в каталог можно использовать метод <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> .</span><span class="sxs-lookup"><span data-stu-id="0c816-107">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="0c816-108">Копирование файлов с определенным шаблоном в каталог</span><span class="sxs-lookup"><span data-stu-id="0c816-108">To copy files with a specific pattern to a directory</span></span>  
  
1. <span data-ttu-id="0c816-109">Используйте метод `GetFiles` для возврата списка файлов.</span><span class="sxs-lookup"><span data-stu-id="0c816-109">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="0c816-110">В этом примере возвращены все RTF-файлы в указанном каталоге.</span><span class="sxs-lookup"><span data-stu-id="0c816-110">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. <span data-ttu-id="0c816-111">Используйте метод `CopyFile` для копирования файлов.</span><span class="sxs-lookup"><span data-stu-id="0c816-111">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="0c816-112">В этом примере файлы копируются в каталог с именем `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="0c816-112">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. <span data-ttu-id="0c816-113">Закройте оператор `For` с помощью оператора `Next` .</span><span class="sxs-lookup"><span data-stu-id="0c816-113">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a><span data-ttu-id="0c816-114">Пример</span><span class="sxs-lookup"><span data-stu-id="0c816-114">Example</span></span>  

 <span data-ttu-id="0c816-115">В следующем примере, который представляет вышеописанные фрагменты в завершенной форме, RTF-файлы копируются из указанного каталога в каталог с именем `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="0c816-115">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="0c816-116">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0c816-116">.NET Framework Security</span></span>  

 <span data-ttu-id="0c816-117">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="0c816-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0c816-118">Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="0c816-118">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="0c816-119">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="0c816-119">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="0c816-120">Каталог не существует (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="0c816-120">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="0c816-121">Каталог указывает на существующий файл (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="0c816-121">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="0c816-122">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="0c816-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="0c816-123">Имя файла или каталога в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="0c816-123">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="0c816-124">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="0c816-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="0c816-125">У пользователя отсутствуют необходимые разрешения (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="0c816-125">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c816-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0c816-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="0c816-127">Практическое руководство. Поиск подкаталогов по заданному шаблону</span><span class="sxs-lookup"><span data-stu-id="0c816-127">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="0c816-128">Устранение неполадок: Чтение из текстовых файлов и запись в такие файлы</span><span class="sxs-lookup"><span data-stu-id="0c816-128">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="0c816-129">Практическое руководство. Получение коллекции содержащихся в каталоге файлов</span><span class="sxs-lookup"><span data-stu-id="0c816-129">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
