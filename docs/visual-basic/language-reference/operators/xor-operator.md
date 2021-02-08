---
description: Дополнительные сведения о операторе XOR (Visual Basic)
title: Оператор Xor
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: 313ff30ace91b1832c0d35df13294e570a8e410d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795226"
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="0b554-103">Оператор Xor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b554-103">Xor Operator (Visual Basic)</span></span>

<span data-ttu-id="0b554-104">Выполняет логическое исключение для двух `Boolean` выражений или побитовое исключение для двух числовых выражений.</span><span class="sxs-lookup"><span data-stu-id="0b554-104">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b554-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0b554-105">Syntax</span></span>  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="0b554-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="0b554-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="0b554-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="0b554-107">Required.</span></span> <span data-ttu-id="0b554-108">Любая `Boolean` или числовая переменная.</span><span class="sxs-lookup"><span data-stu-id="0b554-108">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="0b554-109">Для логического сравнения `result` — это логическое исключение (исключающее логическое сложение) двух `Boolean` значений.</span><span class="sxs-lookup"><span data-stu-id="0b554-109">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="0b554-110">Для битовых операций `result` — это числовое значение, представляющее побитовое исключение (исключающее побитовое сложение) двух числовых битов.</span><span class="sxs-lookup"><span data-stu-id="0b554-110">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="0b554-111">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="0b554-111">Required.</span></span> <span data-ttu-id="0b554-112">Произвольное выражение типа `Boolean` или числового типа.</span><span class="sxs-lookup"><span data-stu-id="0b554-112">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="0b554-113">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="0b554-113">Required.</span></span> <span data-ttu-id="0b554-114">Произвольное выражение типа `Boolean` или числового типа.</span><span class="sxs-lookup"><span data-stu-id="0b554-114">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b554-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="0b554-115">Remarks</span></span>  

 <span data-ttu-id="0b554-116">Для логического сравнения `result` параметр имеет значение, `True` только если в точности один из значений равен `expression1` `expression2` `True` .</span><span class="sxs-lookup"><span data-stu-id="0b554-116">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="0b554-117">То есть, если и только если `expression1` и `expression2` имеют противоположные `Boolean` значения.</span><span class="sxs-lookup"><span data-stu-id="0b554-117">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="0b554-118">В следующей таблице показано, как `result` определяется.</span><span class="sxs-lookup"><span data-stu-id="0b554-118">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="0b554-119">Если `expression1` имеет значение </span><span class="sxs-lookup"><span data-stu-id="0b554-119">If `expression1` is</span></span>|<span data-ttu-id="0b554-120">И `expression2` является</span><span class="sxs-lookup"><span data-stu-id="0b554-120">And `expression2` is</span></span>|<span data-ttu-id="0b554-121">Значение `result` равно</span><span class="sxs-lookup"><span data-stu-id="0b554-121">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="0b554-122">При логическом сравнении `Xor` оператор всегда вычисляет оба выражения, которые могут включать вызовы процедур.</span><span class="sxs-lookup"><span data-stu-id="0b554-122">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="0b554-123">Не существует аналога сокращенного `Xor` выражения, поскольку результат всегда зависит от обоих операндов.</span><span class="sxs-lookup"><span data-stu-id="0b554-123">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="0b554-124">Дополнительные операторы для *сокращенного* вычисления логических операторов см. в разделе [оператор AndAlso](andalso-operator.md) и [оператор OrElse](orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="0b554-124">For *short-circuiting* logical operators, see [AndAlso Operator](andalso-operator.md) and [OrElse Operator](orelse-operator.md).</span></span>  
  
 <span data-ttu-id="0b554-125">Для побитовых операций `Xor` оператор выполняет побитовое сравнение одинаково позиционированных битов в двух числовых выражениях и устанавливает соответствующий бит в `result` соответствии со следующей таблицей.</span><span class="sxs-lookup"><span data-stu-id="0b554-125">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="0b554-126">Если бит в `expression1` имеет значение</span><span class="sxs-lookup"><span data-stu-id="0b554-126">If bit in `expression1` is</span></span>|<span data-ttu-id="0b554-127">И bit в `expression2` имеет</span><span class="sxs-lookup"><span data-stu-id="0b554-127">And bit in `expression2` is</span></span>|<span data-ttu-id="0b554-128">Бит в `result` имеет значение</span><span class="sxs-lookup"><span data-stu-id="0b554-128">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="0b554-129">1</span><span class="sxs-lookup"><span data-stu-id="0b554-129">1</span></span>|<span data-ttu-id="0b554-130">1</span><span class="sxs-lookup"><span data-stu-id="0b554-130">1</span></span>|<span data-ttu-id="0b554-131">0</span><span class="sxs-lookup"><span data-stu-id="0b554-131">0</span></span>|  
|<span data-ttu-id="0b554-132">1</span><span class="sxs-lookup"><span data-stu-id="0b554-132">1</span></span>|<span data-ttu-id="0b554-133">0</span><span class="sxs-lookup"><span data-stu-id="0b554-133">0</span></span>|<span data-ttu-id="0b554-134">1</span><span class="sxs-lookup"><span data-stu-id="0b554-134">1</span></span>|  
|<span data-ttu-id="0b554-135">0</span><span class="sxs-lookup"><span data-stu-id="0b554-135">0</span></span>|<span data-ttu-id="0b554-136">1</span><span class="sxs-lookup"><span data-stu-id="0b554-136">1</span></span>|<span data-ttu-id="0b554-137">1</span><span class="sxs-lookup"><span data-stu-id="0b554-137">1</span></span>|  
|<span data-ttu-id="0b554-138">0</span><span class="sxs-lookup"><span data-stu-id="0b554-138">0</span></span>|<span data-ttu-id="0b554-139">0</span><span class="sxs-lookup"><span data-stu-id="0b554-139">0</span></span>|<span data-ttu-id="0b554-140">0</span><span class="sxs-lookup"><span data-stu-id="0b554-140">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="0b554-141">Так как логические и побитовые операторы имеют более низкий приоритет, чем другие арифметические и реляционные операторы, все битовые операции должны быть заключены в круглые скобки, чтобы обеспечить точное выполнение.</span><span class="sxs-lookup"><span data-stu-id="0b554-141">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="0b554-142">Например, 5 `Xor` 3 — 6.</span><span class="sxs-lookup"><span data-stu-id="0b554-142">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="0b554-143">Чтобы узнать, почему это так, преобразуйте значения 5 и 3 в двоичные представления, 101 и 011.</span><span class="sxs-lookup"><span data-stu-id="0b554-143">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="0b554-144">Затем используйте предыдущую таблицу, чтобы определить, что 101 Xor 011 имеет значение 110, которое является двоичным представлением десятичного числа 6.</span><span class="sxs-lookup"><span data-stu-id="0b554-144">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="0b554-145">Типы данных</span><span class="sxs-lookup"><span data-stu-id="0b554-145">Data Types</span></span>  

 <span data-ttu-id="0b554-146">Если операнды состоят из одного `Boolean` выражения и одного числового выражения, Visual Basic преобразует `Boolean` выражение в числовое значение (– 1 для `True` и 0 для `False` ) и выполняет побитовую операцию.</span><span class="sxs-lookup"><span data-stu-id="0b554-146">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="0b554-147">Для `Boolean` сравнения тип данных результата — `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="0b554-147">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="0b554-148">Для побитового сравнения тип данных результата является числовым типом, подходящим для типов данных `expression1` и `expression2` .</span><span class="sxs-lookup"><span data-stu-id="0b554-148">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="0b554-149">См. таблицу "реляционные и побитовые сравнения" в разделе [типы данных результатов операторов](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="0b554-149">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="0b554-150">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="0b554-150">Overloading</span></span>  

 <span data-ttu-id="0b554-151">`Xor`Оператор можно *перегрузить*, что означает, что класс или структура может переопределить свое поведение, когда операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="0b554-151">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0b554-152">Если код использует этот оператор для такого класса или структуры, убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="0b554-152">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="0b554-153">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0b554-153">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b554-154">Пример</span><span class="sxs-lookup"><span data-stu-id="0b554-154">Example</span></span>  

 <span data-ttu-id="0b554-155">В следующем примере оператор используется `Xor` для выполнения логического исключения (исключающее логическое сложение) в двух выражениях.</span><span class="sxs-lookup"><span data-stu-id="0b554-155">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="0b554-156">Результатом является `Boolean` значение, указывающее, имеет ли только одно из выражений `True` .</span><span class="sxs-lookup"><span data-stu-id="0b554-156">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 <span data-ttu-id="0b554-157">В предыдущем примере создаются результаты `False` , `True` и `False` соответственно.</span><span class="sxs-lookup"><span data-stu-id="0b554-157">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b554-158">Пример</span><span class="sxs-lookup"><span data-stu-id="0b554-158">Example</span></span>  

 <span data-ttu-id="0b554-159">В следующем примере оператор используется `Xor` для выполнения логического исключения (исключающее логическое сложение) для отдельных битов двух числовых выражений.</span><span class="sxs-lookup"><span data-stu-id="0b554-159">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="0b554-160">Бит в результирующем шаблоне устанавливается, если только один из соответствующих битов операндов имеет значение 1.</span><span class="sxs-lookup"><span data-stu-id="0b554-160">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 <span data-ttu-id="0b554-161">В предыдущем примере выдается результат 2, 12 и 14 соответственно.</span><span class="sxs-lookup"><span data-stu-id="0b554-161">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b554-162">См. также</span><span class="sxs-lookup"><span data-stu-id="0b554-162">See also</span></span>

- [<span data-ttu-id="0b554-163">Логические (побитовые) операторы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b554-163">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="0b554-164">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0b554-164">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="0b554-165">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="0b554-165">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="0b554-166">Логические и побитовые операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0b554-166">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
