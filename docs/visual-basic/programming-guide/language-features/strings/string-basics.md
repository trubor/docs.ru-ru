---
description: Дополнительные сведения о строковых принципах см. в Visual Basic
title: Основы работы со строками
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 25d76ee177e5b3eaaa8aa6b2b1b1787dc29095a1
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424363"
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="215d5-103">Основы работы со строками в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="215d5-103">String Basics in Visual Basic</span></span>

<span data-ttu-id="215d5-104">Тип данных `String` представляет последовательность символов (каждый из которых, в свою очередь, представляет экземпляр типа данных `Char`).</span><span class="sxs-lookup"><span data-stu-id="215d5-104">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="215d5-105">В этом разделе рассматриваются основные понятия строк в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="215d5-105">This topic introduces the basic concepts of strings in Visual Basic.</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="215d5-106">Строковые переменные</span><span class="sxs-lookup"><span data-stu-id="215d5-106">String Variables</span></span>  

 <span data-ttu-id="215d5-107">Экземпляру строки можно назначить литеральное значение, которое представляет ряд символов.</span><span class="sxs-lookup"><span data-stu-id="215d5-107">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="215d5-108">Пример:</span><span class="sxs-lookup"><span data-stu-id="215d5-108">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 <span data-ttu-id="215d5-109">Переменная `String` также может принимать любое выражение, результатом которого является строка.</span><span class="sxs-lookup"><span data-stu-id="215d5-109">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="215d5-110">Ниже приведены примеры.</span><span class="sxs-lookup"><span data-stu-id="215d5-110">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 <span data-ttu-id="215d5-111">Любой литерал, который присваивается переменной `String`, должен быть заключен в кавычки ("").</span><span class="sxs-lookup"><span data-stu-id="215d5-111">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="215d5-112">Это означает, что кавычки в пределах строки не могут быть представлены кавычкой.</span><span class="sxs-lookup"><span data-stu-id="215d5-112">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="215d5-113">Например, следующий код вызовет ошибку компиляции:</span><span class="sxs-lookup"><span data-stu-id="215d5-113">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 <span data-ttu-id="215d5-114">Этот код вызывает ошибку, так как компилятор завершает строку после второй пары кавычек, а остаток строки интерпретируется как код.</span><span class="sxs-lookup"><span data-stu-id="215d5-114">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="215d5-115">Чтобы решить эту проблему, Visual Basic интерпретирует две кавычки в строковом литерале как одну кавычку в строке.</span><span class="sxs-lookup"><span data-stu-id="215d5-115">To solve this problem, Visual Basic interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="215d5-116">В следующем примере показан правильный способ указания кавычек в строке:</span><span class="sxs-lookup"><span data-stu-id="215d5-116">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 <span data-ttu-id="215d5-117">В предыдущем примере два символа кавычек перед словом `Look` становятся одним символом кавычек в строке.</span><span class="sxs-lookup"><span data-stu-id="215d5-117">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="215d5-118">Три символа кавычек в конце строки представляют один символ кавычек в строке и конечный символ строки.</span><span class="sxs-lookup"><span data-stu-id="215d5-118">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="215d5-119">Строковые литералы могут содержать несколько строк:</span><span class="sxs-lookup"><span data-stu-id="215d5-119">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="215d5-120">Результирующая строка содержит последовательности новых строк, используемых в строковом литерале (vbcr, vbcrlf и т. д.).</span><span class="sxs-lookup"><span data-stu-id="215d5-120">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="215d5-121">Вам больше не требуется использовать старое решение:</span><span class="sxs-lookup"><span data-stu-id="215d5-121">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="215d5-122">Символы в строках</span><span class="sxs-lookup"><span data-stu-id="215d5-122">Characters in Strings</span></span>  

 <span data-ttu-id="215d5-123">Строку можно представить как последовательность значений `Char`. При этом тип `String` имеет встроенные функции, которые позволяют работать со строками, как с массивами.</span><span class="sxs-lookup"><span data-stu-id="215d5-123">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="215d5-124">Как и в платформа .NET Framework, это массивы, начинающиеся с нуля.</span><span class="sxs-lookup"><span data-stu-id="215d5-124">Like all array in .NET Framework, these are zero-based arrays.</span></span> <span data-ttu-id="215d5-125">К определенному символу в строке можно обратиться с помощью свойства `Chars`, которое предоставляет механизм доступа к символу по позиции, в которой он отображается в строке.</span><span class="sxs-lookup"><span data-stu-id="215d5-125">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="215d5-126">Пример:</span><span class="sxs-lookup"><span data-stu-id="215d5-126">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 <span data-ttu-id="215d5-127">В приведенном выше примере свойство `Chars` строки возвращает четвертый символ в строке, `D`, и присваивает его `myChar`.</span><span class="sxs-lookup"><span data-stu-id="215d5-127">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="215d5-128">Вы также можете получить длину определенной строки с помощью свойства `Length`.</span><span class="sxs-lookup"><span data-stu-id="215d5-128">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="215d5-129">Если вам требуется выполнить несколько манипуляций со строкой, можно преобразовать ее в массив экземпляров `Char` с помощью функции `ToCharArray` строки.</span><span class="sxs-lookup"><span data-stu-id="215d5-129">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="215d5-130">Пример:</span><span class="sxs-lookup"><span data-stu-id="215d5-130">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 <span data-ttu-id="215d5-131">Переменная `myArray` теперь содержит массив значений `Char`, каждое из которых представляет символ из `myString`.</span><span class="sxs-lookup"><span data-stu-id="215d5-131">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="215d5-132">Неизменность строк</span><span class="sxs-lookup"><span data-stu-id="215d5-132">The Immutability of Strings</span></span>  

 <span data-ttu-id="215d5-133">Строка является *неизменяемой*. Это означает, что ее значение нельзя изменить после ее создания.</span><span class="sxs-lookup"><span data-stu-id="215d5-133">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="215d5-134">Однако это не мешает назначить строковой переменной более одного значения.</span><span class="sxs-lookup"><span data-stu-id="215d5-134">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="215d5-135">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="215d5-135">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 <span data-ttu-id="215d5-136">Здесь строковая переменная создается, получает значение, которое затем изменяется.</span><span class="sxs-lookup"><span data-stu-id="215d5-136">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="215d5-137">В частности, в первой строке создается экземпляр типа `String`, которому присваивается значение `This string is immutable`.</span><span class="sxs-lookup"><span data-stu-id="215d5-137">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="215d5-138">Во второй строке примера создается новый экземпляр, которому присваивается значение `Or is it?`. При этом строковая переменная удаляет ссылку на первый экземпляр и сохраняет ссылку на новый экземпляр.</span><span class="sxs-lookup"><span data-stu-id="215d5-138">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="215d5-139">В отличие от других встроенных типов данных `String` — это ссылочный тип.</span><span class="sxs-lookup"><span data-stu-id="215d5-139">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="215d5-140">Если переменная ссылочного типа передается в качестве аргумента функции или подпрограмме, вместо фактического значения строки передается ссылка на адрес в памяти, где хранятся данные.</span><span class="sxs-lookup"><span data-stu-id="215d5-140">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="215d5-141">Поэтому в предыдущем примере имя переменной остается таким же, но оно указывает на другой экземпляр класса `String`, который содержит новое значение.</span><span class="sxs-lookup"><span data-stu-id="215d5-141">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215d5-142">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="215d5-142">See also</span></span>

- [<span data-ttu-id="215d5-143">Знакомство со строками в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="215d5-143">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="215d5-144">Тип данных String</span><span class="sxs-lookup"><span data-stu-id="215d5-144">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="215d5-145">Тип данных Char</span><span class="sxs-lookup"><span data-stu-id="215d5-145">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="215d5-146">Базовые операции со строками в .NET Framework</span><span class="sxs-lookup"><span data-stu-id="215d5-146">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
