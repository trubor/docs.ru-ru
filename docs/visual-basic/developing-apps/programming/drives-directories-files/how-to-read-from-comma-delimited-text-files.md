---
description: 'Узнайте подробнее о: Практическое руководство. Чтение из текстовых файлов с разделителями-запятыми в Visual Basic'
title: Практическое руководство. Чтение из текстовых файлов с разделителями-запятыми
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: dc4d4d5a7639ab7b5aa342aa8646b02985e40797
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797488"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="89612-103">Практическое руководство. Чтение из текстовых файлов с разделителями-запятыми в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89612-103">How to: read from comma-delimited text files in Visual Basic</span></span>

<span data-ttu-id="89612-104">Объект `TextFieldParser` позволяет легко и эффективно анализировать структурированные текстовые файлы, например файлы журналов.</span><span class="sxs-lookup"><span data-stu-id="89612-104">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="89612-105">Свойство `TextFieldType` определяет, является ли файл файлом с разделителями или с полями фиксированной ширины текста.</span><span class="sxs-lookup"><span data-stu-id="89612-105">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="89612-106">Анализ текстового файла с разделителями-запятыми</span><span class="sxs-lookup"><span data-stu-id="89612-106">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="89612-107">Создайте `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="89612-107">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="89612-108">Следующий код создает объект `TextFieldParser` с именем `MyReader` и открывает файл `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="89612-108">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="89612-109">Определение тип `TextField` и разделитель.</span><span class="sxs-lookup"><span data-stu-id="89612-109">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="89612-110">Следующий код определяет для свойства `TextFieldType` значение `Delimited`, а для разделителя — ",".</span><span class="sxs-lookup"><span data-stu-id="89612-110">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="89612-111">Просмотрите поля в файле.</span><span class="sxs-lookup"><span data-stu-id="89612-111">Loop through the fields in the file.</span></span> <span data-ttu-id="89612-112">Если какие-либо строки повреждены, выведите сообщение об ошибке и продолжите анализ.</span><span class="sxs-lookup"><span data-stu-id="89612-112">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="89612-113">Следующий код выполняет цикл по файлу, отображая каждое поле по очереди и сообщая обо всех полях с неправильным форматированием.</span><span class="sxs-lookup"><span data-stu-id="89612-113">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="89612-114">Закройте блоки `While` и `Using` операторами `End While` и `End Using`.</span><span class="sxs-lookup"><span data-stu-id="89612-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="89612-115">Пример</span><span class="sxs-lookup"><span data-stu-id="89612-115">Example</span></span>  

 <span data-ttu-id="89612-116">В этом примере производится чтение данных из файла `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="89612-116">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="89612-117">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="89612-117">Robust programming</span></span>  

 <span data-ttu-id="89612-118">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="89612-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="89612-119">Строка не может быть проанализирована с использованием указанного формата (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="89612-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="89612-120">Сообщение исключения содержит строку, вызвавшую исключение, а свойство <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> содержит текст, который содержится в этой строке.</span><span class="sxs-lookup"><span data-stu-id="89612-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
- <span data-ttu-id="89612-121">Указанный файл не существует (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="89612-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="89612-122">Ситуация частичного доверия, в которой пользователь не имеет достаточных разрешений для доступа к файлу.</span><span class="sxs-lookup"><span data-stu-id="89612-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="89612-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="89612-123">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="89612-124">Слишком длинный путь (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="89612-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="89612-125">У пользователя нет необходимых разрешений для доступа к файлу (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="89612-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89612-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="89612-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="89612-127">Практическое руководство. Чтение из текстовых файлов с полями фиксированного размера</span><span class="sxs-lookup"><span data-stu-id="89612-127">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="89612-128">Практическое руководство. Чтение из текстовых файлов различных форматов</span><span class="sxs-lookup"><span data-stu-id="89612-128">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="89612-129">Анализ текстовых файлов с помощью объекта TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="89612-129">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="89612-130">Пошаговое руководство: Операции с файлами и каталогами в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89612-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="89612-131">Устранение неполадок: Чтение из текстовых файлов и запись в такие файлы</span><span class="sxs-lookup"><span data-stu-id="89612-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
