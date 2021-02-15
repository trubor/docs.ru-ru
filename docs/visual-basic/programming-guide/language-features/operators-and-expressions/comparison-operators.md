---
description: 'Дополнительные сведения: операторы сравнения в Visual Basic'
title: Операторы сравнения
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
ms.openlocfilehash: f16b30ca3a0cd5aa4bd5c0b2673a51205714a00c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476414"
---
# <a name="comparison-operators-in-visual-basic"></a><span data-ttu-id="6b97c-103">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b97c-103">Comparison Operators in Visual Basic</span></span>

<span data-ttu-id="6b97c-104">Операторы сравнения сравнивают два выражения и возвращают `Boolean` значение, представляющее связь их значений.</span><span class="sxs-lookup"><span data-stu-id="6b97c-104">Comparison operators compare two expressions and return a `Boolean` value that represents the relationship of their values.</span></span> <span data-ttu-id="6b97c-105">Существуют операторы для сравнения числовых значений, операторы для сравнения строк и операторы для сравнения объектов.</span><span class="sxs-lookup"><span data-stu-id="6b97c-105">There are operators for comparing numeric values, operators for comparing strings, and operators for comparing objects.</span></span> <span data-ttu-id="6b97c-106">Здесь обсуждаются все три типа операторов.</span><span class="sxs-lookup"><span data-stu-id="6b97c-106">All three types of operators are discussed herein.</span></span>  
  
## <a name="comparing-numeric-values"></a><span data-ttu-id="6b97c-107">Сравнение числовых значений</span><span class="sxs-lookup"><span data-stu-id="6b97c-107">Comparing Numeric Values</span></span>  

 <span data-ttu-id="6b97c-108">Visual Basic сравнивает числовые значения с помощью шести числовых операторов сравнения.</span><span class="sxs-lookup"><span data-stu-id="6b97c-108">Visual Basic compares numeric values using six numeric comparison operators.</span></span> <span data-ttu-id="6b97c-109">Каждый оператор принимает в качестве операндов два выражения, результатом вычисления которых являются числовые значения.</span><span class="sxs-lookup"><span data-stu-id="6b97c-109">Each operator takes as operands two expressions that evaluate to numeric values.</span></span> <span data-ttu-id="6b97c-110">В следующей таблице перечислены операторы и приведены примеры каждого из них.</span><span class="sxs-lookup"><span data-stu-id="6b97c-110">The following table lists the operators and shows examples of each.</span></span>  
  
|<span data-ttu-id="6b97c-111">Оператор</span><span class="sxs-lookup"><span data-stu-id="6b97c-111">Operator</span></span>|<span data-ttu-id="6b97c-112">Проверяемое условие</span><span class="sxs-lookup"><span data-stu-id="6b97c-112">Condition tested</span></span>|<span data-ttu-id="6b97c-113">Примеры</span><span class="sxs-lookup"><span data-stu-id="6b97c-113">Examples</span></span>|  
|--------------|----------------------|--------------|  
|<span data-ttu-id="6b97c-114">`=` Проверке</span><span class="sxs-lookup"><span data-stu-id="6b97c-114">`=` (Equality)</span></span>|<span data-ttu-id="6b97c-115">Значение первого выражения, равное значению второго?</span><span class="sxs-lookup"><span data-stu-id="6b97c-115">Is the value of the first expression equal to the value of the second?</span></span>|<span data-ttu-id="6b97c-116">`23`   `=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="6b97c-116">`23`   `=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="6b97c-117">`23`   `=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="6b97c-117">`23`   `=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="6b97c-118">`23`   `=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="6b97c-118">`23`   `=`   `12    ' False`</span></span>|  
|<span data-ttu-id="6b97c-119">`<>` Неравенство</span><span class="sxs-lookup"><span data-stu-id="6b97c-119">`<>` (Inequality)</span></span>|<span data-ttu-id="6b97c-120">Значение первого выражения, не равное значению второго?</span><span class="sxs-lookup"><span data-stu-id="6b97c-120">Is the value of the first expression unequal to the value of the second?</span></span>|<span data-ttu-id="6b97c-121">`23`   `<>`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="6b97c-121">`23`   `<>`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="6b97c-122">`23`   `<>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="6b97c-122">`23`   `<>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="6b97c-123">`23`   `<>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="6b97c-123">`23`   `<>`   `12    ' True`</span></span>|  
|<span data-ttu-id="6b97c-124">`<` (Меньше)</span><span class="sxs-lookup"><span data-stu-id="6b97c-124">`<` (Less than)</span></span>|<span data-ttu-id="6b97c-125">Значение первого выражения меньше значения второго?</span><span class="sxs-lookup"><span data-stu-id="6b97c-125">Is the value of the first expression less than the value of the second?</span></span>|<span data-ttu-id="6b97c-126">`23`   `<`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="6b97c-126">`23`   `<`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="6b97c-127">`23`   `<`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="6b97c-127">`23`   `<`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="6b97c-128">`23`   `<`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="6b97c-128">`23`   `<`   `12    ' False`</span></span>|  
|<span data-ttu-id="6b97c-129">`>` (Больше)</span><span class="sxs-lookup"><span data-stu-id="6b97c-129">`>` (Greater than)</span></span>|<span data-ttu-id="6b97c-130">Значение первого выражения, превышающего значение второго?</span><span class="sxs-lookup"><span data-stu-id="6b97c-130">Is the value of the first expression greater than the value of the second?</span></span>|<span data-ttu-id="6b97c-131">`23`   `>`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="6b97c-131">`23`   `>`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="6b97c-132">`23`   `>`   `23    ' False`</span><span class="sxs-lookup"><span data-stu-id="6b97c-132">`23`   `>`   `23    ' False`</span></span><br /><br /> <span data-ttu-id="6b97c-133">`23`   `>`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="6b97c-133">`23`   `>`   `12    ' True`</span></span>|  
|<span data-ttu-id="6b97c-134">`<=` (Меньше или равно)</span><span class="sxs-lookup"><span data-stu-id="6b97c-134">`<=` (Less than or equal to)</span></span>|<span data-ttu-id="6b97c-135">Значение первого выражения, которое меньше или равно значению второго?</span><span class="sxs-lookup"><span data-stu-id="6b97c-135">Is the value of the first expression less than or equal to the value of the second?</span></span>|<span data-ttu-id="6b97c-136">`23`   `<=`   `33    ' True`</span><span class="sxs-lookup"><span data-stu-id="6b97c-136">`23`   `<=`   `33    ' True`</span></span><br /><br /> <span data-ttu-id="6b97c-137">`23`   `<=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="6b97c-137">`23`   `<=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="6b97c-138">`23`   `<=`   `12    ' False`</span><span class="sxs-lookup"><span data-stu-id="6b97c-138">`23`   `<=`   `12    ' False`</span></span>|  
|<span data-ttu-id="6b97c-139">`>=` (Больше или равно)</span><span class="sxs-lookup"><span data-stu-id="6b97c-139">`>=` (Greater than or equal to)</span></span>|<span data-ttu-id="6b97c-140">Значение первого выражения, которое больше или равно значению второго?</span><span class="sxs-lookup"><span data-stu-id="6b97c-140">Is the value of the first expression greater than or equal to the value of the second?</span></span>|<span data-ttu-id="6b97c-141">`23`   `>=`   `33    ' False`</span><span class="sxs-lookup"><span data-stu-id="6b97c-141">`23`   `>=`   `33    ' False`</span></span><br /><br /> <span data-ttu-id="6b97c-142">`23`   `>=`   `23    ' True`</span><span class="sxs-lookup"><span data-stu-id="6b97c-142">`23`   `>=`   `23    ' True`</span></span><br /><br /> <span data-ttu-id="6b97c-143">`23`   `>=`   `12    ' True`</span><span class="sxs-lookup"><span data-stu-id="6b97c-143">`23`   `>=`   `12    ' True`</span></span>|  
  
## <a name="comparing-strings"></a><span data-ttu-id="6b97c-144">Сравнение строк</span><span class="sxs-lookup"><span data-stu-id="6b97c-144">Comparing Strings</span></span>  

 <span data-ttu-id="6b97c-145">Visual Basic сравнивает строки с помощью [оператора Like](../../../language-reference/operators/like-operator.md) , а также числовых операторов сравнения.</span><span class="sxs-lookup"><span data-stu-id="6b97c-145">Visual Basic compares strings using the [Like Operator](../../../language-reference/operators/like-operator.md) as well as the numeric comparison operators.</span></span> <span data-ttu-id="6b97c-146">`Like`Оператор позволяет указать шаблон.</span><span class="sxs-lookup"><span data-stu-id="6b97c-146">The `Like` operator allows you to specify a pattern.</span></span> <span data-ttu-id="6b97c-147">Затем Строка сравнивается с шаблоном, и, если она соответствует, результатом будет `True` .</span><span class="sxs-lookup"><span data-stu-id="6b97c-147">The string is then compared against the pattern, and if it matches, the result is `True`.</span></span> <span data-ttu-id="6b97c-148">В противном случае результат будет `False`.</span><span class="sxs-lookup"><span data-stu-id="6b97c-148">Otherwise, the result is `False`.</span></span> <span data-ttu-id="6b97c-149">Числовые операторы позволяют сравнивать значения на `String` основе их порядка сортировки, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6b97c-149">The numeric operators allow you to compare `String` values based on their sort order, as the following example shows.</span></span>  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="6b97c-150">Результатом в предыдущем примере является то, `True` что первый символ в первой строке сортируется перед первым символом во второй строке.</span><span class="sxs-lookup"><span data-stu-id="6b97c-150">The result in the preceding example is `True` because the first character in the first string sorts before the first character in the second string.</span></span> <span data-ttu-id="6b97c-151">Если первые символы равны, то сравнение будет продолжаться со следующим символом в обеих строках и т. д.</span><span class="sxs-lookup"><span data-stu-id="6b97c-151">If the first characters were equal, the comparison would continue to the next character in both strings, and so on.</span></span> <span data-ttu-id="6b97c-152">Можно также проверить равенство строк с помощью оператора равенства, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6b97c-152">You can also test equality of strings using the equality operator, as the following example shows.</span></span>  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="6b97c-153">Если одна строка является префиксом другой, например "AA" и "AAA", более длинная строка считается больше чем укороченная строка.</span><span class="sxs-lookup"><span data-stu-id="6b97c-153">If one string is a prefix of another, such as "aa" and "aaa", the longer string is considered to be greater than the shorter string.</span></span> <span data-ttu-id="6b97c-154">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6b97c-154">The following example illustrates this.</span></span>  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 <span data-ttu-id="6b97c-155">Порядок сортировки основан на двоичном сравнении или текстовом сравнении в зависимости от значения параметра `Option Compare` .</span><span class="sxs-lookup"><span data-stu-id="6b97c-155">The sort order is based on either a binary comparison or a textual comparison depending on the setting of `Option Compare`.</span></span> <span data-ttu-id="6b97c-156">Дополнительные сведения см. в разделе [вариант инструкции Compare](../../../language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6b97c-156">For more information see [Option Compare Statement](../../../language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="comparing-objects"></a><span data-ttu-id="6b97c-157">Сравнение объектов</span><span class="sxs-lookup"><span data-stu-id="6b97c-157">Comparing Objects</span></span>  

 <span data-ttu-id="6b97c-158">Visual Basic сравнивает две переменные ссылки на объект с помощью [оператора is](../../../language-reference/operators/is-operator.md) и [оператора IsNot](../../../language-reference/operators/isnot-operator.md).</span><span class="sxs-lookup"><span data-stu-id="6b97c-158">Visual Basic compares two object reference variables with the [Is Operator](../../../language-reference/operators/is-operator.md) and the [IsNot Operator](../../../language-reference/operators/isnot-operator.md).</span></span> <span data-ttu-id="6b97c-159">Чтобы определить, ссылаются ли две ссылочные переменные на один и тот же экземпляр объекта, можно использовать любой из этих операторов.</span><span class="sxs-lookup"><span data-stu-id="6b97c-159">You can use either of these operators to determine if two reference variables refer to the same object instance.</span></span> <span data-ttu-id="6b97c-160">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6b97c-160">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 <span data-ttu-id="6b97c-161">В предыдущем примере `x Is y` принимает значение `True` , так как обе переменные ссылаются на один и тот же экземпляр.</span><span class="sxs-lookup"><span data-stu-id="6b97c-161">In the preceding example, `x Is y` evaluates to `True`, because both variables refer to the same instance.</span></span> <span data-ttu-id="6b97c-162">Сравните этот результат со следующим примером.</span><span class="sxs-lookup"><span data-stu-id="6b97c-162">Contrast this result with the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 <span data-ttu-id="6b97c-163">В предыдущем примере принимает значение `x Is y` `False` , поскольку хотя переменные ссылаются на объекты одного типа, они ссылаются на разные экземпляры этого типа.</span><span class="sxs-lookup"><span data-stu-id="6b97c-163">In the preceding example, `x Is y` evaluates to `False`, because although the variables refer to objects of the same type, they refer to different instances of that type.</span></span>  
  
 <span data-ttu-id="6b97c-164">Если требуется проверить наличие двух объектов, не указывающих на один и тот же экземпляр, `IsNot` оператор позволяет избежать сочетания грамматически неловкий `Not` и `Is` .</span><span class="sxs-lookup"><span data-stu-id="6b97c-164">When you want to test for two objects not pointing to the same instance, the `IsNot` operator lets you avoid a grammatically clumsy combination of `Not` and `Is`.</span></span> <span data-ttu-id="6b97c-165">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6b97c-165">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 <span data-ttu-id="6b97c-166">В предыдущем примере `If a IsNot b` эквивалентно `If Not a Is b` .</span><span class="sxs-lookup"><span data-stu-id="6b97c-166">In the preceding example, `If a IsNot b` is equivalent to `If Not a Is b`.</span></span>  
  
### <a name="comparing-object-type"></a><span data-ttu-id="6b97c-167">Сравнение типа объекта</span><span class="sxs-lookup"><span data-stu-id="6b97c-167">Comparing Object Type</span></span>  

 <span data-ttu-id="6b97c-168">Можно проверить, относится ли объект к определенному типу с помощью `TypeOf` выражения... `Is` .</span><span class="sxs-lookup"><span data-stu-id="6b97c-168">You can test whether an object is of a particular type with the `TypeOf`...`Is` expression.</span></span> <span data-ttu-id="6b97c-169">Синтаксис выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6b97c-169">The syntax is as follows:</span></span>  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 <span data-ttu-id="6b97c-170">Если `typename` указывает тип интерфейса, `TypeOf` выражение... Возвращает, `Is` `True` Если объект реализует тип интерфейса.</span><span class="sxs-lookup"><span data-stu-id="6b97c-170">When `typename` specifies an interface type, then the `TypeOf`...`Is` expression returns `True` if the object implements the interface type.</span></span> <span data-ttu-id="6b97c-171">Если `typename` является типом класса, выражение возвращает значение, `True` Если объект является экземпляром указанного класса или класса, производного от указанного класса.</span><span class="sxs-lookup"><span data-stu-id="6b97c-171">When `typename` is a class type, then the expression returns `True` if the object is an instance of the specified class or of a class that derives from the specified class.</span></span> <span data-ttu-id="6b97c-172">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6b97c-172">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 <span data-ttu-id="6b97c-173">В приведенном выше примере `TypeOf x Is Control` результатом вычисления выражения `True` `x` является тип `Button` , который наследует от `Control` .</span><span class="sxs-lookup"><span data-stu-id="6b97c-173">In the preceding example, the `TypeOf x Is Control` expression evaluates to `True` because the type of `x` is `Button`, which inherits from `Control`.</span></span>  
  
 <span data-ttu-id="6b97c-174">Дополнительные сведения см. в разделе [оператор typeof](../../../language-reference/operators/typeof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="6b97c-174">For more information, see [TypeOf Operator](../../../language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b97c-175">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6b97c-175">See also</span></span>

- [<span data-ttu-id="6b97c-176">Сравнения значений</span><span class="sxs-lookup"><span data-stu-id="6b97c-176">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="6b97c-177">Операторы сравнения</span><span class="sxs-lookup"><span data-stu-id="6b97c-177">Comparison Operators</span></span>](../../../language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="6b97c-178">Операторы</span><span class="sxs-lookup"><span data-stu-id="6b97c-178">Operators</span></span>](../../../language-reference/operators/index.md)
- [<span data-ttu-id="6b97c-179">Арифметические операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b97c-179">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="6b97c-180">Операторы объединения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b97c-180">Concatenation Operators in Visual Basic</span></span>](concatenation-operators.md)
- [<span data-ttu-id="6b97c-181">Логические и побитовые операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b97c-181">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
