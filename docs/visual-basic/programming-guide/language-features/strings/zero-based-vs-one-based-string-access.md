---
description: Дополнительные сведения см. в статье как с нуля, так и с помощью одностраничного доступа к строкам в Visual Basic
title: 'Что лучше: отсчет строк с нуля или с единицы?'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: adab6954c4329ae0a547d136f26f6c3115dc5890
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463836"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="5ed2e-103">Что лучше: отсчет индексации с нуля или с единицы? (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ed2e-103">Zero-based vs. One-based String Access in Visual Basic</span></span>

<span data-ttu-id="5ed2e-104">В этом разделе сравнивается, как Visual Basic и платформа .NET Framework предоставляют доступ к символам в строке.</span><span class="sxs-lookup"><span data-stu-id="5ed2e-104">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="5ed2e-105">Платформа .NET Framework всегда предоставляет доступ к символам в строке с нуля, тогда как Visual Basic предоставляет доступ с нуля и с одной стороны, в зависимости от функции.</span><span class="sxs-lookup"><span data-stu-id="5ed2e-105">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="5ed2e-106">One-Based</span><span class="sxs-lookup"><span data-stu-id="5ed2e-106">One-Based</span></span>  

 <span data-ttu-id="5ed2e-107">Пример одноVisual Basicной функции можно получить с помощью `Mid` функции.</span><span class="sxs-lookup"><span data-stu-id="5ed2e-107">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="5ed2e-108">Он принимает аргумент, который указывает на позиции символа, с которого начнется подстрока, начиная с позиции 1.</span><span class="sxs-lookup"><span data-stu-id="5ed2e-108">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="5ed2e-109">Метод платформа .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> принимает индекс символа в строке, с которой начинается подстрока, начиная с позиции 0.</span><span class="sxs-lookup"><span data-stu-id="5ed2e-109">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="5ed2e-110">Таким способом, если имеется строка «ABCD», то отдельные символы нумеруются 1, 2, 3, 4, 5 для использования с `Mid` функцией, но 0, 1, 2, 3, 4 для использования с <xref:System.String.Substring%2A?displayProperty=nameWithType> методом.</span><span class="sxs-lookup"><span data-stu-id="5ed2e-110">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="5ed2e-111">Zero-Based</span><span class="sxs-lookup"><span data-stu-id="5ed2e-111">Zero-Based</span></span>  

 <span data-ttu-id="5ed2e-112">Пример функции Visual Basic, начинающейся с нуля, можно получить с помощью `Split` функции.</span><span class="sxs-lookup"><span data-stu-id="5ed2e-112">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="5ed2e-113">Он разделяет строку и возвращает массив, содержащий подстроки.</span><span class="sxs-lookup"><span data-stu-id="5ed2e-113">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="5ed2e-114">Метод платформа .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> также разделяет строку и возвращает массив, содержащий подстроки.</span><span class="sxs-lookup"><span data-stu-id="5ed2e-114">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="5ed2e-115">Так как `Split` функция и <xref:System.String.Split%2A> метод возвращают платформа .NET Framework массивы, они должны относиться от нуля.</span><span class="sxs-lookup"><span data-stu-id="5ed2e-115">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed2e-116">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="5ed2e-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="5ed2e-117">Знакомство со строками в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ed2e-117">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
