---
description: Дополнительные сведения см. в статье как создать лямбда-выражение (Visual Basic)
title: Практическое руководство. Создание лямбда-выражения
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 386d40c1e2021c9b02b2f785300c4e978b4da87d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472570"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="b189a-103">Практическое руководство. Создание лямбда-выражения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b189a-103">How to: Create a Lambda Expression (Visual Basic)</span></span>

<span data-ttu-id="b189a-104">*Лямбда-выражение* — это функция или подпрограммы, у которой нет имени.</span><span class="sxs-lookup"><span data-stu-id="b189a-104">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="b189a-105">Лямбда-выражение может использоваться везде, где допустим тип делегата.</span><span class="sxs-lookup"><span data-stu-id="b189a-105">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="b189a-106">Создание однострочной функции лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="b189a-106">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="b189a-107">В любой ситуации, где можно использовать тип делегата, введите ключевое слово `Function` , как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="b189a-107">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="b189a-108">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="b189a-108">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="b189a-109">В скобках сразу после `Function` введите параметры функции.</span><span class="sxs-lookup"><span data-stu-id="b189a-109">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="b189a-110">Обратите внимание, что имя не указывается после `Function` .</span><span class="sxs-lookup"><span data-stu-id="b189a-110">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="b189a-111">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="b189a-111">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="b189a-112">После списка параметров введите одно выражение в качестве текста функции.</span><span class="sxs-lookup"><span data-stu-id="b189a-112">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="b189a-113">Значение, которое вычисляется выражением, — это значение, возвращаемое функцией.</span><span class="sxs-lookup"><span data-stu-id="b189a-113">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="b189a-114">Не используйте `As` предложение, чтобы указать тип возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="b189a-114">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="b189a-115">Лямбда-выражение вызывается путем передачи целочисленного аргумента.</span><span class="sxs-lookup"><span data-stu-id="b189a-115">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="b189a-116">Кроме того, тот же результат достигается в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="b189a-116">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="b189a-117">Создание однострочной подпрограммы лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="b189a-117">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="b189a-118">В любой ситуации, где можно использовать тип делегата, введите ключевое слово `Sub` , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="b189a-118">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="b189a-119">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="b189a-119">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="b189a-120">В скобках сразу после `Sub` введите параметры подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="b189a-120">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="b189a-121">Обратите внимание, что имя не указывается после `Sub` .</span><span class="sxs-lookup"><span data-stu-id="b189a-121">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="b189a-122">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="b189a-122">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="b189a-123">После списка параметров введите один оператор в качестве текста подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="b189a-123">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="b189a-124">Лямбда-выражение вызывается путем передачи строкового аргумента.</span><span class="sxs-lookup"><span data-stu-id="b189a-124">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="b189a-125">Создание многострочной функции лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="b189a-125">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="b189a-126">В любой ситуации, где можно использовать тип делегата, введите ключевое слово `Function` , как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="b189a-126">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="b189a-127">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="b189a-127">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="b189a-128">В скобках сразу после `Function` введите параметры функции.</span><span class="sxs-lookup"><span data-stu-id="b189a-128">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="b189a-129">Обратите внимание, что имя не указывается после `Function` .</span><span class="sxs-lookup"><span data-stu-id="b189a-129">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="b189a-130">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="b189a-130">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="b189a-131">Нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="b189a-131">Press ENTER.</span></span> <span data-ttu-id="b189a-132">`End Function`Инструкция автоматически добавляется.</span><span class="sxs-lookup"><span data-stu-id="b189a-132">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="b189a-133">В теле функции добавьте следующий код, чтобы создать выражение и вернуть значение.</span><span class="sxs-lookup"><span data-stu-id="b189a-133">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="b189a-134">Не используйте `As` предложение, чтобы указать тип возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="b189a-134">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="b189a-135">Лямбда-выражение вызывается путем передачи целочисленного аргумента.</span><span class="sxs-lookup"><span data-stu-id="b189a-135">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="b189a-136">Создание многострочной подпрограммы лямбда-выражений</span><span class="sxs-lookup"><span data-stu-id="b189a-136">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="b189a-137">В любой ситуации, где можно использовать тип делегата, введите ключевое слово `Sub` , как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="b189a-137">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="b189a-138">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="b189a-138">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="b189a-139">В скобках сразу после `Sub` введите параметры подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="b189a-139">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="b189a-140">Обратите внимание, что имя не указывается после `Sub` .</span><span class="sxs-lookup"><span data-stu-id="b189a-140">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="b189a-141">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="b189a-141">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="b189a-142">Нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="b189a-142">Press ENTER.</span></span> <span data-ttu-id="b189a-143">`End Sub`Инструкция автоматически добавляется.</span><span class="sxs-lookup"><span data-stu-id="b189a-143">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="b189a-144">В теле функции добавьте следующий код для выполнения при вызове подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="b189a-144">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="b189a-145">Лямбда-выражение вызывается путем передачи строкового аргумента.</span><span class="sxs-lookup"><span data-stu-id="b189a-145">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="b189a-146">Пример</span><span class="sxs-lookup"><span data-stu-id="b189a-146">Example</span></span>  

 <span data-ttu-id="b189a-147">Обычно лямбда-выражения используются для определения функции, которую можно передать в качестве аргумента для параметра, тип которого имеет значение `Delegate` .</span><span class="sxs-lookup"><span data-stu-id="b189a-147">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="b189a-148">В следующем примере <xref:System.Diagnostics.Process.GetProcesses%2A> метод возвращает массив процессов, запущенных на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="b189a-148">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="b189a-149">Для <xref:System.Linq.Enumerable.Where%2A> метода из <xref:System.Linq.Enumerable> класса требуется делегат в `Boolean` качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="b189a-149">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="b189a-150">Лямбда-выражение в примере используется для этой цели.</span><span class="sxs-lookup"><span data-stu-id="b189a-150">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="b189a-151">Он возвращает `True` для каждого процесса, который имеет только один поток, и выбранные в `filteredList` .</span><span class="sxs-lookup"><span data-stu-id="b189a-151">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="b189a-152">Предыдущий пример эквивалентен следующему коду, написанному в синтаксисе Language-Integrated query (LINQ):</span><span class="sxs-lookup"><span data-stu-id="b189a-152">The previous example is equivalent to the following code, which is written in Language-Integrated Query (LINQ) syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="b189a-153">См. также</span><span class="sxs-lookup"><span data-stu-id="b189a-153">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="b189a-154">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="b189a-154">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="b189a-155">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="b189a-155">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="b189a-156">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="b189a-156">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="b189a-157">Делегаты</span><span class="sxs-lookup"><span data-stu-id="b189a-157">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="b189a-158">Практическое руководство. Передача процедур другой процедуре в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b189a-158">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="b189a-159">Оператор Delegate</span><span class="sxs-lookup"><span data-stu-id="b189a-159">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- <span data-ttu-id="b189a-160">[Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b189a-160">[Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md)</span></span>
