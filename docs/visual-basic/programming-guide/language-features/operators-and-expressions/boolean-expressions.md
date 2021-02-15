---
description: 'Дополнительные сведения: логические выражения (Visual Basic)'
title: Логические выражения
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
ms.openlocfilehash: 3b752e2146755e1272b261f32931e3022e8ef354
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100465318"
---
# <a name="boolean-expressions-visual-basic"></a><span data-ttu-id="bfe49-103">Логические выражения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfe49-103">Boolean Expressions (Visual Basic)</span></span>

<span data-ttu-id="bfe49-104">*Логическое выражение* — это выражение, результатом вычисления которого является значение [логического типа данных](../../../language-reference/data-types/boolean-data-type.md): `True` или `False` .</span><span class="sxs-lookup"><span data-stu-id="bfe49-104">A *Boolean expression* is an expression that evaluates to a value of the [Boolean Data Type](../../../language-reference/data-types/boolean-data-type.md): `True` or `False`.</span></span> <span data-ttu-id="bfe49-105">`Boolean` выражения могут принимать несколько форм.</span><span class="sxs-lookup"><span data-stu-id="bfe49-105">`Boolean` expressions can take several forms.</span></span> <span data-ttu-id="bfe49-106">Простейшим является прямое сравнение значения `Boolean` переменной с `Boolean` литералом, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="bfe49-106">The simplest is the direct comparison of the value of a `Boolean` variable to a `Boolean` literal, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a><span data-ttu-id="bfe49-107">Два значения оператора =</span><span class="sxs-lookup"><span data-stu-id="bfe49-107">Two Meanings of the = Operator</span></span>  

 <span data-ttu-id="bfe49-108">Обратите внимание, что оператор присваивания `newCustomer = True` выглядит так же, как выражение в предыдущем примере, но выполняет другую функцию и используется по-разному.</span><span class="sxs-lookup"><span data-stu-id="bfe49-108">Notice that the assignment statement `newCustomer = True` looks the same as the expression in the preceding example, but it performs a different function and is used differently.</span></span> <span data-ttu-id="bfe49-109">В предыдущем примере выражение `newCustomer = True` представляет логическое значение, а `=` знак интерпретируется как оператор сравнения.</span><span class="sxs-lookup"><span data-stu-id="bfe49-109">In the preceding example, the expression `newCustomer = True` represents a Boolean value, and the `=` sign is interpreted as a comparison operator.</span></span> <span data-ttu-id="bfe49-110">В изолированном операторе `=` знак интерпретируется как оператор присваивания и присваивает значение справа переменной слева.</span><span class="sxs-lookup"><span data-stu-id="bfe49-110">In a stand-alone statement, the `=` sign is interpreted as an assignment operator and assigns the value on the right to the variable on the left.</span></span> <span data-ttu-id="bfe49-111">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="bfe49-111">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 <span data-ttu-id="bfe49-112">Дополнительные сведения см. в разделе [сравнения значений](value-comparisons.md) и [инструкции](../../../language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="bfe49-112">For further information, see [Value Comparisons](value-comparisons.md) and [Statements](../../../language-reference/statements/index.md).</span></span>  
  
## <a name="comparison-operators"></a><span data-ttu-id="bfe49-113">Операторы сравнения</span><span class="sxs-lookup"><span data-stu-id="bfe49-113">Comparison Operators</span></span>  

 <span data-ttu-id="bfe49-114">Операторы сравнения, такие как `=` ,, `<` ,, `>` `<>` `<=` , и `>=` создают логические выражения путем сравнения выражения с левой стороны оператора с выражением в правой части оператора и вычисления результата в виде `True` или `False` .</span><span class="sxs-lookup"><span data-stu-id="bfe49-114">Comparison operators such as `=`, `<`, `>`, `<>`, `<=`, and `>=` produce Boolean expressions by comparing the expression on the left side of the operator to the expression on the right side of the operator and evaluating the result as `True` or `False`.</span></span> <span data-ttu-id="bfe49-115">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="bfe49-115">The following example illustrates this.</span></span>  
  
 `42 < 81`  
  
 <span data-ttu-id="bfe49-116">Поскольку 42 меньше 81, логическое выражение в предыдущем примере вычисляется как `True` .</span><span class="sxs-lookup"><span data-stu-id="bfe49-116">Because 42 is less than 81, the Boolean expression in the preceding example evaluates to `True`.</span></span> <span data-ttu-id="bfe49-117">Дополнительные сведения об этом типе выражения см. в разделе [сравнения значений](value-comparisons.md).</span><span class="sxs-lookup"><span data-stu-id="bfe49-117">For more information on this kind of expression, see [Value Comparisons](value-comparisons.md).</span></span>  
  
### <a name="comparison-operators-combined-with-logical-operators"></a><span data-ttu-id="bfe49-118">Операторы сравнения в сочетании с логическими операторами</span><span class="sxs-lookup"><span data-stu-id="bfe49-118">Comparison Operators Combined with Logical Operators</span></span>  

 <span data-ttu-id="bfe49-119">Выражения сравнения можно комбинировать с помощью логических операторов для создания более сложных логических выражений.</span><span class="sxs-lookup"><span data-stu-id="bfe49-119">Comparison expressions can be combined using logical operators to produce more complex Boolean expressions.</span></span> <span data-ttu-id="bfe49-120">В следующем примере показано использование операторов сравнения в сочетании с логическим оператором.</span><span class="sxs-lookup"><span data-stu-id="bfe49-120">The following example demonstrates the use of comparison operators in conjunction with a logical operator.</span></span>  
  
 `x > y And x < 1000`  
  
 <span data-ttu-id="bfe49-121">В предыдущем примере значение общего выражения зависит от значений выражений на каждой стороне `And` оператора.</span><span class="sxs-lookup"><span data-stu-id="bfe49-121">In the preceding example, the value of the overall expression depends on the values of the expressions on each side of the `And` operator.</span></span> <span data-ttu-id="bfe49-122">Если оба выражения имеют значение `True` , то общее выражение принимает значение `True` .</span><span class="sxs-lookup"><span data-stu-id="bfe49-122">If both expressions are `True`, then the overall expression evaluates to `True`.</span></span> <span data-ttu-id="bfe49-123">Если любое из выражений имеет значение `False` , результатом вычисления всего выражения будет значение `False` .</span><span class="sxs-lookup"><span data-stu-id="bfe49-123">If either expression is `False`, then the entire expression evaluates to `False`.</span></span>  
  
## <a name="short-circuiting-operators"></a><span data-ttu-id="bfe49-124">Операторы Short-Circuiting</span><span class="sxs-lookup"><span data-stu-id="bfe49-124">Short-Circuiting Operators</span></span>  

 <span data-ttu-id="bfe49-125">Логические операторы `AndAlso` и `OrElse` демонстрируют поведение, называемое *сокращенным вычислением*.</span><span class="sxs-lookup"><span data-stu-id="bfe49-125">The logical operators `AndAlso` and `OrElse` exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="bfe49-126">Оператор сокращенного вычисления сначала вычисляет левый операнд.</span><span class="sxs-lookup"><span data-stu-id="bfe49-126">A short-circuiting operator evaluates the left operand first.</span></span> <span data-ttu-id="bfe49-127">Если левый операнд определяет значение всего выражения, выполнение программы продолжается без вычисления правого выражения.</span><span class="sxs-lookup"><span data-stu-id="bfe49-127">If the left operand determines the value of the entire expression, then program execution proceeds without evaluating the right expression.</span></span> <span data-ttu-id="bfe49-128">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="bfe49-128">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 <span data-ttu-id="bfe49-129">В предыдущем примере оператор вычисляет левое выражение `45 < 12` .</span><span class="sxs-lookup"><span data-stu-id="bfe49-129">In the preceding example, the operator evaluates the left expression, `45 < 12`.</span></span> <span data-ttu-id="bfe49-130">Так как левое выражение принимает значение `False` , все логическое выражение должно иметь значение `False` .</span><span class="sxs-lookup"><span data-stu-id="bfe49-130">Because the left expression evaluates to `False`, the entire logical expression must evaluate to `False`.</span></span> <span data-ttu-id="bfe49-131">Таким результатом, выполнение программы пропускает выполнение кода в `If` блоке без вычисления правого выражения `testFunction(3)` .</span><span class="sxs-lookup"><span data-stu-id="bfe49-131">Program execution thus skips execution of the code within the `If` block without evaluating the right expression, `testFunction(3)`.</span></span> <span data-ttu-id="bfe49-132">Этот пример не вызывается `testFunction()` , поскольку левое выражение фалсифиес все выражение.</span><span class="sxs-lookup"><span data-stu-id="bfe49-132">This example does not call `testFunction()` because the left expression falsifies the entire expression.</span></span>  
  
 <span data-ttu-id="bfe49-133">Аналогично, если левое выражение в логическом выражении с помощью метода `OrElse` Evaluate имеет значение `True` , выполнение переходит к следующей строке кода без вычисления правого выражения, поскольку левое выражение уже проверило все выражение.</span><span class="sxs-lookup"><span data-stu-id="bfe49-133">Similarly, if the left expression in a logical expression using `OrElse` evaluates to `True`, execution proceeds to the next line of code without evaluating the right expression, because the left expression has already validated the entire expression.</span></span>  
  
### <a name="comparison-with-non-short-circuiting-operators"></a><span data-ttu-id="bfe49-134">Сравнение с операторами, не являющимися сокращенными</span><span class="sxs-lookup"><span data-stu-id="bfe49-134">Comparison with Non-Short-Circuiting Operators</span></span>  

 <span data-ttu-id="bfe49-135">Напротив, обе стороны логического оператора оцениваются при использовании логических операторов `And` и `Or` .</span><span class="sxs-lookup"><span data-stu-id="bfe49-135">By contrast, both sides of the logical operator are evaluated when the logical operators `And` and `Or` are used.</span></span> <span data-ttu-id="bfe49-136">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="bfe49-136">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 <span data-ttu-id="bfe49-137">В предыдущем примере вызывается, несмотря на то, `testFunction()` что левое выражение имеет значение `False` .</span><span class="sxs-lookup"><span data-stu-id="bfe49-137">The preceding example calls `testFunction()` even though the left expression evaluates to `False`.</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="bfe49-138">Выражения в скобках</span><span class="sxs-lookup"><span data-stu-id="bfe49-138">Parenthetical Expressions</span></span>  

 <span data-ttu-id="bfe49-139">Можно использовать круглые скобки для управления порядком вычисления логических выражений.</span><span class="sxs-lookup"><span data-stu-id="bfe49-139">You can use parentheses to control the order of evaluation of Boolean expressions.</span></span> <span data-ttu-id="bfe49-140">Выражения, заключенные в круглые скобки, сначала оцениваются.</span><span class="sxs-lookup"><span data-stu-id="bfe49-140">Expressions enclosed by parentheses evaluate first.</span></span> <span data-ttu-id="bfe49-141">Для нескольких уровней вложенности приоритет предоставляется самым глубоким вложенным выражениям.</span><span class="sxs-lookup"><span data-stu-id="bfe49-141">For multiple levels of nesting, precedence is granted to the most deeply nested expressions.</span></span> <span data-ttu-id="bfe49-142">В круглых скобках вычисление продолжается в соответствии с правилами приоритета операторов.</span><span class="sxs-lookup"><span data-stu-id="bfe49-142">Within parentheses, evaluation proceeds according to the rules of operator precedence.</span></span> <span data-ttu-id="bfe49-143">Дополнительные сведения см. [в разделе приоритет операторов в Visual Basic](../../../language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="bfe49-143">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfe49-144">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="bfe49-144">See also</span></span>

- [<span data-ttu-id="bfe49-145">Логические и побитовые операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bfe49-145">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
- [<span data-ttu-id="bfe49-146">Сравнения значений</span><span class="sxs-lookup"><span data-stu-id="bfe49-146">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="bfe49-147">Операторы</span><span class="sxs-lookup"><span data-stu-id="bfe49-147">Statements</span></span>](../statements.md)
- [<span data-ttu-id="bfe49-148">Операторы сравнения</span><span class="sxs-lookup"><span data-stu-id="bfe49-148">Comparison Operators</span></span>](../../../language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="bfe49-149">Эффективное сочетание операторов</span><span class="sxs-lookup"><span data-stu-id="bfe49-149">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
- [<span data-ttu-id="bfe49-150">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bfe49-150">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="bfe49-151">Логический тип данных</span><span class="sxs-lookup"><span data-stu-id="bfe49-151">Boolean Data Type</span></span>](../../../language-reference/data-types/boolean-data-type.md)
