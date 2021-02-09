---
description: 'Подробнее о следующем: Практическое руководство. Запись текста в двоичные файлы в Visual Basic'
title: Практическое руководство. Запись в двоичные файлы
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: a1fe18c9143c26fd40e6a1d9cde36581c2c0be12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797332"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="b82b3-103">Практическое руководство. Запись текста в двоичные файлы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b82b3-103">How to: Write to Binary Files in Visual Basic</span></span>

<span data-ttu-id="b82b3-104">Метод <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> записывает данные в двоичный файл.</span><span class="sxs-lookup"><span data-stu-id="b82b3-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="b82b3-105">Если параметр `append` имеет значение `True`, данные будут добавляться в файл; в противном случае данные в файле перезаписываются.</span><span class="sxs-lookup"><span data-stu-id="b82b3-105">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>

<span data-ttu-id="b82b3-106">Если указанный путь без имени файла является недопустимым, возникает исключение <xref:System.IO.DirectoryNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="b82b3-106">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="b82b3-107">Если путь является допустимым, но файл не существует, файл будет создан.</span><span class="sxs-lookup"><span data-stu-id="b82b3-107">If the path is valid but the file does not exist, the file will be created.</span></span>

## <a name="to-write-to-a-binary-file"></a><span data-ttu-id="b82b3-108">Запись в двоичный файл</span><span class="sxs-lookup"><span data-stu-id="b82b3-108">To write to a binary file</span></span>

<span data-ttu-id="b82b3-109">Используйте метод `WriteAllBytes`, указав путь к файлу, имя файла и байты, которые требуется записать.</span><span class="sxs-lookup"><span data-stu-id="b82b3-109">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="b82b3-110">В этом примере массив данных `CustomerData` добавляется в файл `CollectedData.dat`.</span><span class="sxs-lookup"><span data-stu-id="b82b3-110">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a><span data-ttu-id="b82b3-111">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="b82b3-111">Robust Programming</span></span>

<span data-ttu-id="b82b3-112">Исключение может возникнуть при следующих условиях:</span><span class="sxs-lookup"><span data-stu-id="b82b3-112">The following conditions may create an exception:</span></span>

- <span data-ttu-id="b82b3-113">Путь является недопустимым по одной из следующих причин: это строка нулевой длины; она содержит только пробелы; она содержит недопустимые знаки.</span><span class="sxs-lookup"><span data-stu-id="b82b3-113">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="b82b3-114">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="b82b3-114">(<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="b82b3-115">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="b82b3-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="b82b3-116">`File` указывает на путь, который не существует (<xref:System.IO.FileNotFoundException> или <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="b82b3-116">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="b82b3-117">Файл уже используется другим процессом или возникла ошибка ввода-вывода (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="b82b3-117">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="b82b3-118">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="b82b3-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="b82b3-119">Имя файла или каталога в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="b82b3-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="b82b3-120">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="b82b3-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="b82b3-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b82b3-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="b82b3-122">Практическое руководство. Запись текста в файлы</span><span class="sxs-lookup"><span data-stu-id="b82b3-122">How to: Write Text to Files</span></span>](how-to-write-text-to-files.md)
