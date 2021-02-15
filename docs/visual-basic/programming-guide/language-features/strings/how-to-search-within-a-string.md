---
description: Дополнительные сведения см. в статье как искать в строке (Visual Basic)
title: Практические руководства. Поиск в строке
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: dab9faf91eef2e6d845805693227e1a6735ec796
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429732"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="ab5c7-103">Как выполнить поиск в строке (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab5c7-103">How to: search within a string (Visual Basic)</span></span>

<span data-ttu-id="ab5c7-104">В этой статье приведен пример поиска в строке в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-104">This article shows an example of how to search within a string in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="ab5c7-105">Пример</span><span class="sxs-lookup"><span data-stu-id="ab5c7-105">Example</span></span>

<span data-ttu-id="ab5c7-106">В этом примере вызывается <xref:System.String.IndexOf%2A> метод для <xref:System.String> объекта, чтобы сообщить индекс первого вхождения подстроки:</span><span class="sxs-lookup"><span data-stu-id="ab5c7-106">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring:</span></span>

 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]

## <a name="robust-programming"></a><span data-ttu-id="ab5c7-107">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="ab5c7-107">Robust programming</span></span>

<span data-ttu-id="ab5c7-108"><xref:System.String.IndexOf%2A>Метод возвращает расположение первого символа в первом вхождении подстроки.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-108">The <xref:System.String.IndexOf%2A> method returns the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="ab5c7-109">Индекс основан на 0, что означает, что первый символ строки имеет индекс 0.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-109">The index is 0-based, which means the first character of a string has an index of 0.</span></span>

<span data-ttu-id="ab5c7-110">Если не <xref:System.String.IndexOf%2A> находит подстроку, возвращается значение-1.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-110">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>

<span data-ttu-id="ab5c7-111"><xref:System.String.IndexOf%2A>Метод учитывает регистр и использует текущий язык и региональные параметры.</span><span class="sxs-lookup"><span data-stu-id="ab5c7-111">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>

<span data-ttu-id="ab5c7-112">Для оптимального управления ошибками может потребоваться заключить Поиск строки в `Try` блок [конструкции try... Перехватить... Построение оператора finally](../../../language-reference/statements/try-catch-finally-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="ab5c7-112">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md) construction.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab5c7-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ab5c7-113">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="ab5c7-114">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="ab5c7-114">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="ab5c7-115">Знакомство со строками в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab5c7-115">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="ab5c7-116">Строки</span><span class="sxs-lookup"><span data-stu-id="ab5c7-116">Strings</span></span>](index.md)
