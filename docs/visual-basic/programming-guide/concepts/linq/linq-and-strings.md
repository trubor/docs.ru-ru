---
description: 'Дополнительные сведения: LINQ и строки (Visual Basic)'
title: LINQ и строки
ms.date: 07/20/2015
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
ms.openlocfilehash: 16e1a2c3d8cee30643743400ad21dfc4ff15c14d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100469790"
---
# <a name="linq-and-strings-visual-basic"></a><span data-ttu-id="367ca-103">LINQ и строки (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367ca-103">LINQ and Strings (Visual Basic)</span></span>

<span data-ttu-id="367ca-104">LINQ можно использовать для запроса и преобразования строк и коллекций строк.</span><span class="sxs-lookup"><span data-stu-id="367ca-104">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="367ca-105">При этом лучше всего его потенциал раскрывается при работе с частично структурированными данными в текстовых файлах.</span><span class="sxs-lookup"><span data-stu-id="367ca-105">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="367ca-106">Запросы LINQ можно комбинировать с традиционными строковыми функциями и регулярными выражениями.</span><span class="sxs-lookup"><span data-stu-id="367ca-106">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="367ca-107">Например, используя метод <xref:System.String.Split%2A> или <xref:System.Text.RegularExpressions.Regex.Split%2A>, можно создать массив строк, который затем можно запрашивать или изменять с помощью LINQ.</span><span class="sxs-lookup"><span data-stu-id="367ca-107">For example, you can use the <xref:System.String.Split%2A> or <xref:System.Text.RegularExpressions.Regex.Split%2A> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="367ca-108">Метод <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> можно использовать в предложении `where` запроса LINQ.</span><span class="sxs-lookup"><span data-stu-id="367ca-108">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="367ca-109">Также LINQ можно использовать для запроса или изменения результатов <xref:System.Text.RegularExpressions.MatchCollection>, возвращаемых регулярным выражением.</span><span class="sxs-lookup"><span data-stu-id="367ca-109">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>  
  
 <span data-ttu-id="367ca-110">Методы, описанные в этом разделе, позволяют преобразовать частично структурированные текстовые данные в XML.</span><span class="sxs-lookup"><span data-stu-id="367ca-110">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="367ca-111">Дополнительные сведения см. [в разделе инструкции. Создание XML из CSV-файлов](../../../../standard/linq/generate-xml-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="367ca-111">For more information, see [How to: Generate XML from CSV Files](../../../../standard/linq/generate-xml-csv-files.md).</span></span>  
  
 <span data-ttu-id="367ca-112">Примеры в этом разделе делятся на две категории:</span><span class="sxs-lookup"><span data-stu-id="367ca-112">The examples in this section fall into two categories:</span></span>  
  
## <a name="querying-a-block-of-text"></a><span data-ttu-id="367ca-113">Запрос блока текста</span><span class="sxs-lookup"><span data-stu-id="367ca-113">Querying a Block of Text</span></span>  

 <span data-ttu-id="367ca-114">Вы можете запрашивать, анализировать и изменять блоки текста, разбивая их на запрашиваемый массив строк меньшего размера с помощью методов <xref:System.String.Split%2A> или <xref:System.Text.RegularExpressions.Regex.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="367ca-114">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A> method.</span></span> <span data-ttu-id="367ca-115">Исходный текст можно разбить на слова, предложения, абзацы, страницы или другие фрагменты, а затем применить другие способы фрагментации, необходимые для вашего запроса.</span><span class="sxs-lookup"><span data-stu-id="367ca-115">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>  
  
 [<span data-ttu-id="367ca-116">Как подсчитать количество вхождений слова в строке (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367ca-116">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 <span data-ttu-id="367ca-117">Показывает, как использовать LINQ для простых запросов текста.</span><span class="sxs-lookup"><span data-stu-id="367ca-117">Shows how to use LINQ for simple querying over text.</span></span>  
  
 [<span data-ttu-id="367ca-118">Практическое руководство. Запрос к предложениям, содержащим указанный набор слов (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367ca-118">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 <span data-ttu-id="367ca-119">Показывает, как разбивать текстовые файлы на произвольные фрагменты и выполнять запросы к каждой части.</span><span class="sxs-lookup"><span data-stu-id="367ca-119">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>  
  
 [<span data-ttu-id="367ca-120">Как запросить символы в строке (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367ca-120">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>](how-to-query-for-characters-in-a-string-linq.md)  
 <span data-ttu-id="367ca-121">Показывает, что строка является запрашиваемым типом.</span><span class="sxs-lookup"><span data-stu-id="367ca-121">Demonstrates that a string is a queryable type.</span></span>  
  
 [<span data-ttu-id="367ca-122">Как сочетать запросы LINQ с помощью регулярных выражений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367ca-122">How to combine LINQ queries with regular expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)  
 <span data-ttu-id="367ca-123">Показывает, как выполнять сопоставление комплексных шаблонов с отфильтрованными результатами запросов, используя регулярные выражения в запросах LINQ.</span><span class="sxs-lookup"><span data-stu-id="367ca-123">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>  
  
## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="367ca-124">Запрос частично структурированных данных в текстовом формате</span><span class="sxs-lookup"><span data-stu-id="367ca-124">Querying Semi-Structured Data in Text Format</span></span>  

 <span data-ttu-id="367ca-125">Многие типы текстовых файлов состоят из серии строк, которые часто имеют одинаковый формат, например, из файлов с разделителями табуляцией или запятыми либо из строк фиксированной длины.</span><span class="sxs-lookup"><span data-stu-id="367ca-125">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="367ca-126">После того как текстовый файл будет считан в память, можно использовать LINQ для запроса и (или) изменения строк.</span><span class="sxs-lookup"><span data-stu-id="367ca-126">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="367ca-127">Кроме того, запросы LINQ упрощают задачу объединения данных из различных источников.</span><span class="sxs-lookup"><span data-stu-id="367ca-127">LINQ queries also simplify the task of combining data from multiple sources.</span></span>  
  
 [<span data-ttu-id="367ca-128">Как найти разность множеств между двумя списками (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367ca-128">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)  
 <span data-ttu-id="367ca-129">Показывает, как найти все строки, которые есть в одном списке, но отсутствуют в другом.</span><span class="sxs-lookup"><span data-stu-id="367ca-129">Shows how to find all the strings that are present in one list but not the other.</span></span>  
  
 [<span data-ttu-id="367ca-130">Практическое руководство. Сортировка или фильтрация текстовых данных по любому слову или полю (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367ca-130">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 <span data-ttu-id="367ca-131">Показывает, как сортировать текстовые строки по какому-либо слову или полю.</span><span class="sxs-lookup"><span data-stu-id="367ca-131">Shows how to sort text lines based on any word or field.</span></span>  
  
 [<span data-ttu-id="367ca-132">Как изменить порядок полей файла с разделителями (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367ca-132">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>](how-to-reorder-the-fields-of-a-delimited-file.md)  
 <span data-ttu-id="367ca-133">Показывает, как изменить порядок полей в строке CSV-файла.</span><span class="sxs-lookup"><span data-stu-id="367ca-133">Shows how to reorder fields in a line in a .csv file.</span></span>  
  
 [<span data-ttu-id="367ca-134">Практические руководства. объединение и сравнение коллекций строк (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367ca-134">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)  
 <span data-ttu-id="367ca-135">Показывает различные способы объединения списков строк.</span><span class="sxs-lookup"><span data-stu-id="367ca-135">Shows how to combine string lists in various ways.</span></span>  
  
 [<span data-ttu-id="367ca-136">Как заполнить коллекции объектов из нескольких источников (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367ca-136">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 <span data-ttu-id="367ca-137">Показывает, как создавать коллекции объектов, используя в качестве источников данных сразу несколько текстовых файлов.</span><span class="sxs-lookup"><span data-stu-id="367ca-137">Shows how to create object collections by using multiple text files as data sources.</span></span>  
  
 [<span data-ttu-id="367ca-138">Как присоединиться к содержимому из разнородных файлов (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367ca-138">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)  
 <span data-ttu-id="367ca-139">Показывает, как объединить строки из двух списков в одну строку, используя ключ сопоставления.</span><span class="sxs-lookup"><span data-stu-id="367ca-139">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>  
  
 [<span data-ttu-id="367ca-140">Инструкции. Разбиение файла на несколько файлов с помощью групп (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367ca-140">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 <span data-ttu-id="367ca-141">Показывает, как создавать файлы, используя в качестве источника данных одиночный файл.</span><span class="sxs-lookup"><span data-stu-id="367ca-141">Shows how to create new files by using a single file as a data source.</span></span>  
  
 [<span data-ttu-id="367ca-142">Руководство. Вычисление значений столбцов в текстовом файле CSV (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367ca-142">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 <span data-ttu-id="367ca-143">Показывает, как выполнять математические расчеты на основе текстовых данных в CSV-файлах.</span><span class="sxs-lookup"><span data-stu-id="367ca-143">Shows how to perform mathematical computations on text data in .csv files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="367ca-144">См. также</span><span class="sxs-lookup"><span data-stu-id="367ca-144">See also</span></span>

- [<span data-ttu-id="367ca-145">LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="367ca-145">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="367ca-146">Как создать XML из CSV-файлов</span><span class="sxs-lookup"><span data-stu-id="367ca-146">How to: Generate XML from CSV Files</span></span>](../../../../standard/linq/generate-xml-csv-files.md)
