---
description: Дополнительные сведения см. в статье как получить доступ к символам в строках в Visual Basic
title: Практическое руководство. Доступ к символам в строках
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 373005699483dbae92df3a6fe73cc9b6318a9c61
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476167"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="604f2-103">Практическое руководство. Доступ к символам строк в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="604f2-103">How to: Access Characters in Strings in Visual Basic</span></span>

<span data-ttu-id="604f2-104">В этом примере показано, как использовать <xref:System.String.Chars%2A> свойство для доступа к символу в указанном месте в строке.</span><span class="sxs-lookup"><span data-stu-id="604f2-104">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="604f2-105">Пример</span><span class="sxs-lookup"><span data-stu-id="604f2-105">Example</span></span>  

 <span data-ttu-id="604f2-106">Иногда бывает полезно иметь данные о символах в строке и позициях этих символов в строке.</span><span class="sxs-lookup"><span data-stu-id="604f2-106">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="604f2-107">Строку можно представить как массив символов ( `Char` экземпляров); вы можете получить определенный символ, обратившись к индексу этого символа через <xref:System.String.Chars%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="604f2-107">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="604f2-108">Параметр свойства отсчитывается `index` <xref:System.String.Chars%2A> от нуля.</span><span class="sxs-lookup"><span data-stu-id="604f2-108">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="604f2-109">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="604f2-109">Robust Programming</span></span>  

 <span data-ttu-id="604f2-110"><xref:System.String.Chars%2A>Свойство возвращает символ в указанной позиции.</span><span class="sxs-lookup"><span data-stu-id="604f2-110">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="604f2-111">Однако некоторые символы Юникода могут быть представлены более чем одним символом.</span><span class="sxs-lookup"><span data-stu-id="604f2-111">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="604f2-112">Дополнительные сведения о работе с символами Юникода см. в разделе [инструкции. Преобразование строки в массив символов](how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="604f2-112">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="604f2-113"><xref:System.String.Chars%2A>Свойство вызывает исключение, <xref:System.IndexOutOfRangeException> Если `index` параметр больше или равен длине строки или если он меньше нуля.</span><span class="sxs-lookup"><span data-stu-id="604f2-113">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="604f2-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="604f2-114">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="604f2-115">Практическое руководство. Преобразование строки в массив символов</span><span class="sxs-lookup"><span data-stu-id="604f2-115">How to: Convert a String to an Array of Characters</span></span>](how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="604f2-116">Преобразование между строками и другими типами данных в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="604f2-116">Converting Between Strings and Other Data Types in Visual Basic</span></span>](converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="604f2-117">Строки</span><span class="sxs-lookup"><span data-stu-id="604f2-117">Strings</span></span>](index.md)
