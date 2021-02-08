---
description: 'Дополнительные сведения о: файл слишком большой для чтения в массив байтов'
title: Файл слишком велик для чтения в массив байтов
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 8b2eb7bcbbea42c56d607147e55d6c02695c5670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796292"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="0aac4-103">Файл слишком велик для чтения в массив байтов</span><span class="sxs-lookup"><span data-stu-id="0aac4-103">File is too large to read into a byte array</span></span>

<span data-ttu-id="0aac4-104">Размер файла, который вы пытаетесь прочесть в массиве байтов, превышает 4 ГБ.</span><span class="sxs-lookup"><span data-stu-id="0aac4-104">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="0aac4-105">`My.Computer.FileSystem.ReadAllBytes`Метод не может считать файл, размер которого превышает этот.</span><span class="sxs-lookup"><span data-stu-id="0aac4-105">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0aac4-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="0aac4-106">To correct this error</span></span>  
  
- <span data-ttu-id="0aac4-107">Используйте <xref:System.IO.StreamReader> для чтения файла.</span><span class="sxs-lookup"><span data-stu-id="0aac4-107">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="0aac4-108">Дополнительные сведения см. [в разделе основы платформа .NET Framework файлового ввода-вывода и файловой системы (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="0aac4-108">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aac4-109">См. также</span><span class="sxs-lookup"><span data-stu-id="0aac4-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [<span data-ttu-id="0aac4-110">Доступ к файлам с помощью Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0aac4-110">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
- [<span data-ttu-id="0aac4-111">Практическое руководство. Чтение текста из файлов с помощью StreamReader</span><span class="sxs-lookup"><span data-stu-id="0aac4-111">How to: Read Text from Files with a StreamReader</span></span>](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
