---
description: Дополнительные сведения см. в статье как создать строку из массива значений типа char (Visual Basic)
title: Практическое руководство. Создание строки из значений массива символьного типа
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 67b675f5f02c92b785e374b99f49248d43d12fb4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429836"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="87538-103">Практическое руководство. Создание строки из значений массива символьного типа (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87538-103">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>

<span data-ttu-id="87538-104">В этом примере создается строка «ABCD» из отдельных символов.</span><span class="sxs-lookup"><span data-stu-id="87538-104">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87538-105">Пример</span><span class="sxs-lookup"><span data-stu-id="87538-105">Example</span></span>  

 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="87538-106">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="87538-106">Compile the code</span></span>  

 <span data-ttu-id="87538-107">Этот метод не имеет особых требований.</span><span class="sxs-lookup"><span data-stu-id="87538-107">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="87538-108">Синтаксис `"a"c` , где один `c` символ следует за одиночным знаком в кавычках, используется для создания символьного литерала.</span><span class="sxs-lookup"><span data-stu-id="87538-108">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="87538-109">Отказоустойчивость</span><span class="sxs-lookup"><span data-stu-id="87538-109">Robust Programming</span></span>  

 <span data-ttu-id="87538-110">Символы NULL (эквивалентны `Chr(0)` ) в строке ведут к непредвиденным результатам при использовании строки.</span><span class="sxs-lookup"><span data-stu-id="87538-110">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="87538-111">Символ null будет включаться в строку, но символы, следующие за символом NULL, не будут отображаться в некоторых ситуациях.</span><span class="sxs-lookup"><span data-stu-id="87538-111">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87538-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="87538-112">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="87538-113">Тип данных Char</span><span class="sxs-lookup"><span data-stu-id="87538-113">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="87538-114">Типы данных</span><span class="sxs-lookup"><span data-stu-id="87538-114">Data Types</span></span>](../data-types/index.md)
