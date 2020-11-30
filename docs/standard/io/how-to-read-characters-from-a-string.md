---
title: Практическое руководство. Считывание символов из строки
description: Узнайте, как считывать символы из строки в .NET. Ознакомьтесь с примерами синхронного и асинхронного чтения символов.
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
ms.openlocfilehash: beb3f4f38a5c28d19eff6fece5a6bb3c4e7a9c48
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734573"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="fa62f-104">Практическое руководство. Считывание символов из строки</span><span class="sxs-lookup"><span data-stu-id="fa62f-104">How to: Read characters from a string</span></span>

<span data-ttu-id="fa62f-105">Следующий пример кода демонстрирует синхронное и асинхронное чтение символов из строки.</span><span class="sxs-lookup"><span data-stu-id="fa62f-105">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="fa62f-106">Пример. Синхронное чтение символов</span><span class="sxs-lookup"><span data-stu-id="fa62f-106">Example: Read characters synchronously</span></span>

 <span data-ttu-id="fa62f-107">Этот пример синхронным образом считывает 13 символов из строки, сохраняет их в массиве и отображает.</span><span class="sxs-lookup"><span data-stu-id="fa62f-107">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="fa62f-108">Затем он считывает остальные символы строки, сохраняет их в массив, начиная с шестого элемента, и отображает содержимое массива.</span><span class="sxs-lookup"><span data-stu-id="fa62f-108">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="fa62f-109">Пример. Асинхронное чтение символов</span><span class="sxs-lookup"><span data-stu-id="fa62f-109">Example: Read characters asynchronously</span></span>  

 <span data-ttu-id="fa62f-110">Ниже приведен пример кода за приложением WPF.</span><span class="sxs-lookup"><span data-stu-id="fa62f-110">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="fa62f-111">При загрузке окна пример асинхронным способом считывает все символы из элемента управления <xref:System.Windows.Controls.TextBox> и сохраняет их в массиве.</span><span class="sxs-lookup"><span data-stu-id="fa62f-111">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="fa62f-112">Затем он асинхронно записывает все буквы и пробелы в элемент управления <xref:System.Windows.Controls.TextBlock>, размещая их на отдельных строках.</span><span class="sxs-lookup"><span data-stu-id="fa62f-112">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fa62f-113">См. также</span><span class="sxs-lookup"><span data-stu-id="fa62f-113">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="fa62f-114">Асинхронный файловый ввод-вывод</span><span class="sxs-lookup"><span data-stu-id="fa62f-114">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="fa62f-115">[Практическое руководство. Создание списка каталогов](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fa62f-115">[How to: Create a directory listing](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="fa62f-116">Практическое руководство. Считывание данных из нового файла и запись в этот файл</span><span class="sxs-lookup"><span data-stu-id="fa62f-116">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="fa62f-117">Практическое руководство. Открытие файла журнала и добавление в него данных</span><span class="sxs-lookup"><span data-stu-id="fa62f-117">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="fa62f-118">Практическое руководство. Чтение текста из файла</span><span class="sxs-lookup"><span data-stu-id="fa62f-118">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="fa62f-119">Практическое руководство. Запись текста в файл</span><span class="sxs-lookup"><span data-stu-id="fa62f-119">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="fa62f-120">Практическое руководство. Запись символов в строку</span><span class="sxs-lookup"><span data-stu-id="fa62f-120">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="fa62f-121">Файловый и потоковый ввод-вывод</span><span class="sxs-lookup"><span data-stu-id="fa62f-121">File and stream I/O</span></span>](index.md)
