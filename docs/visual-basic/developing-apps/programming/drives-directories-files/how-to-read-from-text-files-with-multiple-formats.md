---
description: 'Подробнее о следующем: Практическое руководство. Чтение текстовых файлов различных форматов в Visual Basic'
title: Практическое руководство. Чтение из текстовых файлов различных форматов
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: 90d981ad051fb395d57604434cf9ba6b74603e7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797449"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="2bd39-103">Практическое руководство. Чтение текстовых файлов различных форматов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2bd39-103">How to: Read from fext files with multiple formats in Visual Basic</span></span>

<span data-ttu-id="2bd39-104">Объект <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> позволяет легко и эффективно анализировать структурированные текстовые файлы, например файлы журналов.</span><span class="sxs-lookup"><span data-stu-id="2bd39-104">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="2bd39-105">Обработать файл, имеющий содержимое в нескольких форматах, можно с помощью метода `PeekChars`, который позволяет определять формат каждой анализируемой строки на протяжении всего файла.</span><span class="sxs-lookup"><span data-stu-id="2bd39-105">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="2bd39-106">Анализ текстового файла с содержимым в нескольких форматах</span><span class="sxs-lookup"><span data-stu-id="2bd39-106">To parse a text file with multiple formats</span></span>

1. <span data-ttu-id="2bd39-107">Добавьте текстовый файл с именем *testfile.txt* в проект.</span><span class="sxs-lookup"><span data-stu-id="2bd39-107">Add a text file named *testfile.txt* to your project.</span></span> <span data-ttu-id="2bd39-108">Добавьте в текстовый файл следующее содержимое:</span><span class="sxs-lookup"><span data-stu-id="2bd39-108">Add the following content to the text file:</span></span>

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. <span data-ttu-id="2bd39-109">Определите ожидаемый формат и формат, используемый при сообщении об ошибке.</span><span class="sxs-lookup"><span data-stu-id="2bd39-109">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="2bd39-110">Последним элементом в каждом массиве является -1, поэтому предполагается, что ширина последнего поля может изменяться.</span><span class="sxs-lookup"><span data-stu-id="2bd39-110">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="2bd39-111">Это происходит, когда последний элемент массива меньше или равен нулю.</span><span class="sxs-lookup"><span data-stu-id="2bd39-111">This occurs when the last entry in the array is less than or equal to 0.</span></span>

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. <span data-ttu-id="2bd39-112">Создайте объект <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>, определив ширину и формат.</span><span class="sxs-lookup"><span data-stu-id="2bd39-112">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. <span data-ttu-id="2bd39-113">Переберите в цикле строки, проверяя формат перед чтением.</span><span class="sxs-lookup"><span data-stu-id="2bd39-113">Loop through the rows, testing for format before reading.</span></span>

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. <span data-ttu-id="2bd39-114">Выведите сообщения об ошибках на консоль.</span><span class="sxs-lookup"><span data-stu-id="2bd39-114">Write errors to the console.</span></span>

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a><span data-ttu-id="2bd39-115">Пример</span><span class="sxs-lookup"><span data-stu-id="2bd39-115">Example</span></span>

<span data-ttu-id="2bd39-116">Далее приведен полный пример, считывающий из файла `testfile.txt`:</span><span class="sxs-lookup"><span data-stu-id="2bd39-116">The following is the complete example that reads from the file `testfile.txt`:</span></span>

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a><span data-ttu-id="2bd39-117">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="2bd39-117">Robust programming</span></span>

<span data-ttu-id="2bd39-118">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="2bd39-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="2bd39-119">Строка не может быть проанализирована с использованием указанного формата (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="2bd39-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="2bd39-120">Сообщение исключения содержит строку, вызвавшую исключение, а свойство <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> присвоено тексту, который содержится в этой строке.</span><span class="sxs-lookup"><span data-stu-id="2bd39-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>
- <span data-ttu-id="2bd39-121">Указанный файл не существует (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="2bd39-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>
- <span data-ttu-id="2bd39-122">Ситуация частичного доверия, в которой пользователь не имеет достаточных разрешений для доступа к файлу.</span><span class="sxs-lookup"><span data-stu-id="2bd39-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="2bd39-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="2bd39-123">(<xref:System.Security.SecurityException>).</span></span>
- <span data-ttu-id="2bd39-124">Слишком длинный путь (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="2bd39-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>
- <span data-ttu-id="2bd39-125">У пользователя нет необходимых разрешений для доступа к файлу (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="2bd39-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="2bd39-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2bd39-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [<span data-ttu-id="2bd39-127">Практическое руководство. Чтение из текстовых файлов с разделителями-запятыми</span><span class="sxs-lookup"><span data-stu-id="2bd39-127">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="2bd39-128">Практическое руководство. Чтение из текстовых файлов с полями фиксированного размера</span><span class="sxs-lookup"><span data-stu-id="2bd39-128">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="2bd39-129">Анализ текстовых файлов с помощью объекта TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="2bd39-129">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
