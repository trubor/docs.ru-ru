---
description: 'Дополнительные сведения: выражение функции (Visual Basic)'
title: Выражение function
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: bef5db7f167b615c2a0c20539521c186683da985
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666021"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="b9687-103">Выражение Function (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9687-103">Function Expression (Visual Basic)</span></span>

<span data-ttu-id="b9687-104">Объявляет параметры и код, определяющие лямбда-выражение функции.</span><span class="sxs-lookup"><span data-stu-id="b9687-104">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9687-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b9687-105">Syntax</span></span>  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="b9687-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="b9687-106">Parts</span></span>  
  
|<span data-ttu-id="b9687-107">Термин</span><span class="sxs-lookup"><span data-stu-id="b9687-107">Term</span></span>|<span data-ttu-id="b9687-108">Определение</span><span class="sxs-lookup"><span data-stu-id="b9687-108">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="b9687-109">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="b9687-109">Optional.</span></span> <span data-ttu-id="b9687-110">Список имен локальных переменных, представляющих параметры этой процедуры.</span><span class="sxs-lookup"><span data-stu-id="b9687-110">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="b9687-111">Круглые скобки должны присутствовать, даже если список пуст.</span><span class="sxs-lookup"><span data-stu-id="b9687-111">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="b9687-112">См. [список параметров](../statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="b9687-112">See [Parameter List](../statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="b9687-113">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="b9687-113">Required.</span></span> <span data-ttu-id="b9687-114">Одно выражение.</span><span class="sxs-lookup"><span data-stu-id="b9687-114">A single expression.</span></span> <span data-ttu-id="b9687-115">Тип выражения является типом возвращаемого значения функции.</span><span class="sxs-lookup"><span data-stu-id="b9687-115">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="b9687-116">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="b9687-116">Required.</span></span> <span data-ttu-id="b9687-117">Список инструкций, которые возвращают значение с помощью `Return` инструкции.</span><span class="sxs-lookup"><span data-stu-id="b9687-117">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="b9687-118">(См. раздел [оператор return](../statements/return-statement.md).) Тип возвращаемого значения — это возвращаемый тип функции.</span><span class="sxs-lookup"><span data-stu-id="b9687-118">(See [Return Statement](../statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9687-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="b9687-119">Remarks</span></span>  

 <span data-ttu-id="b9687-120">*Лямбда-выражение* — это функция без имени, которая вычисляет и возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="b9687-120">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="b9687-121">Лямбда-выражение можно использовать в любом месте, где можно использовать тип делегата, кроме аргумента `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="b9687-121">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="b9687-122">Дополнительные сведения о делегатах и использовании лямбда-выражений с делегатами см. в разделе [оператор Delegate](../statements/delegate-statement.md) и [Преобразование неявного делегата](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="b9687-122">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="b9687-123">Синтаксис лямбда-выражений</span><span class="sxs-lookup"><span data-stu-id="b9687-123">Lambda Expression Syntax</span></span>  

 <span data-ttu-id="b9687-124">Синтаксис лямбда-выражения напоминает стандартную функцию.</span><span class="sxs-lookup"><span data-stu-id="b9687-124">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="b9687-125">Различия заключаются в следующем.</span><span class="sxs-lookup"><span data-stu-id="b9687-125">The differences are as follows:</span></span>  
  
- <span data-ttu-id="b9687-126">Лямбда-выражение не имеет имени.</span><span class="sxs-lookup"><span data-stu-id="b9687-126">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="b9687-127">Лямбда-выражения не могут иметь модификаторы, такие как `Overloads` или `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="b9687-127">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="b9687-128">Лямбда-выражения не используют `As` предложение для обозначения возвращаемого типа функции.</span><span class="sxs-lookup"><span data-stu-id="b9687-128">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="b9687-129">Вместо этого тип выводится из значения, которое принимает текст однострочного лямбда-выражения, или возвращаемое значение многострочного лямбда-выражения.</span><span class="sxs-lookup"><span data-stu-id="b9687-129">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="b9687-130">Например, если текст однострочного лямбда-выражения имеет значение `Where cust.City = "London"` , его тип возвращаемого значения — `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b9687-130">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="b9687-131">Тело однострочного лямбда-выражения должно быть выражением, а не оператором.</span><span class="sxs-lookup"><span data-stu-id="b9687-131">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="b9687-132">Тело может состоять из вызова процедуры функции, но не вызова процедуры подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="b9687-132">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
- <span data-ttu-id="b9687-133">Либо все параметры должны иметь указанные типы данных, либо все должны быть выведены.</span><span class="sxs-lookup"><span data-stu-id="b9687-133">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="b9687-134">Параметры Optional и ParamArray не разрешены.</span><span class="sxs-lookup"><span data-stu-id="b9687-134">Optional and Paramarray parameters are not permitted.</span></span>  
  
- <span data-ttu-id="b9687-135">Универсальные параметры не допускаются.</span><span class="sxs-lookup"><span data-stu-id="b9687-135">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9687-136">Пример</span><span class="sxs-lookup"><span data-stu-id="b9687-136">Example</span></span>  

 <span data-ttu-id="b9687-137">В следующих примерах показано два способа создания простых лямбда-выражений.</span><span class="sxs-lookup"><span data-stu-id="b9687-137">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="b9687-138">Первый использует `Dim` для предоставления имени функции.</span><span class="sxs-lookup"><span data-stu-id="b9687-138">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="b9687-139">Для вызова функции вы отправляете значение для параметра.</span><span class="sxs-lookup"><span data-stu-id="b9687-139">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="b9687-140">Пример</span><span class="sxs-lookup"><span data-stu-id="b9687-140">Example</span></span>  

 <span data-ttu-id="b9687-141">Кроме того, можно одновременно объявить и запустить функцию.</span><span class="sxs-lookup"><span data-stu-id="b9687-141">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="b9687-142">Пример</span><span class="sxs-lookup"><span data-stu-id="b9687-142">Example</span></span>  

 <span data-ttu-id="b9687-143">Ниже приведен пример лямбда-выражения, которое увеличивает свой аргумент и возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="b9687-143">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="b9687-144">В примере показан синтаксис однострочного и многострочного лямбда-выражения для функции.</span><span class="sxs-lookup"><span data-stu-id="b9687-144">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="b9687-145">Дополнительные примеры см. в разделе [лямбда-выражения](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b9687-145">For more examples, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="b9687-146">Пример</span><span class="sxs-lookup"><span data-stu-id="b9687-146">Example</span></span>  

 <span data-ttu-id="b9687-147">Лямбда-выражения лежат в основе многих операторов запросов в Language-Integrated query (LINQ) и могут использоваться явным образом в запросах, основанных на методах.</span><span class="sxs-lookup"><span data-stu-id="b9687-147">Lambda expressions underlie many of the query operators in Language-Integrated Query (LINQ), and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="b9687-148">В следующем примере показан типичный запрос LINQ, а затем перевод запроса в формат метода.</span><span class="sxs-lookup"><span data-stu-id="b9687-148">The following example shows a typical LINQ query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="b9687-149">Дополнительные сведения о методах запросов см. в разделе [запросы](../queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="b9687-149">For more information about query methods, see [Queries](../queries/index.md).</span></span> <span data-ttu-id="b9687-150">Дополнительные сведения о стандартных операторах запросов см. в разделе [Общие сведения о стандартных операторах запросов](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b9687-150">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9687-151">См. также</span><span class="sxs-lookup"><span data-stu-id="b9687-151">See also</span></span>

- [<span data-ttu-id="b9687-152">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="b9687-152">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="b9687-153">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="b9687-153">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="b9687-154">Операторы и выражения</span><span class="sxs-lookup"><span data-stu-id="b9687-154">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="b9687-155">Операторы</span><span class="sxs-lookup"><span data-stu-id="b9687-155">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="b9687-156">Сравнения значений</span><span class="sxs-lookup"><span data-stu-id="b9687-156">Value Comparisons</span></span>](../../programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="b9687-157">Логические выражения</span><span class="sxs-lookup"><span data-stu-id="b9687-157">Boolean Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="b9687-158">Оператор If</span><span class="sxs-lookup"><span data-stu-id="b9687-158">If Operator</span></span>](if-operator.md)
- [<span data-ttu-id="b9687-159">Неявное преобразование делегата</span><span class="sxs-lookup"><span data-stu-id="b9687-159">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
