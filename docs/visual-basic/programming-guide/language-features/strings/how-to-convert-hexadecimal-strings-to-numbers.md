---
description: Дополнительные сведения см. в статье как преобразовать шестнадцатеричные строки в числа (Visual Basic)
title: Практическое руководство. Преобразование шестнадцатеричных строк в числа
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: cf1648b5f85f189f203f56cf569041e4f2db5ac3
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425547"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="c4970-103">Практическое руководство. Преобразование шестнадцатеричных строк в числа (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4970-103">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>

<span data-ttu-id="c4970-104">В этом примере шестнадцатеричная строка преобразуется в целое число с помощью <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> метода.</span><span class="sxs-lookup"><span data-stu-id="c4970-104">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="c4970-105">Преобразование шестнадцатеричной строки в число</span><span class="sxs-lookup"><span data-stu-id="c4970-105">To convert a hexadecimal string to a number</span></span>

- <span data-ttu-id="c4970-106">Используйте <xref:System.Convert.ToInt32(System.String,System.Int32)> метод для преобразования числа, выраженного в кодировке base-16, в целое число.</span><span class="sxs-lookup"><span data-stu-id="c4970-106">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>

  <span data-ttu-id="c4970-107">Первым аргументом <xref:System.Convert.ToInt32(System.String,System.Int32)> метода является Преобразуемая строка.</span><span class="sxs-lookup"><span data-stu-id="c4970-107">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="c4970-108">Второй аргумент описывает, в какой базе чисел выражается число. шестнадцатеричное число — основание 16.</span><span class="sxs-lookup"><span data-stu-id="c4970-108">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- <span data-ttu-id="c4970-109">Обратите внимание, что шестнадцатеричная строка имеет следующие ограничения.</span><span class="sxs-lookup"><span data-stu-id="c4970-109">Note that the hexadecimal string has the following restrictions:</span></span>

  - <span data-ttu-id="c4970-110">Он не может включать `&h` префикс.</span><span class="sxs-lookup"><span data-stu-id="c4970-110">It cannot include the `&h` prefix.</span></span>
  - <span data-ttu-id="c4970-111">Он не может включать `_` Разделитель цифр.</span><span class="sxs-lookup"><span data-stu-id="c4970-111">It cannot include the `_` digit separator.</span></span>

  <span data-ttu-id="c4970-112">Если указан префикс или разделитель цифр, вызов <xref:System.Convert.ToInt32(System.String,System.Int32)> метода создает исключение <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="c4970-112">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4970-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c4970-113">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
