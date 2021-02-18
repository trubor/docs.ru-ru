---
title: Руководство по программированию на C#. Запись в текстовый файл
description: Узнайте, как выполнить запись данных в текстовый файл на C#. Изучите несколько примеров кода и ознакомьтесь с дополнительными ресурсами.
ms.date: 02/11/2021
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.topic: how-to
ms.custom: contperf-fy21q3
ms.openlocfilehash: ecc3ba73161d4f4571bbc6ae0c9aaa3337586ef7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475621"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="34e56-104">Руководство по программированию на C#. Запись в текстовый файл</span><span class="sxs-lookup"><span data-stu-id="34e56-104">How to write to a text file (C# Programming Guide)</span></span>

<span data-ttu-id="34e56-105">В этой статье есть несколько примеров, демонстрирующих различные способы записи текста в файл.</span><span class="sxs-lookup"><span data-stu-id="34e56-105">In this article, there are several examples showing various ways to write text to a file.</span></span> <span data-ttu-id="34e56-106">В первых двух примерах используются удобные статические методы класса <xref:System.IO.File?displayProperty=nameWithType> для записи каждого элемента любого объекта `IEnumerable<string>` и `string` в текстовый файл.</span><span class="sxs-lookup"><span data-stu-id="34e56-106">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any `IEnumerable<string>` and a `string` to a text file.</span></span> <span data-ttu-id="34e56-107">В третьем примере показано, как добавить текст в файл, если необходимо обрабатывать отдельно каждую строку по мере ее записи в файл.</span><span class="sxs-lookup"><span data-stu-id="34e56-107">The third example shows how to add text to a file when you have to process each line individually as you write to the file.</span></span> <span data-ttu-id="34e56-108">В первых трех примерах происходит перезапись всего существующего содержимого файла.</span><span class="sxs-lookup"><span data-stu-id="34e56-108">In the first three examples, you overwrite all existing content in the file.</span></span> <span data-ttu-id="34e56-109">В последнем примере показано, как добавить текст в существующий файл.</span><span class="sxs-lookup"><span data-stu-id="34e56-109">The final example shows how to append text to an existing file.</span></span>

 <span data-ttu-id="34e56-110">Все эти примеры записывают строковые литералы в файлы.</span><span class="sxs-lookup"><span data-stu-id="34e56-110">These examples all write string literals to files.</span></span> <span data-ttu-id="34e56-111">Чтобы отформатировать записываемый в файл текст, воспользуйтесь методом <xref:System.String.Format%2A> или функцией [интерполяции строк](../../language-reference/tokens/interpolated.md) C#.</span><span class="sxs-lookup"><span data-stu-id="34e56-111">If you want to format text written to a file, use the <xref:System.String.Format%2A> method or C# [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>

## <a name="write-a-collection-of-strings-to-a-file"></a><span data-ttu-id="34e56-112">Запись коллекции строк в файл</span><span class="sxs-lookup"><span data-stu-id="34e56-112">Write a collection of strings to a file</span></span>

:::code language="csharp" source="snippets/write-text/WriteAllLines.cs":::

<span data-ttu-id="34e56-113">Предыдущий пример исходного кода:</span><span class="sxs-lookup"><span data-stu-id="34e56-113">The preceding source code example:</span></span>

- <span data-ttu-id="34e56-114">Создает экземпляр массива строк с тремя значениями.</span><span class="sxs-lookup"><span data-stu-id="34e56-114">Instantiates a string array with three values.</span></span>
- <span data-ttu-id="34e56-115">Ожидает вызов <xref:System.IO.File.WriteAllLinesAsync%2A?displayProperty=nameWithType>, который:</span><span class="sxs-lookup"><span data-stu-id="34e56-115">Awaits a call to <xref:System.IO.File.WriteAllLinesAsync%2A?displayProperty=nameWithType> which:</span></span>

  - <span data-ttu-id="34e56-116">Асинхронно создает имя файла *WriteLines.txt*.</span><span class="sxs-lookup"><span data-stu-id="34e56-116">Asynchronously creates a file name *WriteLines.txt*.</span></span> <span data-ttu-id="34e56-117">Если целевой файл уже существует, он будет перезаписан.</span><span class="sxs-lookup"><span data-stu-id="34e56-117">If the file already exists, it is overwritten.</span></span>
  - <span data-ttu-id="34e56-118">Записывает заданные строки в файл.</span><span class="sxs-lookup"><span data-stu-id="34e56-118">Writes the given lines to the file.</span></span>
  - <span data-ttu-id="34e56-119">Закрывает файл, выполняет автоматическую очистку и удаление по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="34e56-119">Closes the file, automatically flushing and disposing as needed.</span></span>

## <a name="write-one-string-to-a-file"></a><span data-ttu-id="34e56-120">Запись одной строки в файл</span><span class="sxs-lookup"><span data-stu-id="34e56-120">Write one string to a file</span></span>

:::code language="csharp" source="snippets/write-text/WriteAllText.cs":::

<span data-ttu-id="34e56-121">Предыдущий пример исходного кода:</span><span class="sxs-lookup"><span data-stu-id="34e56-121">The preceding source code example:</span></span>

- <span data-ttu-id="34e56-122">Создает экземпляр строки с заданным назначенным строковым литералом.</span><span class="sxs-lookup"><span data-stu-id="34e56-122">Instantiates a string given the assigned string literal.</span></span>
- <span data-ttu-id="34e56-123">Ожидает вызов <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType>, который:</span><span class="sxs-lookup"><span data-stu-id="34e56-123">Awaits a call to <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> which:</span></span>

  - <span data-ttu-id="34e56-124">Асинхронно создает имя файла *WriteText.txt*.</span><span class="sxs-lookup"><span data-stu-id="34e56-124">Asynchronously creates a file name *WriteText.txt*.</span></span> <span data-ttu-id="34e56-125">Если целевой файл уже существует, он будет перезаписан.</span><span class="sxs-lookup"><span data-stu-id="34e56-125">If the file already exists, it is overwritten.</span></span>
  - <span data-ttu-id="34e56-126">Записывает заданный текст в файл.</span><span class="sxs-lookup"><span data-stu-id="34e56-126">Writes the given text to the file.</span></span>
  - <span data-ttu-id="34e56-127">Закрывает файл, выполняет автоматическую очистку и удаление по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="34e56-127">Closes the file, automatically flushing and disposing as needed.</span></span>

## <a name="write-selected-strings-from-an-array-to-a-file"></a><span data-ttu-id="34e56-128">Запись выбранных строк из массива в файл</span><span class="sxs-lookup"><span data-stu-id="34e56-128">Write selected strings from an array to a file</span></span>

:::code language="csharp" source="snippets/write-text/StreamWriterOne.cs":::

<span data-ttu-id="34e56-129">Предыдущий пример исходного кода:</span><span class="sxs-lookup"><span data-stu-id="34e56-129">The preceding source code example:</span></span>

- <span data-ttu-id="34e56-130">Создает экземпляр массива строк с тремя значениями.</span><span class="sxs-lookup"><span data-stu-id="34e56-130">Instantiates a string array with three values.</span></span>
- <span data-ttu-id="34e56-131">Создает экземпляр <xref:System.IO.StreamWriter> с путем к файлу *WriteLines2.txt* как [с помощью объявления](../../whats-new/csharp-8.md#using-declarations).</span><span class="sxs-lookup"><span data-stu-id="34e56-131">Instantiates a <xref:System.IO.StreamWriter> with a file path of *WriteLines2.txt* as a [using declaration](../../whats-new/csharp-8.md#using-declarations).</span></span>
- <span data-ttu-id="34e56-132">Выполняет итерацию по всем строкам.</span><span class="sxs-lookup"><span data-stu-id="34e56-132">Iterates through all the lines.</span></span>
- <span data-ttu-id="34e56-133">Условно ожидает вызов <xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType>, который записывает строку в файл, если строка не содержит `"Second"`.</span><span class="sxs-lookup"><span data-stu-id="34e56-133">Conditionally awaits a call to <xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType>, which writes the line to the file when the line doesn't contain `"Second"`.</span></span>

## <a name="append-text-to-an-existing-file"></a><span data-ttu-id="34e56-134">Добавление текста в существующий файл</span><span class="sxs-lookup"><span data-stu-id="34e56-134">Append text to an existing file</span></span>

:::code language="csharp" source="snippets/write-text/StreamWriterTwo.cs":::

<span data-ttu-id="34e56-135">Предыдущий пример исходного кода:</span><span class="sxs-lookup"><span data-stu-id="34e56-135">The preceding source code example:</span></span>

- <span data-ttu-id="34e56-136">Создает экземпляр массива строк с тремя значениями.</span><span class="sxs-lookup"><span data-stu-id="34e56-136">Instantiates a string array with three values.</span></span>
- <span data-ttu-id="34e56-137">Создает экземпляр <xref:System.IO.StreamWriter> с путем к файлу *WriteLines2.txt* как [с помощью объявления](../../whats-new/csharp-8.md#using-declarations), передавая `true` для добавления.</span><span class="sxs-lookup"><span data-stu-id="34e56-137">Instantiates a <xref:System.IO.StreamWriter> with a file path of *WriteLines2.txt* as a [using declaration](../../whats-new/csharp-8.md#using-declarations), passing in `true` to append.</span></span>
- <span data-ttu-id="34e56-138">Ожидает вызов <xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType>, который записывает строку в файл как добавленную строку.</span><span class="sxs-lookup"><span data-stu-id="34e56-138">Awaits a call to <xref:System.IO.StreamWriter.WriteLineAsync(System.String)?displayProperty=nameWithType>, which writes the string to the file as an appended line.</span></span>

## <a name="exceptions"></a><span data-ttu-id="34e56-139">Исключения</span><span class="sxs-lookup"><span data-stu-id="34e56-139">Exceptions</span></span>

<span data-ttu-id="34e56-140">При следующих условиях возможно возникновение исключения:</span><span class="sxs-lookup"><span data-stu-id="34e56-140">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="34e56-141"><xref:System.InvalidOperationException>: Файл существует и является файлом только для чтения.</span><span class="sxs-lookup"><span data-stu-id="34e56-141"><xref:System.InvalidOperationException>: The file exists and is read-only.</span></span>
- <span data-ttu-id="34e56-142"><xref:System.IO.PathTooLongException>: Имя пути имеет слишком большую длину.</span><span class="sxs-lookup"><span data-stu-id="34e56-142"><xref:System.IO.PathTooLongException>: The path name may be too long.</span></span>
- <span data-ttu-id="34e56-143"><xref:System.IO.IOException>: Диск может быть переполнен.</span><span class="sxs-lookup"><span data-stu-id="34e56-143"><xref:System.IO.IOException>: The disk may be full.</span></span>

<span data-ttu-id="34e56-144">Существуют дополнительные условия, которые могут привести к возникновению исключений при работе с файловой системой, поэтому программировать следует с осторожностью.</span><span class="sxs-lookup"><span data-stu-id="34e56-144">There are additional conditions that may cause exceptions when working with the file system, it is best to program defensively.</span></span>

## <a name="see-also"></a><span data-ttu-id="34e56-145">См. также</span><span class="sxs-lookup"><span data-stu-id="34e56-145">See also</span></span>

- [<span data-ttu-id="34e56-146">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="34e56-146">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="34e56-147">Файловая система и реестр (руководство по программированию на C#)</span><span class="sxs-lookup"><span data-stu-id="34e56-147">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="34e56-148">Пример. Сохранение коллекции настраиваемых объектов в локальном хранилище</span><span class="sxs-lookup"><span data-stu-id="34e56-148">Sample: Save a collection to Application Storage</span></span>](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
