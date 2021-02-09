---
description: 'Подробнее о следующем: Практическое руководство. Удаление файла в Visual Basic'
title: Практическое руководство. Удаление файла
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 49bfe2e4a0d9114e2f653ae14dab303e35e2dfeb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797579"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="67dcb-103">Практическое руководство. Удаление файла в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="67dcb-103">How to: Delete a File in Visual Basic</span></span>

<span data-ttu-id="67dcb-104">Метод `DeleteFile` объекта `My.Computer.FileSystem` позволяет удалить файл.</span><span class="sxs-lookup"><span data-stu-id="67dcb-104">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="67dcb-105">Параметры метода позволяют указать, следует ли отправлять удаленный файл в **корзину**, следует ли запрашивать у пользователя подтверждение удаления файла и что делать при отмене пользователем операции.</span><span class="sxs-lookup"><span data-stu-id="67dcb-105">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="67dcb-106">Удаление текстового файла</span><span class="sxs-lookup"><span data-stu-id="67dcb-106">To delete a text file</span></span>  
  
- <span data-ttu-id="67dcb-107">Для удаления файла используйте метод `DeleteFile`.</span><span class="sxs-lookup"><span data-stu-id="67dcb-107">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="67dcb-108">В следующем коде показано, как удалить файл с именем `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="67dcb-108">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="67dcb-109">Удаление текстового файла с запросом подтверждения удаления файла</span><span class="sxs-lookup"><span data-stu-id="67dcb-109">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
- <span data-ttu-id="67dcb-110">Для удаления файла используйте метод `DeleteFile`, присвоив параметру`showUI` значение `AllDialogs`.</span><span class="sxs-lookup"><span data-stu-id="67dcb-110">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="67dcb-111">В следующем коде демонстрируется удаление файла `test.txt` с запросом у пользователя подтверждения удаления файла.</span><span class="sxs-lookup"><span data-stu-id="67dcb-111">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="67dcb-112">Удаление текстового файла и отправка его в корзину</span><span class="sxs-lookup"><span data-stu-id="67dcb-112">To delete a text file and send it to the Recycle Bin</span></span>  
  
- <span data-ttu-id="67dcb-113">Для удаления файла используйте метод `DeleteFile`, присвоив параметру `SendToRecycleBin` значение `recycle`.</span><span class="sxs-lookup"><span data-stu-id="67dcb-113">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="67dcb-114">В следующем коде демонстрируется удаление файла `test.txt` и отправка его в **корзину**.</span><span class="sxs-lookup"><span data-stu-id="67dcb-114">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a><span data-ttu-id="67dcb-115">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="67dcb-115">Robust Programming</span></span>  

 <span data-ttu-id="67dcb-116">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="67dcb-116">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="67dcb-117">Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="67dcb-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="67dcb-118">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="67dcb-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="67dcb-119">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="67dcb-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="67dcb-120">Имя файла или папки в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="67dcb-120">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="67dcb-121">Файл уже используется (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="67dcb-121">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="67dcb-122">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="67dcb-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="67dcb-123">Файл не существует (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="67dcb-123">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="67dcb-124">Пользователь не имеет разрешения на удаление файла, или файл доступен только для чтения (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="67dcb-124">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="67dcb-125">Существует ситуация частичного доверия, в которой пользователь не имеет достаточных разрешений для доступа к файлу (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="67dcb-125">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="67dcb-126">Пользователь отменил действие и `onUserCancel` задано `ThrowException` (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="67dcb-126">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67dcb-127">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="67dcb-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="67dcb-128">Практическое руководство. Получение коллекции содержащихся в каталоге файлов</span><span class="sxs-lookup"><span data-stu-id="67dcb-128">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
