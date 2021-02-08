---
description: 'Дополнительные сведения: оператор AndAlso (Visual Basic)'
title: Оператор AndAlso
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: dcf6c2685bf8f9ffee27b00543786cd3b315b327
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774269"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="0af97-103">Оператор AndAlso (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0af97-103">AndAlso Operator (Visual Basic)</span></span>

<span data-ttu-id="0af97-104">Выполняет сокращенное вычисление логического умножения двух выражений.</span><span class="sxs-lookup"><span data-stu-id="0af97-104">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0af97-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0af97-105">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="0af97-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="0af97-106">Parts</span></span>  
  
|<span data-ttu-id="0af97-107">Термин</span><span class="sxs-lookup"><span data-stu-id="0af97-107">Term</span></span>|<span data-ttu-id="0af97-108">Определение</span><span class="sxs-lookup"><span data-stu-id="0af97-108">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="0af97-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="0af97-109">Required.</span></span> <span data-ttu-id="0af97-110">Произвольное выражение `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="0af97-110">Any `Boolean` expression.</span></span> <span data-ttu-id="0af97-111">Результатом `Boolean` сравнения двух выражений является результат.</span><span class="sxs-lookup"><span data-stu-id="0af97-111">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="0af97-112">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="0af97-112">Required.</span></span> <span data-ttu-id="0af97-113">Произвольное выражение `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="0af97-113">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="0af97-114">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="0af97-114">Required.</span></span> <span data-ttu-id="0af97-115">Произвольное выражение `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="0af97-115">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0af97-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="0af97-116">Remarks</span></span>  

 <span data-ttu-id="0af97-117">Логическая операция называется *сокращенной* , если скомпилированный код может обходить вычисление одного выражения в зависимости от результата другого выражения.</span><span class="sxs-lookup"><span data-stu-id="0af97-117">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="0af97-118">Если результат вычисления первого выражения определяет окончательный результат операции, нет необходимости оценивать второе выражение, так как оно не может изменить окончательный результат.</span><span class="sxs-lookup"><span data-stu-id="0af97-118">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="0af97-119">Сокращенное вычисление может повысить производительность, если пропущенное выражение является сложным или если оно включает вызовы процедур.</span><span class="sxs-lookup"><span data-stu-id="0af97-119">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="0af97-120">Если оба выражения имеют значение `True` , `result` то имеет значение `True` .</span><span class="sxs-lookup"><span data-stu-id="0af97-120">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="0af97-121">В следующей таблице показано, как `result` определяется.</span><span class="sxs-lookup"><span data-stu-id="0af97-121">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="0af97-122">Если `expression1` имеет значение </span><span class="sxs-lookup"><span data-stu-id="0af97-122">If `expression1` is</span></span>|<span data-ttu-id="0af97-123">И `expression2` является</span><span class="sxs-lookup"><span data-stu-id="0af97-123">And `expression2` is</span></span>|<span data-ttu-id="0af97-124">Значение `result` равно</span><span class="sxs-lookup"><span data-stu-id="0af97-124">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="0af97-125">(не вычислено)</span><span class="sxs-lookup"><span data-stu-id="0af97-125">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="0af97-126">Типы данных</span><span class="sxs-lookup"><span data-stu-id="0af97-126">Data Types</span></span>  

 <span data-ttu-id="0af97-127">`AndAlso`Оператор определен только для [типа данных Boolean](../data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="0af97-127">The `AndAlso` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="0af97-128">При необходимости Visual Basic преобразует каждый операнд в `Boolean` перед вычислением выражения.</span><span class="sxs-lookup"><span data-stu-id="0af97-128">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="0af97-129">Если результат присваивается числовому типу, Visual Basic преобразует его в `Boolean` этот тип, который `False` станет `0` и `True` станет `-1` .</span><span class="sxs-lookup"><span data-stu-id="0af97-129">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="0af97-130">Дополнительные сведения см. в разделе [преобразования логических типов](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="0af97-130">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="0af97-131">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="0af97-131">Overloading</span></span>  

 <span data-ttu-id="0af97-132">[Операторы and](and-operator.md) и [IsFalse](isfalse-operator.md) можно *перегружать*, что означает, что класс или структура могут переопределять их поведение, когда операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="0af97-132">The [And Operator](and-operator.md) and the [IsFalse Operator](isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0af97-133">Перегрузка `And` `IsFalse` операторов и влияет на поведение `AndAlso` оператора.</span><span class="sxs-lookup"><span data-stu-id="0af97-133">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="0af97-134">Если код использует `AndAlso` класс или структуру, перегрузку `And` и `IsFalse` , убедитесь, что вы понимаете их переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="0af97-134">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="0af97-135">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0af97-135">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0af97-136">Пример</span><span class="sxs-lookup"><span data-stu-id="0af97-136">Example</span></span>  

 <span data-ttu-id="0af97-137">В следующем примере оператор используется `AndAlso` для выполнения логического умножения двух выражений.</span><span class="sxs-lookup"><span data-stu-id="0af97-137">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="0af97-138">Результат представляет собой `Boolean` значение, которое показывает, является ли выражение истинным.</span><span class="sxs-lookup"><span data-stu-id="0af97-138">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="0af97-139">Если первое выражение равно `False` , второе не вычисляется.</span><span class="sxs-lookup"><span data-stu-id="0af97-139">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="0af97-140">В предыдущем примере создаются результаты `True` , `False` и `False` соответственно.</span><span class="sxs-lookup"><span data-stu-id="0af97-140">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="0af97-141">В вычислении `secondCheck` второе выражение не вычисляется, так как первый уже существует `False` .</span><span class="sxs-lookup"><span data-stu-id="0af97-141">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="0af97-142">Однако второе выражение вычисляется в вычислении `thirdCheck` .</span><span class="sxs-lookup"><span data-stu-id="0af97-142">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0af97-143">Пример</span><span class="sxs-lookup"><span data-stu-id="0af97-143">Example</span></span>  

 <span data-ttu-id="0af97-144">В следующем примере показана `Function` процедура поиска заданного значения в элементах массива.</span><span class="sxs-lookup"><span data-stu-id="0af97-144">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="0af97-145">Если массив пуст или если длина массива была превышена, `While` инструкция не проверяет элемент массива на соответствие значению поиска.</span><span class="sxs-lookup"><span data-stu-id="0af97-145">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="0af97-146">См. также</span><span class="sxs-lookup"><span data-stu-id="0af97-146">See also</span></span>

- [<span data-ttu-id="0af97-147">Логические (побитовые) операторы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0af97-147">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="0af97-148">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0af97-148">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="0af97-149">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="0af97-149">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="0af97-150">Оператор And</span><span class="sxs-lookup"><span data-stu-id="0af97-150">And Operator</span></span>](and-operator.md)
- [<span data-ttu-id="0af97-151">Оператор IsFalse</span><span class="sxs-lookup"><span data-stu-id="0af97-151">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="0af97-152">Логические и побитовые операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0af97-152">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
