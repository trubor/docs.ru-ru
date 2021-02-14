---
description: 'Дополнительные сведения о процедурах: Function (Visual Basic)'
title: процедуры функций
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: 4997059fc33fb5d438519356b2c9fdd9e6a27cce
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436153"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="b4fff-103">Процедуры Function (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4fff-103">Function procedures (Visual Basic)</span></span>

<span data-ttu-id="b4fff-104">`Function`Процедура — это последовательность инструкций Visual Basic, заключенных в `Function` операторы и `End Function` .</span><span class="sxs-lookup"><span data-stu-id="b4fff-104">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="b4fff-105">`Function`Процедура выполняет задачу, а затем возвращает управление вызывающему коду.</span><span class="sxs-lookup"><span data-stu-id="b4fff-105">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="b4fff-106">Когда он возвращает управление, он также возвращает значение в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="b4fff-106">When it returns control, it also returns a value to the calling code.</span></span>

<span data-ttu-id="b4fff-107">При каждом вызове процедуры ее инструкции выполняются, начиная с первого исполняемого оператора после `Function` инструкции и заканчивая первой `End Function` `Exit Function` `Return` инструкцией, или.</span><span class="sxs-lookup"><span data-stu-id="b4fff-107">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>

<span data-ttu-id="b4fff-108">Процедуру можно определить `Function` в модуле, классе или структуре.</span><span class="sxs-lookup"><span data-stu-id="b4fff-108">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="b4fff-109">`Public`По умолчанию это означает, что вы можете вызывать его из любого места в приложении, которое имеет доступ к модулю, классу или структуре, в которой он определен.</span><span class="sxs-lookup"><span data-stu-id="b4fff-109">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>

<span data-ttu-id="b4fff-110">`Function`Процедура может принимать аргументы, такие как константы, переменные или выражения, которые передаются в него вызывающим кодом.</span><span class="sxs-lookup"><span data-stu-id="b4fff-110">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="b4fff-111">Синтаксис объявления</span><span class="sxs-lookup"><span data-stu-id="b4fff-111">Declaration syntax</span></span>

<span data-ttu-id="b4fff-112">Синтаксис для объявления `Function` процедуры выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b4fff-112">The syntax for declaring a `Function` procedure is as follows:</span></span>

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

<span data-ttu-id="b4fff-113">*Модификаторы* могут указывать уровень доступа и сведения о перегрузке, переопределении, совместном использовании и затенении.</span><span class="sxs-lookup"><span data-stu-id="b4fff-113">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="b4fff-114">Дополнительные сведения см. в разделе [оператор Function](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b4fff-114">For more information, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

<span data-ttu-id="b4fff-115">Каждый параметр объявляется так же, как и для [процедур подраздела](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b4fff-115">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="b4fff-116">Тип данных</span><span class="sxs-lookup"><span data-stu-id="b4fff-116">Data type</span></span>

<span data-ttu-id="b4fff-117">Каждая `Function` процедура имеет тип данных, точно так же, как и каждая переменная.</span><span class="sxs-lookup"><span data-stu-id="b4fff-117">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="b4fff-118">Этот тип данных указывается `As` предложением в `Function` операторе и определяет тип данных значения, возвращаемого функцией в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="b4fff-118">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="b4fff-119">Это показано в приведенных ниже примерах объявлений.</span><span class="sxs-lookup"><span data-stu-id="b4fff-119">The following sample declarations illustrate this.</span></span>

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

<span data-ttu-id="b4fff-120">Дополнительные сведения см. в разделе "части" в [операторе Function](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b4fff-120">For more information, see "Parts" in [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

### <a name="returning-values"></a><span data-ttu-id="b4fff-121">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="b4fff-121">Returning values</span></span>

<span data-ttu-id="b4fff-122">Значение, которое `Function` процедура отправляет обратно вызывающему коду, называется его возвращаемым значением.</span><span class="sxs-lookup"><span data-stu-id="b4fff-122">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="b4fff-123">Процедура возвращает это значение одним из двух способов:</span><span class="sxs-lookup"><span data-stu-id="b4fff-123">The procedure returns this value in one of two ways:</span></span>

- <span data-ttu-id="b4fff-124">Он использует `Return` инструкцию для указания возвращаемого значения и немедленно возвращает управление вызывающей программе.</span><span class="sxs-lookup"><span data-stu-id="b4fff-124">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="b4fff-125">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="b4fff-125">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- <span data-ttu-id="b4fff-126">Он присваивает значение имени своей функции в одной или нескольких инструкциях процедуры.</span><span class="sxs-lookup"><span data-stu-id="b4fff-126">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="b4fff-127">Управление не возвращается вызывающей программе до тех пор, `Exit Function` пока `End Function` не будет выполнен оператор или.</span><span class="sxs-lookup"><span data-stu-id="b4fff-127">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="b4fff-128">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="b4fff-128">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

<span data-ttu-id="b4fff-129">Преимуществом присвоения возвращаемого значения имени функции является то, что Управление не возвращается из процедуры до тех пор, пока не встретится `Exit Function` `End Function` оператор или.</span><span class="sxs-lookup"><span data-stu-id="b4fff-129">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="b4fff-130">Это позволяет назначить предварительное значение и позже при необходимости изменить его.</span><span class="sxs-lookup"><span data-stu-id="b4fff-130">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>

<span data-ttu-id="b4fff-131">Дополнительные сведения о возвращаемых значениях см. в разделе [оператор Function](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b4fff-131">For more information about returning values, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="b4fff-132">Дополнительные сведения о возврате массивов см. в разделе [массивы](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="b4fff-132">For information about returning arrays, see [Arrays](../arrays/index.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="b4fff-133">Синтаксис вызова</span><span class="sxs-lookup"><span data-stu-id="b4fff-133">Calling syntax</span></span>

<span data-ttu-id="b4fff-134">Процедура вызывается `Function` путем включения ее имени и аргументов в правой части оператора присваивания или в выражении.</span><span class="sxs-lookup"><span data-stu-id="b4fff-134">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="b4fff-135">Необходимо указать значения для всех аргументов, которые не являются необязательными, и необходимо заключить список аргументов в круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="b4fff-135">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="b4fff-136">Если аргументы не указаны, можно дополнительно опустить круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="b4fff-136">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="b4fff-137">Синтаксис для вызова процедуры выглядит следующим образом `Function` .</span><span class="sxs-lookup"><span data-stu-id="b4fff-137">The syntax for a call to a `Function` procedure is as follows.</span></span>

<span data-ttu-id="b4fff-138">*lvalue* `=` *FunctionName* `[(` *ArgumentList*    `)]`</span><span class="sxs-lookup"><span data-stu-id="b4fff-138">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>

<span data-ttu-id="b4fff-139">`If ((`*FunctionName* `[(` *ArgumentList* `)] / 3) <=` *выражение*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="b4fff-139">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>

<span data-ttu-id="b4fff-140">При вызове `Function` процедуры не нужно использовать ее возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="b4fff-140">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="b4fff-141">В противном случае выполняются все действия функции, но возвращаемое значение игнорируется.</span><span class="sxs-lookup"><span data-stu-id="b4fff-141">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="b4fff-142"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> часто вызывается подобным образом.</span><span class="sxs-lookup"><span data-stu-id="b4fff-142"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="b4fff-143">Иллюстрация объявления и вызова</span><span class="sxs-lookup"><span data-stu-id="b4fff-143">Illustration of declaration and call</span></span>

<span data-ttu-id="b4fff-144">Следующая `Function` процедура вычисляет самую длинную сторону (гипотенузу) правого треугольника, учитывая значения двух других сторон.</span><span class="sxs-lookup"><span data-stu-id="b4fff-144">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

<span data-ttu-id="b4fff-145">В следующем примере показан типичный вызов метода `hypotenuse` .</span><span class="sxs-lookup"><span data-stu-id="b4fff-145">The following example shows a typical call to `hypotenuse`.</span></span>

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a><span data-ttu-id="b4fff-146">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="b4fff-146">See also</span></span>

- [<span data-ttu-id="b4fff-147">Процедуры</span><span class="sxs-lookup"><span data-stu-id="b4fff-147">Procedures</span></span>](./index.md)
- [<span data-ttu-id="b4fff-148">Подпрограммы</span><span class="sxs-lookup"><span data-stu-id="b4fff-148">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="b4fff-149">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="b4fff-149">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="b4fff-150">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="b4fff-150">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="b4fff-151">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="b4fff-151">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b4fff-152">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="b4fff-152">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="b4fff-153">Практическое руководство. Создание процедуры, возвращающей значение</span><span class="sxs-lookup"><span data-stu-id="b4fff-153">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="b4fff-154">Практическое руководство. Возврат значения из процедуры</span><span class="sxs-lookup"><span data-stu-id="b4fff-154">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="b4fff-155">Практическое руководство. Вызов процедуры, возвращающей значение</span><span class="sxs-lookup"><span data-stu-id="b4fff-155">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
