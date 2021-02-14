---
description: Дополнительные сведения см. в статье как запросить предложения, содержащие указанный набор слов (LINQ) (Visual Basic)
title: Практическое руководство. Запрос к предложениям, содержащим указанный набор слов (LINQ)
ms.date: 07/20/2015
ms.assetid: a5ae8ced-61fe-4c10-bb8a-95630e50f603
ms.openlocfilehash: b6d2f428e499b8b22fa5bc13015f2405430c1bbd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100435100"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-visual-basic"></a><span data-ttu-id="12630-103">Практическое руководство. Запрос к предложениям, содержащим указанный набор слов (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12630-103">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="12630-104">В этом примере показан поиск предложений, содержащих совпадения для каждого из указанного набора слов в текстовом файле.</span><span class="sxs-lookup"><span data-stu-id="12630-104">This example shows how to find sentences in a text file that contain matches for each of a specified set of words.</span></span> <span data-ttu-id="12630-105">Хотя массив терминов для поиска в этом примере жестко закодирован, его можно заполнять динамически во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="12630-105">Although the array of search terms is hard-coded in this example, it could also be populated dynamically at runtime.</span></span> <span data-ttu-id="12630-106">В этом примере запрос возвращает предложения, которые содержат слова "Historically", "data" и "integrated".</span><span class="sxs-lookup"><span data-stu-id="12630-106">In this example, the query returns the sentences that contain the words "Historically," "data," and "integrated."</span></span>

## <a name="example"></a><span data-ttu-id="12630-107">Пример</span><span class="sxs-lookup"><span data-stu-id="12630-107">Example</span></span>

```vb
Class FindSentences

    Shared Sub Main()
        Dim text As String = "Historically, the world of data and the world of objects " &
        "have not been well integrated. Programmers work in C# or Visual Basic " &
        "and also in SQL or XQuery. On the one side are concepts such as classes, " &
        "objects, fields, inheritance, and .NET Framework APIs. On the other side " &
        "are tables, columns, rows, nodes, and separate languages for dealing with " &
        "them. Data types often require translation between the two worlds; there are " &
        "different standard functions. Because the object world has no notion of query, a " &
        "query can only be represented as a string without compile-time type checking or " &
        "IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " &
        "objects in memory is often tedious and error-prone."

        ' Split the text block into an array of sentences.
        Dim sentences As String() = text.Split(New Char() {".", "?", "!"})

        ' Define the search terms. This list could also be dynamically populated at runtime
        Dim wordsToMatch As String() = {"Historically", "data", "integrated"}

        ' Find sentences that contain all the terms in the wordsToMatch array
        ' Note that the number of terms to match is not specified at compile time
        Dim sentenceQuery = From sentence In sentences
                            Let w = sentence.Split(New Char() {" ", ",", ".", ";", ":"},
                                                   StringSplitOptions.RemoveEmptyEntries)
                            Where w.Distinct().Intersect(wordsToMatch).Count = wordsToMatch.Count()
                            Select sentence

        ' Execute the query
        For Each str As String In sentenceQuery
            Console.WriteLine(str)
        Next

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

End Class
' Output:
' Historically, the world of data and the world of objects have not been well integrated
```

<span data-ttu-id="12630-108">Запрос сначала разделяет текст на предложения, а затем разделяет предложения на массив строк, содержащих слова.</span><span class="sxs-lookup"><span data-stu-id="12630-108">The query works by first splitting the text into sentences, and then splitting the sentences into an array of strings that hold each word.</span></span> <span data-ttu-id="12630-109">Для каждого из этих массивов метод <xref:System.Linq.Enumerable.Distinct%2A> удаляет все повторяющиеся слова, после чего выполняет операцию <xref:System.Linq.Enumerable.Intersect%2A> в отношении массива слов и массива `wordsToMatch`.</span><span class="sxs-lookup"><span data-stu-id="12630-109">For each of these arrays, the <xref:System.Linq.Enumerable.Distinct%2A> method removes all duplicate words, and then the query performs an <xref:System.Linq.Enumerable.Intersect%2A> operation on the word array and the `wordsToMatch` array.</span></span> <span data-ttu-id="12630-110">Если число пересечений совпадает с размером массива `wordsToMatch`, все слова были найдены и возвращается исходное предложение.</span><span class="sxs-lookup"><span data-stu-id="12630-110">If the count of the intersection is the same as the count of the `wordsToMatch` array, all words were found in the words and the original sentence is returned.</span></span>

<span data-ttu-id="12630-111">В вызове <xref:System.String.Split%2A> знаки пунктуации используются как разделители для того, чтобы удалить их из строки.</span><span class="sxs-lookup"><span data-stu-id="12630-111">In the call to <xref:System.String.Split%2A>, the punctuation marks are used as separators in order to remove them from the string.</span></span> <span data-ttu-id="12630-112">Если этого не сделать, то, например, можно получить строку "Historically," которая не будет совпадать с "Historically" в массиве `wordsToMatch`.</span><span class="sxs-lookup"><span data-stu-id="12630-112">If you did not do this, for example you could have a string "Historically," that would not match "Historically" in the `wordsToMatch` array.</span></span> <span data-ttu-id="12630-113">В зависимости от знаков препинания в исходном тексте может потребоваться использовать дополнительные разделители.</span><span class="sxs-lookup"><span data-stu-id="12630-113">You may have to use additional separators, depending on the types of punctuation found in the source text.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="12630-114">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="12630-114">Compile the code</span></span>

<span data-ttu-id="12630-115">Создайте проект консольного приложения Visual Basic с `Imports` инструкцией для пространства имен System. LINQ.</span><span class="sxs-lookup"><span data-stu-id="12630-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="12630-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="12630-116">See also</span></span>

- [<span data-ttu-id="12630-117">LINQ и строки (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12630-117">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
