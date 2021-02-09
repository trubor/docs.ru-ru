---
description: 'Подробнее о следующем: Практическое руководство. Запись текста в файлы в Visual Basic'
title: Практическое руководство. Запись текста в файлы
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: 3f94999c1d20002074ecf57577d3402c350248ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797345"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="aa2ca-103">Практическое руководство. Запись текста в файлы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa2ca-103">How to: Write Text to Files in Visual Basic</span></span>

<span data-ttu-id="aa2ca-104">Метод <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> можно использовать для записи текста в файлы.</span><span class="sxs-lookup"><span data-stu-id="aa2ca-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="aa2ca-105">Если заданный файл не существует, он будет создан.</span><span class="sxs-lookup"><span data-stu-id="aa2ca-105">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="aa2ca-106">Процедура</span><span class="sxs-lookup"><span data-stu-id="aa2ca-106">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="aa2ca-107">Запись текста в файл</span><span class="sxs-lookup"><span data-stu-id="aa2ca-107">To write text to a file</span></span>  
  
- <span data-ttu-id="aa2ca-108">Используйте `WriteAllText` метод для записи текста в файл, указав файл и текст, который требуется записать.</span><span class="sxs-lookup"><span data-stu-id="aa2ca-108">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="aa2ca-109">В этом примере строка `"This is new text."` записывается в файл с именем `test.txt`, при этом текст добавляется к тексту, имеющемуся в файле.</span><span class="sxs-lookup"><span data-stu-id="aa2ca-109">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="aa2ca-110">Запись набора строк в файл</span><span class="sxs-lookup"><span data-stu-id="aa2ca-110">To write a series of strings to a file</span></span>  
  
- <span data-ttu-id="aa2ca-111">Выполните цикл по коллекции строк.</span><span class="sxs-lookup"><span data-stu-id="aa2ca-111">Loop through the string collection.</span></span> <span data-ttu-id="aa2ca-112">Используйте `WriteAllText` метод для записи текста в файл, указав конечный файл и строку, которую требуется добавить, и присвоив параметру `append` значение `True`.</span><span class="sxs-lookup"><span data-stu-id="aa2ca-112">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="aa2ca-113">В этом примере имена файлов в каталоге `Documents and Settings` записываются в файл `FileList.txt`, при этом между каждой записью вставляется символ перевода строки для удобства чтения.</span><span class="sxs-lookup"><span data-stu-id="aa2ca-113">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a><span data-ttu-id="aa2ca-114">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="aa2ca-114">Robust Programming</span></span>  

 <span data-ttu-id="aa2ca-115">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="aa2ca-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="aa2ca-116">Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="aa2ca-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="aa2ca-117">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="aa2ca-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="aa2ca-118">`File` указывает на путь, который не существует (<xref:System.IO.FileNotFoundException> или <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="aa2ca-118">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="aa2ca-119">Файл уже используется другим процессом или возникла ошибка ввода-вывода (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="aa2ca-119">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="aa2ca-120">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="aa2ca-120">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="aa2ca-121">Имя файла или каталога в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="aa2ca-121">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="aa2ca-122">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="aa2ca-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="aa2ca-123">Диск заполнен, и вызов `WriteAllText` завершается сбоем (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="aa2ca-123">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="aa2ca-124">Если код выполняется в контексте частичного доверия, исключение может возникнуть из-за недостатка прав доступа.</span><span class="sxs-lookup"><span data-stu-id="aa2ca-124">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="aa2ca-125">Дополнительные сведения см. в разделе [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="aa2ca-125">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa2ca-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="aa2ca-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [<span data-ttu-id="aa2ca-127">Практическое руководство. Чтение из текстовых файлов</span><span class="sxs-lookup"><span data-stu-id="aa2ca-127">How to: Read from Text Files</span></span>](how-to-read-from-text-files.md)
