---
title: Практическое руководство. Копирование каталогов
description: Сведения о том, как копировать каталоги с помощью классов ввода-вывода, осуществляющих синхронное копирование содержимого каталога в другое место.
ms.date: 12/27/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET], copying directories
- subdirectory copying
- copying directories
- directories [.NET], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: dfe45d8529eb927a6b174a7bb411afa8072035f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679069"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="35215-103">Практическое руководство. Копирование каталогов</span><span class="sxs-lookup"><span data-stu-id="35215-103">How to: Copy directories</span></span>

<span data-ttu-id="35215-104">В этой статье демонстрируется использование классов ввода-вывода для синхронного копирования содержимого каталога в другое место.</span><span class="sxs-lookup"><span data-stu-id="35215-104">This article demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span>

<span data-ttu-id="35215-105">Пример асинхронного копирования файлов см. в разделе [Асинхронный файловый ввод-вывод](asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="35215-105">For an example of asynchronous file copy, see [Asynchronous file I/O](asynchronous-file-i-o.md).</span></span>

<span data-ttu-id="35215-106">В этом примере для копирования подкаталогов объекту `copySubDirs` метода `DirectoryCopy` присваивается значение `true`.</span><span class="sxs-lookup"><span data-stu-id="35215-106">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="35215-107">Метод `DirectoryCopy` выполняет рекурсивное копирование подкаталогов путем вызова самого себя для каждого последующего подкаталога, пока не будет скопировано все.</span><span class="sxs-lookup"><span data-stu-id="35215-107">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35215-108">Пример</span><span class="sxs-lookup"><span data-stu-id="35215-108">Example</span></span>  

 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="35215-109">См. также</span><span class="sxs-lookup"><span data-stu-id="35215-109">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="35215-110">Файловый и потоковый ввод-вывод</span><span class="sxs-lookup"><span data-stu-id="35215-110">File and stream I/O</span></span>](index.md)
- [<span data-ttu-id="35215-111">Распространенные задачи ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="35215-111">Common I/O tasks</span></span>](common-i-o-tasks.md)
- [<span data-ttu-id="35215-112">Асинхронный файловый ввод-вывод</span><span class="sxs-lookup"><span data-stu-id="35215-112">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)
