---
description: 'Подробнее о следующем: Практическое руководство. Дозапись в текстовый файл в Visual Basic'
title: Практическое руководство. Дозапись в текстовый файл
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: f66e1cb4ba299ee89f0d84d17d01af67650c9340
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797670"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a><span data-ttu-id="90216-103">Практическое руководство. Дозапись в текстовый файл в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90216-103">How to: Append to Text Files in Visual Basic</span></span>

<span data-ttu-id="90216-104">Метод <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> можно использовать для добавления данных в текстовый файл, задав для параметра `append` значение `True`.</span><span class="sxs-lookup"><span data-stu-id="90216-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to append to a text file by specifying that the `append` parameter is set to `True`.</span></span>  
  
### <a name="to-append-to-a-text-file"></a><span data-ttu-id="90216-105">Добавление данных в текстовый файл</span><span class="sxs-lookup"><span data-stu-id="90216-105">To append to a text file</span></span>  
  
- <span data-ttu-id="90216-106">Используйте метод `WriteAllText`, указав конечный файл и строку, которую требуется добавить, и присвоив параметру `append` значение `True`.</span><span class="sxs-lookup"><span data-stu-id="90216-106">Use the `WriteAllText` method, specifying the target file and string to be appended and setting the `append` parameter to `True`.</span></span>  
  
     <span data-ttu-id="90216-107">В этом примере в файл с именем `Testfile.txt` записывается строка `"This is a test string."`.</span><span class="sxs-lookup"><span data-stu-id="90216-107">This example writes the string `"This is a test string."` to the file named `Testfile.txt`.</span></span>  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="90216-108">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="90216-108">Robust Programming</span></span>  

 <span data-ttu-id="90216-109">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="90216-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="90216-110">Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="90216-110">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="90216-111">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="90216-111">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="90216-112">`File` указывает на путь, который не существует (<xref:System.IO.FileNotFoundException> или <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="90216-112">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="90216-113">Файл уже используется другим процессом или возникла ошибка ввода-вывода (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="90216-113">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="90216-114">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="90216-114">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="90216-115">Имя файла или каталога в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="90216-115">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="90216-116">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="90216-116">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90216-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="90216-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="90216-118">Запись в файлы</span><span class="sxs-lookup"><span data-stu-id="90216-118">Writing to Files</span></span>](writing-to-files.md)
