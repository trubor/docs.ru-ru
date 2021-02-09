---
description: 'Подробнее о следующем: Практическое руководство. Запись текста в файлы с помощью StreamWriter в Visual Basic'
title: Практическое руководство. Запись текста в файлы с помощью StreamWriter
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: d5528d0b5e7de40062558d29c0d3bebc227583a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797358"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="35cd1-103">Практическое руководство. Запись текста в файлы с помощью StreamWriter в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35cd1-103">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>

<span data-ttu-id="35cd1-104">В этом примере с помощью метода `My.Computer.FileSystem.OpenTextFileWriter` открывается объект <xref:System.IO.StreamWriter>, который используется для записи строки в текстовый файл с помощью метода <xref:System.IO.TextWriter.WriteLine%2A> класса <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="35cd1-104">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35cd1-105">Пример</span><span class="sxs-lookup"><span data-stu-id="35cd1-105">Example</span></span>  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a><span data-ttu-id="35cd1-106">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="35cd1-106">Robust Programming</span></span>  

 <span data-ttu-id="35cd1-107">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="35cd1-107">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="35cd1-108">Файл существует и является файлом только для чтения (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="35cd1-108">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="35cd1-109">Диск заполнен (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="35cd1-109">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="35cd1-110">Слишком длинное имя пути (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="35cd1-110">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="35cd1-111">Безопасность .NET Framework</span><span class="sxs-lookup"><span data-stu-id="35cd1-111">.NET Framework Security</span></span>  

 <span data-ttu-id="35cd1-112">В этом примере создается файл (если файл отсутствует).</span><span class="sxs-lookup"><span data-stu-id="35cd1-112">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="35cd1-113">Если приложению требуется создать файл, оно должно иметь доступ к каталогу для создания файлов (`Create`).</span><span class="sxs-lookup"><span data-stu-id="35cd1-113">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="35cd1-114">Если файл уже существует, то приложению достаточно иметь лишь доступ для записи файлов (`Write`), т. е. меньшие привилегии.</span><span class="sxs-lookup"><span data-stu-id="35cd1-114">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="35cd1-115">Безопаснее создавать файл во время развертывания, если это возможно, а также предоставлять доступ `Read` к отдельному файлу вместо доступа `Create` к папке.</span><span class="sxs-lookup"><span data-stu-id="35cd1-115">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35cd1-116">См. также</span><span class="sxs-lookup"><span data-stu-id="35cd1-116">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [<span data-ttu-id="35cd1-117">Практическое руководство. Чтение из текстовых файлов</span><span class="sxs-lookup"><span data-stu-id="35cd1-117">How to: Read from Text Files</span></span>](how-to-read-from-text-files.md)
- [<span data-ttu-id="35cd1-118">Запись в файлы</span><span class="sxs-lookup"><span data-stu-id="35cd1-118">Writing to Files</span></span>](writing-to-files.md)
