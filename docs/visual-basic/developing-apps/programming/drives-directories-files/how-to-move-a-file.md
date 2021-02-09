---
description: 'Подробнее о следующем: Практическое руководство. Перемещение файла в Visual Basic'
title: Практическое руководство. Перемещение файла
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 31049d2b7f0516c056fc1f1620a3ad8c1f0a2e1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797527"
---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="5db04-103">Практическое руководство. Перемещение файла в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5db04-103">How to: Move a File in Visual Basic</span></span>

<span data-ttu-id="5db04-104">Метод `My.Computer.FileSystem.MoveFile` может использоваться для перемещения файла в другую папку.</span><span class="sxs-lookup"><span data-stu-id="5db04-104">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="5db04-105">Если целевая структура не существует, она будет создана.</span><span class="sxs-lookup"><span data-stu-id="5db04-105">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="5db04-106">Перемещение файла</span><span class="sxs-lookup"><span data-stu-id="5db04-106">To move a file</span></span>  
  
- <span data-ttu-id="5db04-107">Используйте метод `MoveFile` , чтобы переместить файл, указав имя и расположение исходного и целевого файлов.</span><span class="sxs-lookup"><span data-stu-id="5db04-107">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="5db04-108">В данном примере перемещается файл с именем `test.txt` из `TestDir1` в `TestDir2`.</span><span class="sxs-lookup"><span data-stu-id="5db04-108">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="5db04-109">Обратите внимание, что имя целевого файла указывается даже несмотря на то, что оно совпадает с именем исходного файла.</span><span class="sxs-lookup"><span data-stu-id="5db04-109">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="5db04-110">Перемещение и переименование файла</span><span class="sxs-lookup"><span data-stu-id="5db04-110">To move a file and rename it</span></span>  
  
- <span data-ttu-id="5db04-111">Используйте метод `MoveFile` , чтобы переместить файл, указав имя и расположение исходного файла, целевое расположение и новое имя в целевом расположении.</span><span class="sxs-lookup"><span data-stu-id="5db04-111">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="5db04-112">В данном примере файл с именем `test.txt` перемещается из `TestDir1` в `TestDir2` и переименовывается в `nexttest.txt`.</span><span class="sxs-lookup"><span data-stu-id="5db04-112">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5db04-113">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="5db04-113">Robust Programming</span></span>  

 <span data-ttu-id="5db04-114">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="5db04-114">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5db04-115">Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="5db04-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="5db04-116">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="5db04-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="5db04-117">Параметр`destinationFileName` имеет значение `Nothing` или является пустой строкой (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="5db04-117">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="5db04-118">Исходный файл является недопустимым или не существует (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="5db04-118">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="5db04-119">Объединенный путь указывает на существующий каталог, целевой файл существует и `overwrite` имеет значение `False`, файл в целевом каталоге с тем же именем уже используется или пользователь не имеет необходимых разрешений для доступа к файлу (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5db04-119">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="5db04-120">Имя файла или каталога в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="5db04-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="5db04-121">`showUI` имеет значение `True`, `onUserCancel` имеет значение `ThrowException`, и либо пользователь отменил операцию, либо произошла неопределенная ошибка ввода-вывода (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="5db04-121">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="5db04-122">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="5db04-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="5db04-123">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="5db04-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="5db04-124">У пользователя отсутствует необходимое разрешение (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="5db04-124">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db04-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5db04-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [<span data-ttu-id="5db04-126">Практическое руководство. Переименование файла</span><span class="sxs-lookup"><span data-stu-id="5db04-126">How to: Rename a File</span></span>](how-to-rename-a-file.md)
- [<span data-ttu-id="5db04-127">Практическое руководство. Создание копии файла в другом каталоге</span><span class="sxs-lookup"><span data-stu-id="5db04-127">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="5db04-128">Практическое руководство. Анализ путей к файлам</span><span class="sxs-lookup"><span data-stu-id="5db04-128">How to: Parse File Paths</span></span>](how-to-parse-file-paths.md)
