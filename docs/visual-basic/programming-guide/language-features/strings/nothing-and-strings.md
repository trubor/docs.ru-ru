---
description: 'Дополнительные сведения о: Nothing и строках в Visual Basic'
title: Nothing и строки
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: a32dd8b38033f1845f2ada87bf5f538d45fede18
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424350"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="85713-103">Nothing и строки в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85713-103">Nothing and Strings in Visual Basic</span></span>

<span data-ttu-id="85713-104">Среда выполнения Visual Basic и платформа .NET Framework оцениваются по- `Nothing` разному, когда речь идет о строках.</span><span class="sxs-lookup"><span data-stu-id="85713-104">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="85713-105">Среда выполнения Visual Basic и платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="85713-105">Visual Basic Runtime and the .NET Framework</span></span>  

 <span data-ttu-id="85713-106">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="85713-106">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="85713-107">Среда выполнения Visual Basic обычно вычисляется `Nothing` как пустая строка ("").</span><span class="sxs-lookup"><span data-stu-id="85713-107">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="85713-108">Однако платформа .NET Framework не создает исключение, когда выполняется попытка выполнить операцию со строкой `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="85713-108">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85713-109">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="85713-109">See also</span></span>

- [<span data-ttu-id="85713-110">Знакомство со строками в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85713-110">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
