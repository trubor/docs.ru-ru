---
description: Дополнительные сведения о операторе or (Visual Basic)
title: Оператор Or
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: dfc50af2298c162707976e4b2eda9e9536aa64bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730334"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="48ae6-103">Оператор Or (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48ae6-103">Or Operator (Visual Basic)</span></span>

<span data-ttu-id="48ae6-104">Выполняет логическое сложение двух `Boolean` выражений или побитовое сложение двух числовых выражений.</span><span class="sxs-lookup"><span data-stu-id="48ae6-104">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48ae6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="48ae6-105">Syntax</span></span>  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="48ae6-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="48ae6-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="48ae6-107">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="48ae6-107">Required.</span></span> <span data-ttu-id="48ae6-108">Произвольное выражение типа `Boolean` или числового типа.</span><span class="sxs-lookup"><span data-stu-id="48ae6-108">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="48ae6-109">Для `Boolean` сравнения `result` — это включающее логическое сложение двух `Boolean` значений.</span><span class="sxs-lookup"><span data-stu-id="48ae6-109">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="48ae6-110">Для битовых операций `result` — это числовое значение, представляющее включающее побитовое сложение двух числовых битов.</span><span class="sxs-lookup"><span data-stu-id="48ae6-110">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="48ae6-111">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="48ae6-111">Required.</span></span> <span data-ttu-id="48ae6-112">Произвольное выражение типа `Boolean` или числового типа.</span><span class="sxs-lookup"><span data-stu-id="48ae6-112">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="48ae6-113">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="48ae6-113">Required.</span></span> <span data-ttu-id="48ae6-114">Произвольное выражение типа `Boolean` или числового типа.</span><span class="sxs-lookup"><span data-stu-id="48ae6-114">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48ae6-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="48ae6-115">Remarks</span></span>  

 <span data-ttu-id="48ae6-116">Для `Boolean` сравнения `result` параметр имеет значение, `False` только если оба `expression1` `expression2` значения и имеют значение `False` .</span><span class="sxs-lookup"><span data-stu-id="48ae6-116">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="48ae6-117">В следующей таблице показано, как `result` определяется.</span><span class="sxs-lookup"><span data-stu-id="48ae6-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="48ae6-118">Если `expression1` имеет значение </span><span class="sxs-lookup"><span data-stu-id="48ae6-118">If `expression1` is</span></span>|<span data-ttu-id="48ae6-119">И `expression2` является</span><span class="sxs-lookup"><span data-stu-id="48ae6-119">And `expression2` is</span></span>|<span data-ttu-id="48ae6-120">Значение `result` равно</span><span class="sxs-lookup"><span data-stu-id="48ae6-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="48ae6-121">В `Boolean` сравнении `Or` оператор всегда вычисляет оба выражения, которые могут включать вызовы процедур.</span><span class="sxs-lookup"><span data-stu-id="48ae6-121">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="48ae6-122">[Оператор OrElse](orelse-operator.md) выполняет *сокращенное вычисление*, означающее, что если `expression1` имеет значение `True` , то `expression2` не вычисляется.</span><span class="sxs-lookup"><span data-stu-id="48ae6-122">The [OrElse Operator](orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="48ae6-123">Для побитовых операций `Or` оператор выполняет побитовое сравнение одинаково позиционированных битов в двух числовых выражениях и устанавливает соответствующий бит в `result` соответствии со следующей таблицей.</span><span class="sxs-lookup"><span data-stu-id="48ae6-123">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="48ae6-124">Если бит в `expression1` имеет значение</span><span class="sxs-lookup"><span data-stu-id="48ae6-124">If bit in `expression1` is</span></span>|<span data-ttu-id="48ae6-125">И bit в `expression2` имеет</span><span class="sxs-lookup"><span data-stu-id="48ae6-125">And bit in `expression2` is</span></span>|<span data-ttu-id="48ae6-126">Бит в `result` имеет значение</span><span class="sxs-lookup"><span data-stu-id="48ae6-126">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="48ae6-127">1</span><span class="sxs-lookup"><span data-stu-id="48ae6-127">1</span></span>|<span data-ttu-id="48ae6-128">1</span><span class="sxs-lookup"><span data-stu-id="48ae6-128">1</span></span>|<span data-ttu-id="48ae6-129">1</span><span class="sxs-lookup"><span data-stu-id="48ae6-129">1</span></span>|  
|<span data-ttu-id="48ae6-130">1</span><span class="sxs-lookup"><span data-stu-id="48ae6-130">1</span></span>|<span data-ttu-id="48ae6-131">0</span><span class="sxs-lookup"><span data-stu-id="48ae6-131">0</span></span>|<span data-ttu-id="48ae6-132">1</span><span class="sxs-lookup"><span data-stu-id="48ae6-132">1</span></span>|  
|<span data-ttu-id="48ae6-133">0</span><span class="sxs-lookup"><span data-stu-id="48ae6-133">0</span></span>|<span data-ttu-id="48ae6-134">1</span><span class="sxs-lookup"><span data-stu-id="48ae6-134">1</span></span>|<span data-ttu-id="48ae6-135">1</span><span class="sxs-lookup"><span data-stu-id="48ae6-135">1</span></span>|  
|<span data-ttu-id="48ae6-136">0</span><span class="sxs-lookup"><span data-stu-id="48ae6-136">0</span></span>|<span data-ttu-id="48ae6-137">0</span><span class="sxs-lookup"><span data-stu-id="48ae6-137">0</span></span>|<span data-ttu-id="48ae6-138">0</span><span class="sxs-lookup"><span data-stu-id="48ae6-138">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="48ae6-139">Так как логические и побитовые операторы имеют более низкий приоритет, чем другие арифметические и реляционные операторы, все битовые операции должны быть заключены в круглые скобки, чтобы обеспечить точное выполнение.</span><span class="sxs-lookup"><span data-stu-id="48ae6-139">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="48ae6-140">Типы данных</span><span class="sxs-lookup"><span data-stu-id="48ae6-140">Data Types</span></span>  

 <span data-ttu-id="48ae6-141">Если операнды состоят из одного `Boolean` выражения и одного числового выражения, Visual Basic преобразует `Boolean` выражение в числовое значение (– 1 для `True` и 0 для `False` ) и выполняет побитовую операцию.</span><span class="sxs-lookup"><span data-stu-id="48ae6-141">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="48ae6-142">Для `Boolean` сравнения тип данных результата — `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="48ae6-142">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="48ae6-143">Для побитового сравнения тип данных результата является числовым типом, подходящим для типов данных `expression1` и `expression2` .</span><span class="sxs-lookup"><span data-stu-id="48ae6-143">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="48ae6-144">См. таблицу "реляционные и побитовые сравнения" в разделе [типы данных результатов операторов](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="48ae6-144">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="48ae6-145">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="48ae6-145">Overloading</span></span>  

 <span data-ttu-id="48ae6-146">`Or`Оператор можно *перегрузить*, что означает, что класс или структура может переопределить свое поведение, когда операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="48ae6-146">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="48ae6-147">Если код использует этот оператор для такого класса или структуры, убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="48ae6-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="48ae6-148">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="48ae6-148">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48ae6-149">Пример</span><span class="sxs-lookup"><span data-stu-id="48ae6-149">Example</span></span>  

 <span data-ttu-id="48ae6-150">В следующем примере оператор используется `Or` для выполнения включающего логического сложения двух выражений.</span><span class="sxs-lookup"><span data-stu-id="48ae6-150">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="48ae6-151">Результатом является `Boolean` значение, которое представляет, является ли одно из двух выражений `True` .</span><span class="sxs-lookup"><span data-stu-id="48ae6-151">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="48ae6-152">В предыдущем примере создаются результаты `True` , `True` и `False` соответственно.</span><span class="sxs-lookup"><span data-stu-id="48ae6-152">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48ae6-153">Пример</span><span class="sxs-lookup"><span data-stu-id="48ae6-153">Example</span></span>  

 <span data-ttu-id="48ae6-154">В следующем примере оператор используется `Or` для выполнения инклюзивного логического сложения по отдельным битам двух числовых выражений.</span><span class="sxs-lookup"><span data-stu-id="48ae6-154">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="48ae6-155">Бит в результирующем шаблоне задается, если один из соответствующих битов операндов имеет значение 1.</span><span class="sxs-lookup"><span data-stu-id="48ae6-155">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="48ae6-156">В предыдущем примере выдается результат 10, 14 и 14 соответственно.</span><span class="sxs-lookup"><span data-stu-id="48ae6-156">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ae6-157">См. также</span><span class="sxs-lookup"><span data-stu-id="48ae6-157">See also</span></span>

- [<span data-ttu-id="48ae6-158">Логические (побитовые) операторы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48ae6-158">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="48ae6-159">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="48ae6-159">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="48ae6-160">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="48ae6-160">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="48ae6-161">Оператор OrElse</span><span class="sxs-lookup"><span data-stu-id="48ae6-161">OrElse Operator</span></span>](orelse-operator.md)
- [<span data-ttu-id="48ae6-162">Логические и побитовые операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="48ae6-162">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
