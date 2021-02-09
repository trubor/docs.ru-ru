---
description: 'Подробнее о следующем: Практическое руководство. Создание копии файла в том же каталоге в Visual Basic'
title: Практическое руководство. Создание копии файла в том же каталоге
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 27fecc22a9317dd45e663aa37884c6c1f1e36349
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797618"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="5c8a8-103">Практическое руководство. Создание копии файла в том же каталоге в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5c8a8-103">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>

<span data-ttu-id="5c8a8-104">Для копирования файлов используйте метод `My.Computer.FileSystem.CopyFile`.</span><span class="sxs-lookup"><span data-stu-id="5c8a8-104">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="5c8a8-105">Эти параметры обеспечивают возможность перезаписи существующих файлов, переименования файлов и отображения хода выполнения операции, а также отмены операции пользователем.</span><span class="sxs-lookup"><span data-stu-id="5c8a8-105">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="5c8a8-106">Создание копии файла в том же каталоге</span><span class="sxs-lookup"><span data-stu-id="5c8a8-106">To create a copy of a file in the same folder</span></span>  
  
- <span data-ttu-id="5c8a8-107">Используйте метод `CopyFile`, указав конечный файл и расположение.</span><span class="sxs-lookup"><span data-stu-id="5c8a8-107">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="5c8a8-108">В следующем примере создается копия `test.txt` с именем `test2.txt`.</span><span class="sxs-lookup"><span data-stu-id="5c8a8-108">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="5c8a8-109">Создание копии файла в том же каталоге, перезапись существующих файлов</span><span class="sxs-lookup"><span data-stu-id="5c8a8-109">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
- <span data-ttu-id="5c8a8-110">Используйте метод `CopyFile`, указав конечный файл и расположение и задав для параметра `overwrite` значение `True`.</span><span class="sxs-lookup"><span data-stu-id="5c8a8-110">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="5c8a8-111">В следующем примере создается копия `test.txt` с именем `test2.txt` и перезаписываются существующие файлы с этим именем.</span><span class="sxs-lookup"><span data-stu-id="5c8a8-111">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5c8a8-112">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="5c8a8-112">Robust Programming</span></span>  

 <span data-ttu-id="5c8a8-113">Исключение может возникнуть в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="5c8a8-113">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="5c8a8-114">Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="5c8a8-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="5c8a8-115">Системе не удалось получить абсолютный путь (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="5c8a8-115">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="5c8a8-116">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="5c8a8-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="5c8a8-117">Исходный файл является недопустимым или не существует (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="5c8a8-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="5c8a8-118">Объединенный путь указывает на существующий каталог (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5c8a8-118">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="5c8a8-119">Конечный файл существует, а параметр `overwrite` имеет значение `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5c8a8-119">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="5c8a8-120">У пользователя нет необходимых разрешений для доступа к файлу (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5c8a8-120">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="5c8a8-121">Файл в папке назначения с тем же именем уже используется (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5c8a8-121">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="5c8a8-122">Имя файла или папки в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="5c8a8-122">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="5c8a8-123">Параметр `ShowUI` имеет значение `True`, параметр `onUserCancel` имеет значение `ThrowException`, и пользователь отменил операцию (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="5c8a8-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="5c8a8-124">`ShowUI` имеет значение `True`, параметр `onUserCancel` имеет значение `ThrowException`, и возникла неопределенная ошибка ввода-вывода (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="5c8a8-124">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="5c8a8-125">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="5c8a8-125">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="5c8a8-126">У пользователя отсутствует необходимое разрешение (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="5c8a8-126">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="5c8a8-127">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="5c8a8-127">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c8a8-128">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5c8a8-128">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="5c8a8-129">Практическое руководство. Копирование файлов с определенным шаблоном в каталог</span><span class="sxs-lookup"><span data-stu-id="5c8a8-129">How to: Copy Files with a Specific Pattern to a Directory</span></span>](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="5c8a8-130">Практическое руководство. Создание копии файла в другом каталоге</span><span class="sxs-lookup"><span data-stu-id="5c8a8-130">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="5c8a8-131">Практическое руководство. Копирование каталога в другой каталог</span><span class="sxs-lookup"><span data-stu-id="5c8a8-131">How to: Copy a Directory to Another Directory</span></span>](how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="5c8a8-132">Практическое руководство. Переименование файла</span><span class="sxs-lookup"><span data-stu-id="5c8a8-132">How to: Rename a File</span></span>](how-to-rename-a-file.md)
