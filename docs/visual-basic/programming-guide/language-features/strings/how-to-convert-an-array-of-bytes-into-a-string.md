---
description: Дополнительные сведения см. в статье как преобразовать массив байтов в строку в Visual Basic
title: Практическое руководство. Преобразование массива байтов в строку
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: ded4a2c4c235e560198ef2edd4c5031141554079
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425572"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="58ad8-103">Практическое руководство. Преобразование массива байтов в строку в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="58ad8-103">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>

<span data-ttu-id="58ad8-104">В этом разделе показано, как преобразовать байты из массива байтов в строку.</span><span class="sxs-lookup"><span data-stu-id="58ad8-104">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58ad8-105">Пример</span><span class="sxs-lookup"><span data-stu-id="58ad8-105">Example</span></span>  

 <span data-ttu-id="58ad8-106">В этом примере используется <xref:System.Text.Encoding.GetString%2A> метод <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> класса Encoding для преобразования всех байтов из массива байтов в строку.</span><span class="sxs-lookup"><span data-stu-id="58ad8-106">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 <span data-ttu-id="58ad8-107">Можно выбрать один из нескольких параметров кодировки для преобразования массива байтов в строку:</span><span class="sxs-lookup"><span data-stu-id="58ad8-107">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
- <span data-ttu-id="58ad8-108"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Получает кодировку для набора символов ASCII (7-разрядных).</span><span class="sxs-lookup"><span data-stu-id="58ad8-108"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
- <span data-ttu-id="58ad8-109"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Получает кодировку для формата UTF-16 с обратным порядком байтов.</span><span class="sxs-lookup"><span data-stu-id="58ad8-109"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
- <span data-ttu-id="58ad8-110"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Получает кодировку для текущей системной кодовой страницы ANSI.</span><span class="sxs-lookup"><span data-stu-id="58ad8-110"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
- <span data-ttu-id="58ad8-111"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Получает кодировку для формата UTF-16 с прямым порядком байтов.</span><span class="sxs-lookup"><span data-stu-id="58ad8-111"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="58ad8-112"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Получает кодировку для формата UTF-32 с прямым порядком байтов.</span><span class="sxs-lookup"><span data-stu-id="58ad8-112"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="58ad8-113"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Получает кодировку для формата UTF-7.</span><span class="sxs-lookup"><span data-stu-id="58ad8-113"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
- <span data-ttu-id="58ad8-114"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Получает кодировку для формата UTF-8.</span><span class="sxs-lookup"><span data-stu-id="58ad8-114"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ad8-115">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="58ad8-115">See also</span></span>

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [<span data-ttu-id="58ad8-116">Практическое руководство. Преобразование строки в массив байтов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="58ad8-116">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>](how-to-convert-strings-into-an-array-of-bytes.md)
