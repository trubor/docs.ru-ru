---
description: 'Дополнительные сведения: логические и побитовые операторы в Visual Basic'
title: Логические и побитовые операторы
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: 55d9567813a9114573e1e3f70fe181cb8621b350
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472726"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a><span data-ttu-id="c91ac-103">Логические и побитовые операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c91ac-103">Logical and Bitwise Operators in Visual Basic</span></span>

<span data-ttu-id="c91ac-104">Логические операторы сравнивают `Boolean` выражения и возвращают `Boolean` результат.</span><span class="sxs-lookup"><span data-stu-id="c91ac-104">Logical operators compare `Boolean` expressions and return a `Boolean` result.</span></span> <span data-ttu-id="c91ac-105">`And`Операторы, `Or` , `AndAlso` , `OrElse` и `Xor` являются *двоичными* , поскольку они принимают два операнда, а `Not` оператор является *унарным* , так как он принимает один операнд.</span><span class="sxs-lookup"><span data-stu-id="c91ac-105">The `And`, `Or`, `AndAlso`, `OrElse`, and `Xor` operators are *binary* because they take two operands, while the `Not` operator is *unary* because it takes a single operand.</span></span> <span data-ttu-id="c91ac-106">Некоторые из этих операторов также могут выполнять побитовые логические операции над целочисленными значениями.</span><span class="sxs-lookup"><span data-stu-id="c91ac-106">Some of these operators can also perform bitwise logical operations on integral values.</span></span>  
  
## <a name="unary-logical-operator"></a><span data-ttu-id="c91ac-107">Унарный логический оператор</span><span class="sxs-lookup"><span data-stu-id="c91ac-107">Unary Logical Operator</span></span>  

 <span data-ttu-id="c91ac-108">[Оператор not](../../../language-reference/operators/not-operator.md) выполняет логическое *отрицание* в `Boolean` выражении.</span><span class="sxs-lookup"><span data-stu-id="c91ac-108">The [Not Operator](../../../language-reference/operators/not-operator.md) performs logical *negation* on a `Boolean` expression.</span></span> <span data-ttu-id="c91ac-109">Он возвращает логическое противоположное значение операнда.</span><span class="sxs-lookup"><span data-stu-id="c91ac-109">It yields the logical opposite of its operand.</span></span> <span data-ttu-id="c91ac-110">Если результатом вычисления выражения является `True` , возвращается значение `Not` `False` ; Если результат вычисления выражения равен `False` , возвращается значение `Not` `True` .</span><span class="sxs-lookup"><span data-stu-id="c91ac-110">If the expression evaluates to `True`, then `Not` returns `False`; if the expression evaluates to `False`, then `Not` returns `True`.</span></span> <span data-ttu-id="c91ac-111">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c91ac-111">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a><span data-ttu-id="c91ac-112">Бинарные логические операторы</span><span class="sxs-lookup"><span data-stu-id="c91ac-112">Binary Logical Operators</span></span>  

 <span data-ttu-id="c91ac-113">[Оператор and](../../../language-reference/operators/and-operator.md) выполняет логическое *умножение* двух `Boolean` выражений.</span><span class="sxs-lookup"><span data-stu-id="c91ac-113">The [And Operator](../../../language-reference/operators/and-operator.md) performs logical *conjunction* on two `Boolean` expressions.</span></span> <span data-ttu-id="c91ac-114">Если оба выражения имеют значение `True` , `And` возвращается значение `True` .</span><span class="sxs-lookup"><span data-stu-id="c91ac-114">If both expressions evaluate to `True`, then `And` returns `True`.</span></span> <span data-ttu-id="c91ac-115">Если хотя бы одно из выражений имеет значение `False` , `And` возвращается значение `False` .</span><span class="sxs-lookup"><span data-stu-id="c91ac-115">If at least one of the expressions evaluates to `False`, then `And` returns `False`.</span></span>  
  
 <span data-ttu-id="c91ac-116">[Оператор OR](../../../language-reference/operators/or-operator.md) выполняет логическое *сложение* или *Включение* двух `Boolean` выражений.</span><span class="sxs-lookup"><span data-stu-id="c91ac-116">The [Or Operator](../../../language-reference/operators/or-operator.md) performs logical *disjunction* or *inclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="c91ac-117">Если любое из выражений принимает значение `True` , или оба значения имеют значение `True` , `Or` возвращается значение `True` .</span><span class="sxs-lookup"><span data-stu-id="c91ac-117">If either expression evaluates to `True`, or both evaluate to `True`, then `Or` returns `True`.</span></span> <span data-ttu-id="c91ac-118">Если ни одно из выражений не имеет значение `True` , `Or` возвращает `False` .</span><span class="sxs-lookup"><span data-stu-id="c91ac-118">If neither expression evaluates to `True`, `Or` returns `False`.</span></span>  
  
 <span data-ttu-id="c91ac-119">[Оператор XOR](../../../language-reference/operators/xor-operator.md) выполняет логическое *исключение* для двух `Boolean` выражений.</span><span class="sxs-lookup"><span data-stu-id="c91ac-119">The [Xor Operator](../../../language-reference/operators/xor-operator.md) performs logical *exclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="c91ac-120">Если только одно выражение имеет значение `True` , но не оба, `Xor` возвращает `True` .</span><span class="sxs-lookup"><span data-stu-id="c91ac-120">If exactly one expression evaluates to `True`, but not both, `Xor` returns `True`.</span></span> <span data-ttu-id="c91ac-121">Если оба выражения имеют значение `True` или `False` , `Xor` возвращает `False` .</span><span class="sxs-lookup"><span data-stu-id="c91ac-121">If both expressions evaluate to `True` or both evaluate to `False`, `Xor` returns `False`.</span></span>  
  
 <span data-ttu-id="c91ac-122">В следующем примере показаны `And` операторы, `Or` и `Xor` .</span><span class="sxs-lookup"><span data-stu-id="c91ac-122">The following example illustrates the `And`, `Or`, and `Xor` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a><span data-ttu-id="c91ac-123">Short-Circuiting логических операций</span><span class="sxs-lookup"><span data-stu-id="c91ac-123">Short-Circuiting Logical Operations</span></span>  

 <span data-ttu-id="c91ac-124">[Оператор AndAlso](../../../language-reference/operators/andalso-operator.md) очень похож на `And` оператор, в котором он также выполняет логическое умножение двух `Boolean` выражений.</span><span class="sxs-lookup"><span data-stu-id="c91ac-124">The [AndAlso Operator](../../../language-reference/operators/andalso-operator.md) is very similar to the `And` operator, in that it also performs logical conjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="c91ac-125">Основное различие между ними состоит в том, что приводит к `AndAlso` *сокращению* поведения.</span><span class="sxs-lookup"><span data-stu-id="c91ac-125">The key difference between the two is that `AndAlso` exhibits *short-circuiting* behavior.</span></span> <span data-ttu-id="c91ac-126">Если первое выражение в `AndAlso` выражении имеет значение `False` , второе выражение не вычисляется, так как не может изменить окончательный результат и `AndAlso` возвращает `False` .</span><span class="sxs-lookup"><span data-stu-id="c91ac-126">If the first expression in an `AndAlso` expression evaluates to `False`, then the second expression is not evaluated because it cannot alter the final result, and `AndAlso` returns `False`.</span></span>  
  
 <span data-ttu-id="c91ac-127">Аналогично [оператор OrElse](../../../language-reference/operators/orelse-operator.md) выполняет сокращенное вычисление логического сложения двух `Boolean` выражений.</span><span class="sxs-lookup"><span data-stu-id="c91ac-127">Similarly, the [OrElse Operator](../../../language-reference/operators/orelse-operator.md) performs short-circuiting logical disjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="c91ac-128">Если первое выражение в `OrElse` выражении имеет значение `True` , второе выражение не вычисляется, так как не может изменить окончательный результат и `OrElse` возвращает `True` .</span><span class="sxs-lookup"><span data-stu-id="c91ac-128">If the first expression in an `OrElse` expression evaluates to `True`, then the second expression is not evaluated because it cannot alter the final result, and `OrElse` returns `True`.</span></span>  
  
### <a name="short-circuiting-trade-offs"></a><span data-ttu-id="c91ac-129">Short-Circuiting Trade-Offs</span><span class="sxs-lookup"><span data-stu-id="c91ac-129">Short-Circuiting Trade-Offs</span></span>  

 <span data-ttu-id="c91ac-130">Сокращенное вычисление может повысить производительность, не вычисляя выражение, которое не может изменить результат логической операции.</span><span class="sxs-lookup"><span data-stu-id="c91ac-130">Short-circuiting can improve performance by not evaluating an expression that cannot alter the result of the logical operation.</span></span> <span data-ttu-id="c91ac-131">Однако если это выражение выполняет дополнительные действия, сокращенное вычисление пропускает эти действия.</span><span class="sxs-lookup"><span data-stu-id="c91ac-131">However, if that expression performs additional actions, short-circuiting skips those actions.</span></span> <span data-ttu-id="c91ac-132">Например, если выражение содержит вызов `Function` процедуры, эта процедура не вызывается, если выражение сокращено, а любой дополнительный код, содержащийся в, `Function` не выполняется.</span><span class="sxs-lookup"><span data-stu-id="c91ac-132">For example, if the expression includes a call to a `Function` procedure, that procedure is not called if the expression is short-circuited, and any additional code contained in the `Function` does not run.</span></span> <span data-ttu-id="c91ac-133">Таким образом, функция может выполняться только иногда и может быть некорректно проверена.</span><span class="sxs-lookup"><span data-stu-id="c91ac-133">Therefore, the function might run only occasionally, and might not be tested correctly.</span></span> <span data-ttu-id="c91ac-134">Или логика программы может зависеть от кода в `Function` .</span><span class="sxs-lookup"><span data-stu-id="c91ac-134">Or the program logic might depend on the code in the `Function`.</span></span>  
  
 <span data-ttu-id="c91ac-135">В следующем примере показана разница между `And` , `Or` и их сокращенными аналогами.</span><span class="sxs-lookup"><span data-stu-id="c91ac-135">The following example illustrates the difference between `And`, `Or`, and their short-circuiting counterparts.</span></span>  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 <span data-ttu-id="c91ac-136">Обратите внимание, что в предыдущем примере некоторый важный код внутри не `checkIfValid()` выполняется при сокращенном вызове.</span><span class="sxs-lookup"><span data-stu-id="c91ac-136">In the preceding example, note that some important code inside `checkIfValid()` does not run when the call is short-circuited.</span></span> <span data-ttu-id="c91ac-137">Первый `If` оператор вызывает `checkIfValid()` `12 > 45` , хотя возвращает `False` , так как `And` не выполняет сокращенное вычисление.</span><span class="sxs-lookup"><span data-stu-id="c91ac-137">The first `If` statement calls `checkIfValid()` even though `12 > 45` returns `False`, because `And` does not short-circuit.</span></span> <span data-ttu-id="c91ac-138">Вторая `If` инструкция не вызывает метод `checkIfValid()` , поскольку при `12 > 45` возврате `False` происходит `AndAlso` сокращенное значение второго выражения.</span><span class="sxs-lookup"><span data-stu-id="c91ac-138">The second `If` statement does not call `checkIfValid()`, because when `12 > 45` returns `False`, `AndAlso` short-circuits the second expression.</span></span> <span data-ttu-id="c91ac-139">Третья `If` инструкция вызывает `checkIfValid()` , даже если `12 < 45` возвращает `True` , так как `Or` не выполняет сокращенное вычисление.</span><span class="sxs-lookup"><span data-stu-id="c91ac-139">The third `If` statement calls `checkIfValid()` even though `12 < 45` returns `True`, because `Or` does not short-circuit.</span></span> <span data-ttu-id="c91ac-140">Четвертый `If` оператор не вызывает метод `checkIfValid()` , поскольку при `12 < 45` возврате `True` происходит `OrElse` сокращенное значение второго выражения.</span><span class="sxs-lookup"><span data-stu-id="c91ac-140">The fourth `If` statement does not call `checkIfValid()`, because when `12 < 45` returns `True`, `OrElse` short-circuits the second expression.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="c91ac-141">Битовые операции</span><span class="sxs-lookup"><span data-stu-id="c91ac-141">Bitwise Operations</span></span>  

 <span data-ttu-id="c91ac-142">Побитовые операции оценивают два целочисленных значения в форме binary (основание 2).</span><span class="sxs-lookup"><span data-stu-id="c91ac-142">Bitwise operations evaluate two integral values in binary (base 2) form.</span></span> <span data-ttu-id="c91ac-143">Они сравнивают биты в соответствующих позициях и затем присваивают значения на основе сравнения.</span><span class="sxs-lookup"><span data-stu-id="c91ac-143">They compare the bits at corresponding positions and then assign values based on the comparison.</span></span> <span data-ttu-id="c91ac-144">В следующем примере показан `And` оператор.</span><span class="sxs-lookup"><span data-stu-id="c91ac-144">The following example illustrates the `And` operator.</span></span>  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 <span data-ttu-id="c91ac-145">В предыдущем примере задается значение `x` 1.</span><span class="sxs-lookup"><span data-stu-id="c91ac-145">The preceding example sets the value of `x` to 1.</span></span> <span data-ttu-id="c91ac-146">Это происходит по следующим причинам.</span><span class="sxs-lookup"><span data-stu-id="c91ac-146">This happens for the following reasons:</span></span>  
  
- <span data-ttu-id="c91ac-147">Значения рассматриваются как двоичные:</span><span class="sxs-lookup"><span data-stu-id="c91ac-147">The values are treated as binary:</span></span>  
  
     <span data-ttu-id="c91ac-148">3 в двоичном формате = 011</span><span class="sxs-lookup"><span data-stu-id="c91ac-148">3 in binary form = 011</span></span>  
  
     <span data-ttu-id="c91ac-149">5 в двоичном формате = 101</span><span class="sxs-lookup"><span data-stu-id="c91ac-149">5 in binary form = 101</span></span>  
  
- <span data-ttu-id="c91ac-150">`And`Оператор сравнивает двоичные представления, по одной двоичной позиции (бит) за раз.</span><span class="sxs-lookup"><span data-stu-id="c91ac-150">The `And` operator compares the binary representations, one binary position (bit) at a time.</span></span> <span data-ttu-id="c91ac-151">Если оба бита в заданной позиции равны 1, то в результате в эту точку помещается 1.</span><span class="sxs-lookup"><span data-stu-id="c91ac-151">If both bits at a given position are 1, then a 1 is placed in that position in the result.</span></span> <span data-ttu-id="c91ac-152">Если любой из битов равен 0, то в результат помещается 0.</span><span class="sxs-lookup"><span data-stu-id="c91ac-152">If either bit is 0, then a 0 is placed in that position in the result.</span></span> <span data-ttu-id="c91ac-153">В предыдущем примере это работает следующим образом:</span><span class="sxs-lookup"><span data-stu-id="c91ac-153">In the preceding example this works out as follows:</span></span>  
  
     <span data-ttu-id="c91ac-154">011 (3 в двоичной форме)</span><span class="sxs-lookup"><span data-stu-id="c91ac-154">011 (3 in binary form)</span></span>  
  
     <span data-ttu-id="c91ac-155">101 (5 в двоичной форме)</span><span class="sxs-lookup"><span data-stu-id="c91ac-155">101 (5 in binary form)</span></span>  
  
     <span data-ttu-id="c91ac-156">001 (результат в двоичной форме)</span><span class="sxs-lookup"><span data-stu-id="c91ac-156">001 (The result, in binary form)</span></span>  
  
- <span data-ttu-id="c91ac-157">Результат считается десятичным.</span><span class="sxs-lookup"><span data-stu-id="c91ac-157">The result is treated as decimal.</span></span> <span data-ttu-id="c91ac-158">Значение 001 является двоичным представлением 1, то есть `x` = 1.</span><span class="sxs-lookup"><span data-stu-id="c91ac-158">The value 001 is the binary representation of 1, so `x` = 1.</span></span>  
  
 <span data-ttu-id="c91ac-159">Побитовая `Or` Операция аналогична, за исключением того, что 1 назначается биту результата, если один или оба сравниваемых бита равны 1.</span><span class="sxs-lookup"><span data-stu-id="c91ac-159">The bitwise `Or` operation is similar, except that a 1 is assigned to the result bit if either or both of the compared bits is 1.</span></span> <span data-ttu-id="c91ac-160">`Xor` присваивает значение 1 результирующему биту, если ровно один из сравниваемых битов (не оба) равен 1.</span><span class="sxs-lookup"><span data-stu-id="c91ac-160">`Xor` assigns a 1 to the result bit if exactly one of the compared bits (not both) is 1.</span></span> <span data-ttu-id="c91ac-161">`Not` принимает один операнд и инвертирует все биты, включая бит знака, и присваивает это значение результату.</span><span class="sxs-lookup"><span data-stu-id="c91ac-161">`Not` takes a single operand and inverts all the bits, including the sign bit, and assigns that value to the result.</span></span> <span data-ttu-id="c91ac-162">Это означает, что для положительных чисел со знаком `Not` всегда возвращает отрицательное значение, а для отрицательных чисел `Not` всегда возвращает положительное или нулевое значение.</span><span class="sxs-lookup"><span data-stu-id="c91ac-162">This means that for signed positive numbers, `Not` always returns a negative value, and for negative numbers, `Not` always returns a positive or zero value.</span></span>  
  
 <span data-ttu-id="c91ac-163">`AndAlso`Операторы и `OrElse` не поддерживают побитовые операции.</span><span class="sxs-lookup"><span data-stu-id="c91ac-163">The `AndAlso` and `OrElse` operators do not support bitwise operations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c91ac-164">Битовые операции могут выполняться только с целыми типами.</span><span class="sxs-lookup"><span data-stu-id="c91ac-164">Bitwise operations can be performed on integral types only.</span></span> <span data-ttu-id="c91ac-165">Перед выполнением побитовой операции значения с плавающей запятой необходимо преобразовать в целочисленные типы.</span><span class="sxs-lookup"><span data-stu-id="c91ac-165">Floating-point values must be converted to integral types before bitwise operation can proceed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c91ac-166">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c91ac-166">See also</span></span>

- [<span data-ttu-id="c91ac-167">Логические (побитовые) операторы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c91ac-167">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="c91ac-168">Логические выражения</span><span class="sxs-lookup"><span data-stu-id="c91ac-168">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="c91ac-169">Арифметические операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c91ac-169">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="c91ac-170">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c91ac-170">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="c91ac-171">Операторы объединения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c91ac-171">Concatenation Operators in Visual Basic</span></span>](concatenation-operators.md)
- [<span data-ttu-id="c91ac-172">Эффективное сочетание операторов</span><span class="sxs-lookup"><span data-stu-id="c91ac-172">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
