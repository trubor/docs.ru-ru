---
title: Практическое руководство. открытие файла журнала и добавление в него данных
description: Открывайте файл журнала и добавляйте в него данные с помощью классов StreamWriter и StreamReader в .NET, которые записывают символы в потоки и считывают символы из них.
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
ms.openlocfilehash: be4cacee8d0a529730c66c5850f42330520ba2d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734612"
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="d1b01-103">Практическое руководство. открытие файла журнала и добавление в него данных</span><span class="sxs-lookup"><span data-stu-id="d1b01-103">How to: Open and append to a log file</span></span>

<span data-ttu-id="d1b01-104"><xref:System.IO.StreamWriter> и <xref:System.IO.StreamReader> записывают данные в потоки и считывают данные из потоков.</span><span class="sxs-lookup"><span data-stu-id="d1b01-104"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="d1b01-105">Следующий пример кода открывает файл *log.txt* для получения входных данных или создает его, если он не существует, а затем добавляет сведения журнала в конец файла.</span><span class="sxs-lookup"><span data-stu-id="d1b01-105">The following code example opens the *log.txt* file for input, or creates it if it doesn't exist, and appends log information to the end of the file.</span></span> <span data-ttu-id="d1b01-106">После этого он записывает содержимое файла для отображения в стандартный поток вывода.</span><span class="sxs-lookup"><span data-stu-id="d1b01-106">The example then writes the contents of the file to standard output for display.</span></span>

<span data-ttu-id="d1b01-107">Вместо использованного здесь подхода вы можете сохранить сведения в одной строке или в массиве строк и выполнить те же функции с помощью метода <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> или <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d1b01-107">As an alternative to this example, you could store the information as a single string or string array, and use the <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> or <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> method to achieve the same functionality.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1b01-108">Пользователи Visual Basic могут использовать методы и свойства, предоставляемые классом <xref:Microsoft.VisualBasic.Logging.Log> или <xref:Microsoft.VisualBasic.FileIO.FileSystem>, для создания файлов журнала и записи данных в них.</span><span class="sxs-lookup"><span data-stu-id="d1b01-108">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1b01-109">Пример</span><span class="sxs-lookup"><span data-stu-id="d1b01-109">Example</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d1b01-110">См. также</span><span class="sxs-lookup"><span data-stu-id="d1b01-110">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="d1b01-111">Практическое руководство. Перечисление каталогов и файлов</span><span class="sxs-lookup"><span data-stu-id="d1b01-111">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="d1b01-112">Практическое руководство. Считывание данных из нового файла и запись в этот файл</span><span class="sxs-lookup"><span data-stu-id="d1b01-112">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="d1b01-113">Практическое руководство. Чтение текста из файла</span><span class="sxs-lookup"><span data-stu-id="d1b01-113">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="d1b01-114">Практическое руководство. Запись текста в файл</span><span class="sxs-lookup"><span data-stu-id="d1b01-114">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="d1b01-115">Практическое руководство. Считывание символов из строки</span><span class="sxs-lookup"><span data-stu-id="d1b01-115">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="d1b01-116">Практическое руководство. Запись символов в строку</span><span class="sxs-lookup"><span data-stu-id="d1b01-116">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="d1b01-117">Файловый и потоковый ввод-вывод</span><span class="sxs-lookup"><span data-stu-id="d1b01-117">File and stream I/O</span></span>](index.md)
