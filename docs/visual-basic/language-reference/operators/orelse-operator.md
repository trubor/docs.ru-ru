---
description: 'Дополнительные сведения: оператор OrElse (Visual Basic)'
title: Оператор OrElse
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 48ccbda1e0cb4f655b28e902b22fbfe0c3e66ac8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795330"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="dea22-103">Оператор OrElse (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dea22-103">OrElse Operator (Visual Basic)</span></span>

<span data-ttu-id="dea22-104">Выполняет сокращенное вычисление инклюзивного логического сложения двух выражений.</span><span class="sxs-lookup"><span data-stu-id="dea22-104">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dea22-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dea22-105">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="dea22-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="dea22-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="dea22-107">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="dea22-107">Required.</span></span> <span data-ttu-id="dea22-108">Произвольное выражение `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="dea22-108">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="dea22-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="dea22-109">Required.</span></span> <span data-ttu-id="dea22-110">Произвольное выражение `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="dea22-110">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="dea22-111">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="dea22-111">Required.</span></span> <span data-ttu-id="dea22-112">Произвольное выражение `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="dea22-112">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dea22-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="dea22-113">Remarks</span></span>  

 <span data-ttu-id="dea22-114">Логическая операция называется *сокращенной* , если скомпилированный код может обходить вычисление одного выражения в зависимости от результата другого выражения.</span><span class="sxs-lookup"><span data-stu-id="dea22-114">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="dea22-115">Если результат вычисления первого выражения определяет окончательный результат операции, нет необходимости оценивать второе выражение, так как оно не может изменить окончательный результат.</span><span class="sxs-lookup"><span data-stu-id="dea22-115">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="dea22-116">Сокращенное вычисление может повысить производительность, если пропущенное выражение является сложным или если оно включает вызовы процедур.</span><span class="sxs-lookup"><span data-stu-id="dea22-116">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="dea22-117">Если одно или оба выражения имеют значение `True` , `result` то имеет значение `True` .</span><span class="sxs-lookup"><span data-stu-id="dea22-117">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="dea22-118">В следующей таблице показано, как `result` определяется.</span><span class="sxs-lookup"><span data-stu-id="dea22-118">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="dea22-119">Если `expression1` имеет значение </span><span class="sxs-lookup"><span data-stu-id="dea22-119">If `expression1` is</span></span>|<span data-ttu-id="dea22-120">И `expression2` является</span><span class="sxs-lookup"><span data-stu-id="dea22-120">And `expression2` is</span></span>|<span data-ttu-id="dea22-121">Значение `result` равно</span><span class="sxs-lookup"><span data-stu-id="dea22-121">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="dea22-122">(не вычислено)</span><span class="sxs-lookup"><span data-stu-id="dea22-122">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="dea22-123">Типы данных</span><span class="sxs-lookup"><span data-stu-id="dea22-123">Data Types</span></span>  

 <span data-ttu-id="dea22-124">`OrElse`Оператор определен только для [типа данных Boolean](../data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="dea22-124">The `OrElse` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="dea22-125">При необходимости Visual Basic преобразует каждый операнд в `Boolean` перед вычислением выражения.</span><span class="sxs-lookup"><span data-stu-id="dea22-125">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="dea22-126">Если результат присваивается числовому типу, Visual Basic преобразует его в `Boolean` этот тип, который `False` станет `0` и `True` станет `-1` .</span><span class="sxs-lookup"><span data-stu-id="dea22-126">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="dea22-127">Дополнительные сведения см. в разделе [преобразования логических типов](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="dea22-127">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="dea22-128">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="dea22-128">Overloading</span></span>  

 <span data-ttu-id="dea22-129">[Оператор OR](or-operator.md) и [оператор IsTrue](istrue-operator.md) могут быть *перегружены*, что означает, что класс или структура может переопределить их поведение, если операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="dea22-129">The [Or Operator](or-operator.md) and the [IsTrue Operator](istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="dea22-130">Перегрузка `Or` `IsTrue` операторов и влияет на поведение `OrElse` оператора.</span><span class="sxs-lookup"><span data-stu-id="dea22-130">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="dea22-131">Если код использует `OrElse` класс или структуру, перегрузку `Or` и `IsTrue` , убедитесь, что вы понимаете их переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="dea22-131">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="dea22-132">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="dea22-132">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dea22-133">Пример</span><span class="sxs-lookup"><span data-stu-id="dea22-133">Example</span></span>  

 <span data-ttu-id="dea22-134">В следующем примере оператор используется `OrElse` для выполнения логического сложения двух выражений.</span><span class="sxs-lookup"><span data-stu-id="dea22-134">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="dea22-135">Результатом является `Boolean` значение, которое показывает, имеет ли одно из двух выражений значение true.</span><span class="sxs-lookup"><span data-stu-id="dea22-135">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="dea22-136">Если первое выражение равно `True` , второе не вычисляется.</span><span class="sxs-lookup"><span data-stu-id="dea22-136">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="dea22-137">В предыдущем примере создаются результаты `True` , `True` и `False` соответственно.</span><span class="sxs-lookup"><span data-stu-id="dea22-137">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="dea22-138">В вычислении `firstCheck` второе выражение не вычисляется, так как первый уже существует `True` .</span><span class="sxs-lookup"><span data-stu-id="dea22-138">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="dea22-139">Однако второе выражение вычисляется в вычислении `secondCheck` .</span><span class="sxs-lookup"><span data-stu-id="dea22-139">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dea22-140">Пример</span><span class="sxs-lookup"><span data-stu-id="dea22-140">Example</span></span>  

 <span data-ttu-id="dea22-141">В следующем примере показан `If` оператор..., `Then` содержащий два вызова процедуры.</span><span class="sxs-lookup"><span data-stu-id="dea22-141">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="dea22-142">Если первый вызов возвращает `True` , вторая процедура не вызывается.</span><span class="sxs-lookup"><span data-stu-id="dea22-142">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="dea22-143">Это может привести к непредвиденным результатам, если вторая процедура выполняет важные задачи, которые всегда должны выполняться при выполнении этого раздела кода.</span><span class="sxs-lookup"><span data-stu-id="dea22-143">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="dea22-144">См. также</span><span class="sxs-lookup"><span data-stu-id="dea22-144">See also</span></span>

- [<span data-ttu-id="dea22-145">Логические (побитовые) операторы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dea22-145">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="dea22-146">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dea22-146">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="dea22-147">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="dea22-147">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="dea22-148">Оператор Or</span><span class="sxs-lookup"><span data-stu-id="dea22-148">Or Operator</span></span>](or-operator.md)
- [<span data-ttu-id="dea22-149">Оператор IsTrue</span><span class="sxs-lookup"><span data-stu-id="dea22-149">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="dea22-150">Логические и побитовые операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dea22-150">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
