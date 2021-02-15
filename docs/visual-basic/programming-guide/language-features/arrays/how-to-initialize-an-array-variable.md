---
description: Дополнительные сведения см. в статье как инициализировать переменную массива в Visual Basic
title: Практическое руководство. Инициализация переменной массива
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 05cca98457a56db52ee99cfc4ac93c860da7a51d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100427613"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a><span data-ttu-id="6fd68-103">Практическое руководство. Инициализация переменной массива в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6fd68-103">How to: Initialize an Array Variable in Visual Basic</span></span>

<span data-ttu-id="6fd68-104">Инициализируйте переменную массива, включив литерал массива в `New` предложение и указав начальные значения массива.</span><span class="sxs-lookup"><span data-stu-id="6fd68-104">You initialize an array variable by including an array literal in a `New` clause and specifying the initial values of the array.</span></span> <span data-ttu-id="6fd68-105">Можно либо указать тип, либо разрешить вывод его из значений в литерале массива.</span><span class="sxs-lookup"><span data-stu-id="6fd68-105">You can either specify the type or allow it to be inferred from the values in the array literal.</span></span> <span data-ttu-id="6fd68-106">Дополнительные сведения о выводимом типе см. в разделе «Заполнение массива начальными значениями» в [массивах](index.md).</span><span class="sxs-lookup"><span data-stu-id="6fd68-106">For more information about how the type is inferred, see "Populating an Array with Initial Values" in [Arrays](index.md).</span></span>  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a><span data-ttu-id="6fd68-107">Инициализация переменной массива с помощью литерала массива</span><span class="sxs-lookup"><span data-stu-id="6fd68-107">To initialize an array variable by using an array literal</span></span>  
  
- <span data-ttu-id="6fd68-108">Либо в `New` предложении, либо при присваивании значения массива, укажите значения элементов внутри фигурных скобок ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="6fd68-108">Either in the `New` clause, or when you assign the array value, supply the element values inside braces (`{}`).</span></span> <span data-ttu-id="6fd68-109">В следующем примере показано несколько способов объявления, создания и инициализации переменной, содержащей массив с элементами типа `Char` .</span><span class="sxs-lookup"><span data-stu-id="6fd68-109">The following example shows several ways to declare, create, and initialize a variable to contain an array that has elements of type `Char`.</span></span>  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     <span data-ttu-id="6fd68-110">После выполнения каждой инструкции создаваемый массив имеет длину 3 и элементы с индексом 0 по индексу 2, содержащие начальные значения.</span><span class="sxs-lookup"><span data-stu-id="6fd68-110">After each statement executes, the array that's created has a length of 3, with elements at index 0 through index 2 containing the initial values.</span></span> <span data-ttu-id="6fd68-111">При указании и верхней границы, и значений необходимо включить значение для каждого элемента из индекса 0 через верхнюю границу.</span><span class="sxs-lookup"><span data-stu-id="6fd68-111">If you supply both the upper bound and the values, you must include a value for every element from index 0 through the upper bound.</span></span>  
  
     <span data-ttu-id="6fd68-112">Обратите внимание, что при указании значений элементов в литерале массива не нужно указывать верхнюю границу индекса.</span><span class="sxs-lookup"><span data-stu-id="6fd68-112">Notice that you do not have to specify the index upper bound if you supply element values in an array literal.</span></span> <span data-ttu-id="6fd68-113">Если верхняя граница не указана, размер массива определяется исходя из числа значений в литерале массива.</span><span class="sxs-lookup"><span data-stu-id="6fd68-113">If no upper bound is specified, the size of the array is inferred based on the number of values in the array literal.</span></span>  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a><span data-ttu-id="6fd68-114">Инициализация переменной многомерного массива с помощью литералов массива</span><span class="sxs-lookup"><span data-stu-id="6fd68-114">To initialize a multidimensional array variable by using array literals</span></span>  
  
- <span data-ttu-id="6fd68-115">Вложенные значения внутри фигурных скобок ( `{}` ) внутри фигурных скобок.</span><span class="sxs-lookup"><span data-stu-id="6fd68-115">Nest values inside braces (`{}`) within braces.</span></span> <span data-ttu-id="6fd68-116">Убедитесь, что все вложенные литералы массива выводятся как массивы одинакового типа и длины.</span><span class="sxs-lookup"><span data-stu-id="6fd68-116">Ensure that the nested array literals all infer as arrays of the same type and length.</span></span> <span data-ttu-id="6fd68-117">В следующем примере кода показаны несколько примеров инициализации многомерных массивов.</span><span class="sxs-lookup"><span data-stu-id="6fd68-117">The following code example shows several examples of multidimensional array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- <span data-ttu-id="6fd68-118">Можно явно указать границы массива или оставить их, чтобы компилятор мог вычислять границы массива на основе значений в литерале массива.</span><span class="sxs-lookup"><span data-stu-id="6fd68-118">You can explicitly specify the array bounds, or leave them out and have the compiler infer the array bounds based on the values in the array literal.</span></span> <span data-ttu-id="6fd68-119">При указании обеих верхних границ и значений необходимо включить значение для каждого элемента из индекса 0 через верхнюю границу в каждом измерении.</span><span class="sxs-lookup"><span data-stu-id="6fd68-119">If you supply both the upper bounds and the values, you must include a value for every element from index 0 through the upper bound in every dimension.</span></span> <span data-ttu-id="6fd68-120">В следующем примере показано несколько способов объявления, создания и инициализации переменной, содержащей двумерный массив с элементами типа `Short`</span><span class="sxs-lookup"><span data-stu-id="6fd68-120">The following example shows several ways to declare, create, and initialize a variable to contain a two-dimensional array that has elements of type `Short`</span></span>  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     <span data-ttu-id="6fd68-121">После выполнения каждой инструкции созданный массив содержит шесть инициализированных элементов, имеющих индексы `(0,0)` ,,, `(0,1)` , `(0,2)` `(1,0)` `(1,1)` и `(1,2)` .</span><span class="sxs-lookup"><span data-stu-id="6fd68-121">After each statement executes, the created array contains six initialized elements that have indexes `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, and `(1,2)`.</span></span> <span data-ttu-id="6fd68-122">Каждое расположение массива содержит значение `10` .</span><span class="sxs-lookup"><span data-stu-id="6fd68-122">Each array location contains the value `10`.</span></span>  
  
- <span data-ttu-id="6fd68-123">В следующем примере выполняется итерация по многомерному массиву.</span><span class="sxs-lookup"><span data-stu-id="6fd68-123">The following example iterates through a multidimensional array.</span></span> <span data-ttu-id="6fd68-124">В консольном приложении Windows, написанном на Visual Basic, вставьте код в `Sub Main()` метод.</span><span class="sxs-lookup"><span data-stu-id="6fd68-124">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span> <span data-ttu-id="6fd68-125">Последние комментарии показывают выходные данные.</span><span class="sxs-lookup"><span data-stu-id="6fd68-125">The last comments show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a><span data-ttu-id="6fd68-126">Инициализация переменной массива массивов с помощью литералов массива</span><span class="sxs-lookup"><span data-stu-id="6fd68-126">To initialize a jagged array variable by using array literals</span></span>  
  
- <span data-ttu-id="6fd68-127">Вложенные значения объектов в фигурные скобки ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="6fd68-127">Nest object values inside braces (`{}`).</span></span> <span data-ttu-id="6fd68-128">Хотя можно также вкладывать литералы массива, указывающие массивы разной длины, в случае массива массивов убедитесь, что литералы вложенных массивов заключены в круглые скобки ( `()` ).</span><span class="sxs-lookup"><span data-stu-id="6fd68-128">Although you can also nest array literals that specify arrays of different lengths, in the case of a jagged array, make sure that the nested array literals are enclosed in parentheses (`()`).</span></span> <span data-ttu-id="6fd68-129">Круглые скобки принудительно выводят вычисление литералов вложенных массивов, а результирующие массивы используются в качестве начальных значений массива массивов.</span><span class="sxs-lookup"><span data-stu-id="6fd68-129">The parentheses force the evaluation of the nested array literals, and the resulting arrays are used as the initial values of the jagged array.</span></span> <span data-ttu-id="6fd68-130">В следующем примере кода показаны два примера инициализации массива массивов.</span><span class="sxs-lookup"><span data-stu-id="6fd68-130">The following code example shows two examples of jagged array initialization.</span></span>  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- <span data-ttu-id="6fd68-131">В следующем примере выполняется перебор массива массивов.</span><span class="sxs-lookup"><span data-stu-id="6fd68-131">The following example iterates through a jagged array.</span></span> <span data-ttu-id="6fd68-132">В консольном приложении Windows, написанном на Visual Basic, вставьте код в `Sub Main()` метод.</span><span class="sxs-lookup"><span data-stu-id="6fd68-132">In a Windows console application that is written in Visual Basic, paste the code inside the `Sub Main()` method.</span></span>  <span data-ttu-id="6fd68-133">Последние комментарии в коде показывают выходные данные.</span><span class="sxs-lookup"><span data-stu-id="6fd68-133">The last comments in the code show the output.</span></span>  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="6fd68-134">См. также</span><span class="sxs-lookup"><span data-stu-id="6fd68-134">See also</span></span>

- [<span data-ttu-id="6fd68-135">Массивы</span><span class="sxs-lookup"><span data-stu-id="6fd68-135">Arrays</span></span>](index.md)
- [<span data-ttu-id="6fd68-136">Устранение неполадок, связанных с массивами</span><span class="sxs-lookup"><span data-stu-id="6fd68-136">Troubleshooting Arrays</span></span>](troubleshooting-arrays.md)
