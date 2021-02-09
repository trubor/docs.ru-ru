---
description: 'Подробнее о следующем: Практическое руководство. Переименование файла в Visual Basic'
title: Практическое руководство. Переименование файла
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: cf182fa94befdfdcb1568052a0193d483670cf49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797410"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="14e2f-103">Практическое руководство. Переименование файла в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="14e2f-103">How to: Rename a File in Visual Basic</span></span>

<span data-ttu-id="14e2f-104">Метод `RenameFile` объекта `My.Computer.FileSystem` можно использовать, чтобы переименовать файл, указав текущее расположение, имя файла и новое имя файла.</span><span class="sxs-lookup"><span data-stu-id="14e2f-104">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="14e2f-105">Этот метод нельзя использовать для перемещения файла. Для перемещения и переименования файла используется метод `MoveFile`.</span><span class="sxs-lookup"><span data-stu-id="14e2f-105">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="14e2f-106">Переименование файла</span><span class="sxs-lookup"><span data-stu-id="14e2f-106">To rename a file</span></span>  
  
- <span data-ttu-id="14e2f-107">Используйте метод `My.Computer.FileSystem.RenameFile`, чтобы переименовать файл.</span><span class="sxs-lookup"><span data-stu-id="14e2f-107">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="14e2f-108">В этом примере переименовывается файл с именем `Test.txt` в `SecondTest.txt`.</span><span class="sxs-lookup"><span data-stu-id="14e2f-108">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 <span data-ttu-id="14e2f-109">Этот пример кода также доступен в качестве фрагмента кода IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="14e2f-109">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="14e2f-110">В средстве выбора фрагментов кода фрагмент находится в разделе **файловая система: обработка дисков, папок и файлов**.</span><span class="sxs-lookup"><span data-stu-id="14e2f-110">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="14e2f-111">Дополнительные сведения см. в статье [Фрагменты кода](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="14e2f-111">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="14e2f-112">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="14e2f-112">Robust Programming</span></span>  

 <span data-ttu-id="14e2f-113">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="14e2f-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="14e2f-114">Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="14e2f-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="14e2f-115">`newName` содержит сведения о пути (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="14e2f-115">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="14e2f-116">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="14e2f-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="14e2f-117">Параметр`newName` имеет значение `Nothing` или является пустой строкой (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="14e2f-117">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="14e2f-118">Исходный файл является недопустимым или не существует (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="14e2f-118">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="14e2f-119">Имеется существующий файл или каталог с именем, указанным в `newName` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="14e2f-119">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="14e2f-120">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="14e2f-120">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="14e2f-121">Имя файла или каталога в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="14e2f-121">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="14e2f-122">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="14e2f-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="14e2f-123">У пользователя отсутствует необходимое разрешение (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="14e2f-123">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14e2f-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="14e2f-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [<span data-ttu-id="14e2f-125">Практическое руководство. Перемещение файла</span><span class="sxs-lookup"><span data-stu-id="14e2f-125">How to: Move a File</span></span>](how-to-move-a-file.md)
- [<span data-ttu-id="14e2f-126">Создание, удаление и перемещение файлов и каталогов</span><span class="sxs-lookup"><span data-stu-id="14e2f-126">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)
- [<span data-ttu-id="14e2f-127">Практическое руководство. Создание копии файла в том же каталоге</span><span class="sxs-lookup"><span data-stu-id="14e2f-127">How to: Create a Copy of a File in the Same Directory</span></span>](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="14e2f-128">Практическое руководство. Создание копии файла в другом каталоге</span><span class="sxs-lookup"><span data-stu-id="14e2f-128">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
