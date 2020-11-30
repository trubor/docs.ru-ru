---
title: Практическое руководство. Чтение текста из файла
description: В этой статье приведены примеры синхронного и асинхронного чтения текста из текстового файла с помощью класса StreamReader в .NET для классических приложений.
ms.date: 01/03/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
ms.openlocfilehash: 48b862ff77bf4ace48a5481fe9bedcf354b5654b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725343"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="959b8-103">Практическое руководство. Чтение текста из файла</span><span class="sxs-lookup"><span data-stu-id="959b8-103">How to: Read text from a file</span></span>

<span data-ttu-id="959b8-104">В следующих примерах демонстрируется синхронное и асинхронное чтение текста из текстового файла с использованием .NET для классических приложений.</span><span class="sxs-lookup"><span data-stu-id="959b8-104">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="959b8-105">В обоих примерах при создании экземпляра класса <xref:System.IO.StreamReader> указывается относительный или абсолютный путь к файлу.</span><span class="sxs-lookup"><span data-stu-id="959b8-105">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="959b8-106">Эти примеры кода не относятся к приложениям универсальной платформы Windows (UWP), так как в среде выполнения Windows используются разные типы потоков для чтения и записи файлов.</span><span class="sxs-lookup"><span data-stu-id="959b8-106">These code examples do not apply to Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="959b8-107">Пример чтения текста из файла в приложении UWP см. в разделе [Краткое руководство. Чтение и запись файлов](/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="959b8-107">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="959b8-108">Примеры, демонстрирующие преобразование потоков .NET Framework в потоки среды выполнения Windows и наоборот, см. в разделе [Практическое руководство. Преобразование между потоками .NET Framework и потоками среды выполнения Windows](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="959b8-108">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="959b8-109">Пример. Синхронное чтение в консольном приложении</span><span class="sxs-lookup"><span data-stu-id="959b8-109">Example: Synchronous read in a console app</span></span>  

<span data-ttu-id="959b8-110">Следующий пример иллюстрирует синхронную операцию чтения в консольном приложении.</span><span class="sxs-lookup"><span data-stu-id="959b8-110">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="959b8-111">В этом примере текстовый файл открывается с помощью модуля чтения потока, содержимое копируется в строку, а строка выводится в консоли.</span><span class="sxs-lookup"><span data-stu-id="959b8-111">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="959b8-112">В примерах предполагается, что файл с именем *TestFile.txt* уже существует в той же папке, что и приложение.</span><span class="sxs-lookup"><span data-stu-id="959b8-112">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/sync-console/Program.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/sync-console/Program.vb":::
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="959b8-113">Пример. Асинхронное чтение в приложении WPF</span><span class="sxs-lookup"><span data-stu-id="959b8-113">Example: Asynchronous read in a WPF app</span></span>

 <span data-ttu-id="959b8-114">Следующий пример иллюстрирует асинхронную операцию чтения в приложении Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="959b8-114">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="959b8-115">В примерах предполагается, что файл с именем *TestFile.txt* уже существует в той же папке, что и приложение.</span><span class="sxs-lookup"><span data-stu-id="959b8-115">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/async-wpf/MainWindow.xaml.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/async-wpf/MainWindow.xaml.vb":::
  
## <a name="see-also"></a><span data-ttu-id="959b8-116">См. также</span><span class="sxs-lookup"><span data-stu-id="959b8-116">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="959b8-117">Асинхронный файловый ввод-вывод</span><span class="sxs-lookup"><span data-stu-id="959b8-117">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="959b8-118">[Практическое руководство. Создание списка каталогов](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="959b8-118">[How to: Create a directory listing](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- <span data-ttu-id="959b8-119">[Краткое руководство. Чтение и запись файлов](/previous-versions/windows/apps/hh758325(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="959b8-119">[Quickstart: Reading and writing files](/previous-versions/windows/apps/hh758325(v=win.10))</span></span>  
- [<span data-ttu-id="959b8-120">Практическое руководство. Преобразование между потоками .NET Framework и потоками среды выполнения Windows</span><span class="sxs-lookup"><span data-stu-id="959b8-120">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="959b8-121">Практическое руководство. Считывание данных из нового файла и запись в этот файл</span><span class="sxs-lookup"><span data-stu-id="959b8-121">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="959b8-122">Практическое руководство. Открытие файла журнала и добавление в него данных</span><span class="sxs-lookup"><span data-stu-id="959b8-122">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="959b8-123">Практическое руководство. Запись текста в файл</span><span class="sxs-lookup"><span data-stu-id="959b8-123">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="959b8-124">Практическое руководство. Считывание символов из строки</span><span class="sxs-lookup"><span data-stu-id="959b8-124">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="959b8-125">Практическое руководство. Запись символов в строку</span><span class="sxs-lookup"><span data-stu-id="959b8-125">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="959b8-126">Файловый и потоковый ввод-вывод</span><span class="sxs-lookup"><span data-stu-id="959b8-126">File and stream I/O</span></span>](index.md)
