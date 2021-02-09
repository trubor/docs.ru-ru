---
description: 'Подробнее о следующем: Практическое руководство. Чтение из двоичного файла в Visual Basic'
title: Практическое руководство. Чтение из двоичных файлов
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: 0d522c6f55c0ef2e39437ba732040afdf5113d7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797514"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a><span data-ttu-id="75eca-103">Практическое руководство. Чтение из двоичного файла в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="75eca-103">How to: Read From Binary Files in Visual Basic</span></span>

<span data-ttu-id="75eca-104">Объект `My.Computer.FileSystem` предоставляет метод `ReadAllBytes` для чтения данных из двоичных файлов.</span><span class="sxs-lookup"><span data-stu-id="75eca-104">The `My.Computer.FileSystem` object provides the `ReadAllBytes` method for reading from binary files.</span></span>  
  
### <a name="to-read-from-a-binary-file"></a><span data-ttu-id="75eca-105">Чтение данных из двоичного файла</span><span class="sxs-lookup"><span data-stu-id="75eca-105">To read from a binary file</span></span>  
  
- <span data-ttu-id="75eca-106">Используйте метод `ReadAllBytes`, который возвращает содержимое файла в виде массива байтов.</span><span class="sxs-lookup"><span data-stu-id="75eca-106">Use the `ReadAllBytes` method, which returns the contents of a file as a byte array.</span></span> <span data-ttu-id="75eca-107">В этом примере производится чтение данных из файла `C:/Documents and Settings/selfportrait.jpg`.</span><span class="sxs-lookup"><span data-stu-id="75eca-107">This example reads from the file `C:/Documents and Settings/selfportrait.jpg`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
- <span data-ttu-id="75eca-108">При работе с большими двоичными файлами можно использовать метод <xref:System.IO.FileStream.Read%2A> объекта <xref:System.IO.FileStream>, чтобы за раз считывать из файла только заданный объем данных.</span><span class="sxs-lookup"><span data-stu-id="75eca-108">For large binary files, you can use the <xref:System.IO.FileStream.Read%2A> method of the <xref:System.IO.FileStream> object to read from the file only a specified amount at a time.</span></span> <span data-ttu-id="75eca-109">Затем можно ограничить объем файла, загружаемый в память во время каждой операции чтения.</span><span class="sxs-lookup"><span data-stu-id="75eca-109">You can then limit how much of the file is loaded into memory for each read operation.</span></span> <span data-ttu-id="75eca-110">В следующем примере кода показано копирование файла, причем вызывающий объект задает, какая часть файла помещается в память при выполнении каждой операции чтения.</span><span class="sxs-lookup"><span data-stu-id="75eca-110">The following code example copies a file and allows the caller to specify how much of the file is read into memory per read operation.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a><span data-ttu-id="75eca-111">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="75eca-111">Robust Programming</span></span>  

 <span data-ttu-id="75eca-112">Исключение может возникнуть в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="75eca-112">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="75eca-113">Путь является недопустимым, поскольку путь представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="75eca-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="75eca-114">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="75eca-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="75eca-115">Файл не существует (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="75eca-115">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="75eca-116">Файл уже используется другим процессом или возникла ошибка ввода-вывода (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="75eca-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="75eca-117">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="75eca-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="75eca-118">Имя файла или каталога в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="75eca-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="75eca-119">Не хватает памяти для записи строки в буфер (<xref:System.OutOfMemoryException>).</span><span class="sxs-lookup"><span data-stu-id="75eca-119">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
- <span data-ttu-id="75eca-120">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="75eca-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="75eca-121">По имени файла не всегда можно с уверенностью судить о его содержимом.</span><span class="sxs-lookup"><span data-stu-id="75eca-121">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="75eca-122">Например, файл с именем Form1.vb может вовсе не быть исходным файлом Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="75eca-122">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="75eca-123">Следует проверять все входные данные перед использованием их в приложении.</span><span class="sxs-lookup"><span data-stu-id="75eca-123">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="75eca-124">Содержимое файла может отличаться от ожидаемого, поэтому может не удаться прочесть файл с помощью методов чтения.</span><span class="sxs-lookup"><span data-stu-id="75eca-124">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75eca-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="75eca-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="75eca-126">Чтение из файлов</span><span class="sxs-lookup"><span data-stu-id="75eca-126">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="75eca-127">Практическое руководство. Чтение из текстовых файлов различных форматов</span><span class="sxs-lookup"><span data-stu-id="75eca-127">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="75eca-128">Запись данных в буфер обмена и чтение их оттуда</span><span class="sxs-lookup"><span data-stu-id="75eca-128">Storing Data to and Reading from the Clipboard</span></span>](../computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
