---
description: 'Подробнее о следующем: Практическое руководство. Поиск подкаталогов по шаблону в Visual Basic'
title: Практическое руководство. Поиск подкаталогов по заданному шаблону
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: aaf1fe0e844c6a3db2b011289613a80dbd1b43fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797553"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="7eebc-103">Практическое руководство. Поиск подкаталогов по шаблону в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7eebc-103">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="7eebc-104">Метод <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> возвращает доступную только для чтения коллекцию строк, представляющих имена путей к подкаталогам каталога.</span><span class="sxs-lookup"><span data-stu-id="7eebc-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="7eebc-105">Для указания определенного шаблона можно использовать параметр `wildCards` .</span><span class="sxs-lookup"><span data-stu-id="7eebc-105">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="7eebc-106">Если требуется включить в поиск содержимое подкаталогов, присвойте параметру `searchType` значение `SearchOption.SearchAllSubDirectories`.</span><span class="sxs-lookup"><span data-stu-id="7eebc-106">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>

<span data-ttu-id="7eebc-107">Если каталоги, соответствующие указанному шаблону, не найдены, возвращается пустая коллекция.</span><span class="sxs-lookup"><span data-stu-id="7eebc-107">An empty collection is returned if no directories matching the specified pattern are found.</span></span>

## <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="7eebc-108">Поиск подкаталогов по заданному шаблону</span><span class="sxs-lookup"><span data-stu-id="7eebc-108">To find subdirectories with a specific pattern</span></span>

<span data-ttu-id="7eebc-109">Используйте метод `GetDirectories`, указав имя и путь к каталогу для поиска.</span><span class="sxs-lookup"><span data-stu-id="7eebc-109">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="7eebc-110">В следующем примере возвращаются все каталоги в структуре каталогов, имена которых содержат слово "Logs". Затем они добавляются в `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="7eebc-110">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a><span data-ttu-id="7eebc-111">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="7eebc-111">Robust Programming</span></span>

<span data-ttu-id="7eebc-112">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="7eebc-112">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="7eebc-113">Путь является недопустимым, так как он представляет собой строку нулевой длины (пустую строку), либо содержит только пробелы, либо содержит недопустимые знаки, либо представляет собой путь к устройству (начинается с символов \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="7eebc-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="7eebc-114">Путь не является допустимым, поскольку он равен `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="7eebc-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="7eebc-115">Один или несколько указанных подстановочных знаков являются `Nothing`, пустой строкой или содержат только пробелы (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="7eebc-115">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="7eebc-116">`directory` не существует (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="7eebc-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="7eebc-117">`directory` указывает на существующий файл (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="7eebc-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="7eebc-118">Длина пути превышает максимальную длину, определенную в системе (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="7eebc-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="7eebc-119">Имя файла или папки в пути содержит двоеточие (:) или имеет недопустимый формат (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="7eebc-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="7eebc-120">У пользователя отсутствуют необходимые разрешения на просмотр пути (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="7eebc-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="7eebc-121">У пользователя отсутствуют необходимые разрешения (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="7eebc-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="7eebc-122">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7eebc-122">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="7eebc-123">Практическое руководство. Поиск файлов по конкретному шаблону</span><span class="sxs-lookup"><span data-stu-id="7eebc-123">How to: Find Files with a Specific Pattern</span></span>](how-to-find-files-with-a-specific-pattern.md)
