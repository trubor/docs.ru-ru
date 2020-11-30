---
title: Сокращение и удаление символов из строк в .NET
description: Научитесь удалять пробелы в начале или конце строки, а также удалять любое количество пробелов или символов из указанной позиции в строке в .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
ms.openlocfilehash: 9b0fd87bfec747f8dd09d3972167374a1a2daffa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734195"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="4c28c-103">Сокращение и удаление символов из строк в .NET</span><span class="sxs-lookup"><span data-stu-id="4c28c-103">Trimming and Removing Characters from Strings in .NET</span></span>

<span data-ttu-id="4c28c-104">При разборе предложения на отдельные слова может оказаться, что в начале или в конце некоторых слов стоят пробелы.</span><span class="sxs-lookup"><span data-stu-id="4c28c-104">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="4c28c-105">В этом случае можно воспользоваться методами сокращения в классе **System.String**, чтобы удалить любое количество пробелов или других символов из указанной позиции в строке.</span><span class="sxs-lookup"><span data-stu-id="4c28c-105">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="4c28c-106">В таблице ниже описаны доступны методы сокращения.</span><span class="sxs-lookup"><span data-stu-id="4c28c-106">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="4c28c-107">Имя метода</span><span class="sxs-lookup"><span data-stu-id="4c28c-107">Method name</span></span>|<span data-ttu-id="4c28c-108">Использовать</span><span class="sxs-lookup"><span data-stu-id="4c28c-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="4c28c-109">Удаление пробелов или знаков, указанных в массиве знаков, из начала и конца строки.</span><span class="sxs-lookup"><span data-stu-id="4c28c-109">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="4c28c-110">Удаление символов, указанных в массиве символов, в конце строки.</span><span class="sxs-lookup"><span data-stu-id="4c28c-110">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="4c28c-111">Удаление символов, указанных в массиве символов, в начале строки.</span><span class="sxs-lookup"><span data-stu-id="4c28c-111">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="4c28c-112">Удаление указанного количества символов в указанной позиции индекса в строке.</span><span class="sxs-lookup"><span data-stu-id="4c28c-112">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="4c28c-113">Trim</span><span class="sxs-lookup"><span data-stu-id="4c28c-113">Trim</span></span>

 <span data-ttu-id="4c28c-114">Простой способ удалить пробелы с обоих концов строки — метод <xref:System.String.Trim%2A?displayProperty=nameWithType>, использование которого показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="4c28c-114">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="4c28c-115">Кроме того, можно удалить символы, указанные в массиве знаков, из начала и конца строки.</span><span class="sxs-lookup"><span data-stu-id="4c28c-115">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="4c28c-116">В следующем примере удаляются символы пробелов, точки и звездочки.</span><span class="sxs-lookup"><span data-stu-id="4c28c-116">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="4c28c-117">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="4c28c-117">TrimEnd</span></span>

 <span data-ttu-id="4c28c-118">Метод **String.TrimEnd** удаляет символы в конце строки, создавая новый строковый объект.</span><span class="sxs-lookup"><span data-stu-id="4c28c-118">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="4c28c-119">Для указания символов, которые следует удалять, в этот метод передается массив символов.</span><span class="sxs-lookup"><span data-stu-id="4c28c-119">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="4c28c-120">Порядок элементов в массиве символов не влияет на выполнение операции сокращения.</span><span class="sxs-lookup"><span data-stu-id="4c28c-120">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="4c28c-121">В случае обнаружения символа, который отсутствует в массиве, операция останавливается.</span><span class="sxs-lookup"><span data-stu-id="4c28c-121">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="4c28c-122">Ниже приведен пример удаления последних букв строки с помощью метода **TrimEnd**.</span><span class="sxs-lookup"><span data-stu-id="4c28c-122">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="4c28c-123">В этом примере положение символов `'r'` и `'W'` изменено для иллюстрации того, что порядок символов в массиве не имеет значения.</span><span class="sxs-lookup"><span data-stu-id="4c28c-123">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="4c28c-124">Обратите внимание, что этот код удаляет последнее слово `MyString` и часть первого.</span><span class="sxs-lookup"><span data-stu-id="4c28c-124">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="4c28c-125">Этот код выводит на консоль значение `He`.</span><span class="sxs-lookup"><span data-stu-id="4c28c-125">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="4c28c-126">Ниже приведен пример удаления последнего слова строки с помощью метода **TrimEnd**.</span><span class="sxs-lookup"><span data-stu-id="4c28c-126">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="4c28c-127">В этом коде после слова `Hello` следует запятая, а поскольку запятая не указана в массиве символов для сокращения, то выполнение операции прекращается на запятой.</span><span class="sxs-lookup"><span data-stu-id="4c28c-127">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="4c28c-128">Этот код выводит на консоль значение `Hello,`.</span><span class="sxs-lookup"><span data-stu-id="4c28c-128">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="4c28c-129">TrimStart</span><span class="sxs-lookup"><span data-stu-id="4c28c-129">TrimStart</span></span>

 <span data-ttu-id="4c28c-130">Метод **String.TrimStart** аналогичен методу **String.TrimEnd** за исключением того, что он создает новую строку путем удаления знаков в начале существующего строкового объекта.</span><span class="sxs-lookup"><span data-stu-id="4c28c-130">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="4c28c-131">Для указания символов, которые следует удалять, в метод **TrimStart** передается массив символов.</span><span class="sxs-lookup"><span data-stu-id="4c28c-131">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="4c28c-132">Как и в случае с методом **TrimEnd**, порядок элементов в массиве символов не влияет на выполнение операции сокращения.</span><span class="sxs-lookup"><span data-stu-id="4c28c-132">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="4c28c-133">В случае обнаружения символа, который отсутствует в массиве, операция останавливается.</span><span class="sxs-lookup"><span data-stu-id="4c28c-133">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="4c28c-134">В следующем примере удаляется первое слово в строке.</span><span class="sxs-lookup"><span data-stu-id="4c28c-134">The following example removes the first word of a string.</span></span> <span data-ttu-id="4c28c-135">В этом примере положение символов `'l'` и `'H'` изменено для иллюстрации того, что порядок символов в массиве не имеет значения.</span><span class="sxs-lookup"><span data-stu-id="4c28c-135">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="4c28c-136">Этот код выводит на консоль значение `World!`.</span><span class="sxs-lookup"><span data-stu-id="4c28c-136">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="4c28c-137">Удалить</span><span class="sxs-lookup"><span data-stu-id="4c28c-137">Remove</span></span>

 <span data-ttu-id="4c28c-138">Метод <xref:System.String.Remove%2A?displayProperty=nameWithType> удаляет указанное количество знаков, начиная с указанного места в существующей строке.</span><span class="sxs-lookup"><span data-stu-id="4c28c-138">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="4c28c-139">Этот метод подразумевает, что отсчет индекса начинается с нуля.</span><span class="sxs-lookup"><span data-stu-id="4c28c-139">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="4c28c-140">В следующем примере из строки удаляется десять символов, начиная с пятой позиции отсчитываемого от нуля индекса строки.</span><span class="sxs-lookup"><span data-stu-id="4c28c-140">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a><span data-ttu-id="4c28c-141">Замените</span><span class="sxs-lookup"><span data-stu-id="4c28c-141">Replace</span></span>

 <span data-ttu-id="4c28c-142">Чтобы удалить из строки указанный символ или подстроку, можно вызвать метод <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> и указать пустую строку (<xref:System.String.Empty?displayProperty=nameWithType>) в качестве замены.</span><span class="sxs-lookup"><span data-stu-id="4c28c-142">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="4c28c-143">В следующем примере удаляются все запятые из строки.</span><span class="sxs-lookup"><span data-stu-id="4c28c-143">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="4c28c-144">См. также</span><span class="sxs-lookup"><span data-stu-id="4c28c-144">See also</span></span>

- [<span data-ttu-id="4c28c-145">Базовые операции со строками в .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4c28c-145">Basic String Operations</span></span>](basic-string-operations.md)
