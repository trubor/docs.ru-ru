---
description: 'Узнайте подробнее о: Доступ к файлам с помощью Visual Basic'
title: Доступ к файлам
ms.date: 07/20/2015
helpviewer_keywords:
- file access
- files [Visual Basic], input and output
- file access, Visual Basic
- files [Visual Basic], I/O
- file I/O classes
- data [Visual Basic], accessing from files
- files [Visual Basic], accessing
- file access, using components
- My.Computer.FileSystem object, accessing files
- I/O [Visual Basic]
- sequential access
ms.assetid: 231533bf-d049-4345-befa-3fb78fe6517d
ms.openlocfilehash: b3ea742185e7219ce7fdfb8eee987fd9c17e3a88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666320"
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="ae783-103">Доступ к файлам с помощью Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae783-103">File Access with Visual Basic</span></span>

<span data-ttu-id="ae783-104">Объект `My.Computer.FileSystem` предоставляет средства для работы с файлами и папками.</span><span class="sxs-lookup"><span data-stu-id="ae783-104">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="ae783-105">Его свойства, методы и события позволяют создавать, копировать, перемещать, исследовать и удалять файлы и папки.</span><span class="sxs-lookup"><span data-stu-id="ae783-105">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="ae783-106">`My.Computer.FileSystem` обеспечивает более высокую производительность, чем устаревшие функции (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput` и т. д.), предоставляемые Visual Basic для поддержки обратной совместимости.</span><span class="sxs-lookup"><span data-stu-id="ae783-106">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ae783-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="ae783-107">In This Section</span></span>  

 [<span data-ttu-id="ae783-108">Чтение из файлов</span><span class="sxs-lookup"><span data-stu-id="ae783-108">Reading from Files</span></span>](reading-from-files.md)  
 <span data-ttu-id="ae783-109">Список разделов, посвященных использованию объекта `My.Computer.FileSystem` для чтения из файлов.</span><span class="sxs-lookup"><span data-stu-id="ae783-109">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="ae783-110">Запись в файлы</span><span class="sxs-lookup"><span data-stu-id="ae783-110">Writing to Files</span></span>](writing-to-files.md)  
 <span data-ttu-id="ae783-111">Список разделов, посвященных использованию объекта `My.Computer.FileSystem` для записи в файлы.</span><span class="sxs-lookup"><span data-stu-id="ae783-111">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="ae783-112">Создание, удаление и перемещение файлов и каталогов</span><span class="sxs-lookup"><span data-stu-id="ae783-112">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="ae783-113">Список разделов, посвященных использованию объекта `My.Computer.FileSystem` для создания, копирования, удаления и перемещения файлов и папок.</span><span class="sxs-lookup"><span data-stu-id="ae783-113">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="ae783-114">Анализ текстовых файлов с помощью объекта TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="ae783-114">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="ae783-115">Описание использования объекта `TextFieldReader` для анализа таких текстовых файлов как журналов.</span><span class="sxs-lookup"><span data-stu-id="ae783-115">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="ae783-116">Кодировки файлов</span><span class="sxs-lookup"><span data-stu-id="ae783-116">File Encodings</span></span>](file-encodings.md)  
 <span data-ttu-id="ae783-117">Описание кодировок файлов и их применения.</span><span class="sxs-lookup"><span data-stu-id="ae783-117">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="ae783-118">Пошаговое руководство: Операции с файлами и каталогами в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae783-118">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="ae783-119">Демонстрация создания служебной программы, сообщающей сведения о файлах и папках.</span><span class="sxs-lookup"><span data-stu-id="ae783-119">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="ae783-120">Устранение неполадок: Чтение из текстовых файлов и запись в такие файлы</span><span class="sxs-lookup"><span data-stu-id="ae783-120">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="ae783-121">Список распространенных проблем, возникающих при чтении и записи в текстовые файлы, и предлагаемые способы их устранения.</span><span class="sxs-lookup"><span data-stu-id="ae783-121">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
