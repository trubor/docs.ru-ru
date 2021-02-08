---
description: 'Дополнительные сведения о подвыражении: часть выражения (Visual Basic)'
title: Выражение sub
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: e47aa8f9707701b5fd9d90fb3fabb31e9c052b53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795291"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="e2172-103">Часть выражения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2172-103">Sub Expression (Visual Basic)</span></span>

<span data-ttu-id="e2172-104">Объявляет параметры и код, определяющие лямбда-выражение подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="e2172-104">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2172-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e2172-105">Syntax</span></span>  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="e2172-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="e2172-106">Parts</span></span>  
  
|<span data-ttu-id="e2172-107">Термин</span><span class="sxs-lookup"><span data-stu-id="e2172-107">Term</span></span>|<span data-ttu-id="e2172-108">Определение</span><span class="sxs-lookup"><span data-stu-id="e2172-108">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="e2172-109">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="e2172-109">Optional.</span></span> <span data-ttu-id="e2172-110">Список имен локальных переменных, представляющих параметры процедуры.</span><span class="sxs-lookup"><span data-stu-id="e2172-110">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="e2172-111">Круглые скобки должны присутствовать, даже если список пуст.</span><span class="sxs-lookup"><span data-stu-id="e2172-111">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="e2172-112">Дополнительные сведения см. в разделе [Parameter List](../statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="e2172-112">For more information, see [Parameter List](../statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="e2172-113">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="e2172-113">Required.</span></span> <span data-ttu-id="e2172-114">Один оператор.</span><span class="sxs-lookup"><span data-stu-id="e2172-114">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="e2172-115">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="e2172-115">Required.</span></span> <span data-ttu-id="e2172-116">Список инструкций.</span><span class="sxs-lookup"><span data-stu-id="e2172-116">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2172-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="e2172-117">Remarks</span></span>  

 <span data-ttu-id="e2172-118">*Лямбда-выражение* — это подпрограммы без имени и выполняющая одну или несколько инструкций.</span><span class="sxs-lookup"><span data-stu-id="e2172-118">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="e2172-119">Лямбда-выражение можно использовать в любом месте, где можно использовать тип делегата, за исключением того, что в качестве аргумента для `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="e2172-119">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="e2172-120">Дополнительные сведения о делегатах и использовании лямбда-выражений с делегатами см. в разделе [оператор Delegate](../statements/delegate-statement.md) и [Преобразование неявного делегата](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="e2172-120">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="e2172-121">Синтаксис лямбда-выражений</span><span class="sxs-lookup"><span data-stu-id="e2172-121">Lambda Expression Syntax</span></span>  

 <span data-ttu-id="e2172-122">Синтаксис лямбда-выражения напоминает стандартную подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="e2172-122">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="e2172-123">Различия заключаются в следующем.</span><span class="sxs-lookup"><span data-stu-id="e2172-123">The differences are as follows:</span></span>  
  
- <span data-ttu-id="e2172-124">Лямбда-выражение не имеет имени.</span><span class="sxs-lookup"><span data-stu-id="e2172-124">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="e2172-125">Лямбда-выражение не может иметь модификатор, например `Overloads` или `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="e2172-125">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="e2172-126">Тело однострочного лямбда-выражения должно быть оператором, а не выражением.</span><span class="sxs-lookup"><span data-stu-id="e2172-126">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="e2172-127">Тело может состоять из вызова подпроцедуры, но не вызова процедуры функции.</span><span class="sxs-lookup"><span data-stu-id="e2172-127">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
- <span data-ttu-id="e2172-128">В лямбда-выражении либо все параметры должны иметь указанные типы данных, либо все параметры должны быть выведены.</span><span class="sxs-lookup"><span data-stu-id="e2172-128">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
- <span data-ttu-id="e2172-129">Необязательные `ParamArray` Параметры и не допускаются в лямбда-выражениях.</span><span class="sxs-lookup"><span data-stu-id="e2172-129">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
- <span data-ttu-id="e2172-130">Универсальные параметры не допускаются в лямбда-выражениях.</span><span class="sxs-lookup"><span data-stu-id="e2172-130">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2172-131">Пример</span><span class="sxs-lookup"><span data-stu-id="e2172-131">Example</span></span>  

 <span data-ttu-id="e2172-132">Ниже приведен пример лямбда-выражения, записывающего значение в консоль.</span><span class="sxs-lookup"><span data-stu-id="e2172-132">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="e2172-133">В примере показан синтаксис однострочного и многострочного лямбда-выражения для подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="e2172-133">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="e2172-134">Дополнительные примеры см. в разделе [лямбда-выражения](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e2172-134">For more examples, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="e2172-135">См. также</span><span class="sxs-lookup"><span data-stu-id="e2172-135">See also</span></span>

- [<span data-ttu-id="e2172-136">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="e2172-136">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="e2172-137">Лямбда-выражения</span><span class="sxs-lookup"><span data-stu-id="e2172-137">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="e2172-138">Операторы и выражения</span><span class="sxs-lookup"><span data-stu-id="e2172-138">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="e2172-139">Операторы</span><span class="sxs-lookup"><span data-stu-id="e2172-139">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="e2172-140">Неявное преобразование делегата</span><span class="sxs-lookup"><span data-stu-id="e2172-140">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
