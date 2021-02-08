---
description: Дополнительные сведения о операторе and (Visual Basic)
title: Оператор And
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: 238ef0b2f14f2014da6e65684bfac183e03d963e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774282"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="b35ee-103">Оператор And (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b35ee-103">And Operator (Visual Basic)</span></span>

<span data-ttu-id="b35ee-104">Выполняет логическое умножение двух `Boolean` выражений или побитовое умножение двух числовых выражений.</span><span class="sxs-lookup"><span data-stu-id="b35ee-104">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b35ee-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b35ee-105">Syntax</span></span>  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="b35ee-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="b35ee-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="b35ee-107">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="b35ee-107">Required.</span></span> <span data-ttu-id="b35ee-108">Произвольное выражение типа `Boolean` или числового типа.</span><span class="sxs-lookup"><span data-stu-id="b35ee-108">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="b35ee-109">Для логического сравнения `result` — это логическое умножение двух `Boolean` значений.</span><span class="sxs-lookup"><span data-stu-id="b35ee-109">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="b35ee-110">Для битовых операций `result` — это числовое значение, представляющее побитовое умножение двух числовых битов.</span><span class="sxs-lookup"><span data-stu-id="b35ee-110">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="b35ee-111">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="b35ee-111">Required.</span></span> <span data-ttu-id="b35ee-112">Произвольное выражение типа `Boolean` или числового типа.</span><span class="sxs-lookup"><span data-stu-id="b35ee-112">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="b35ee-113">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="b35ee-113">Required.</span></span> <span data-ttu-id="b35ee-114">Произвольное выражение типа `Boolean` или числового типа.</span><span class="sxs-lookup"><span data-stu-id="b35ee-114">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b35ee-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="b35ee-115">Remarks</span></span>  

 <span data-ttu-id="b35ee-116">Для логического сравнения `result` параметр имеет значение, `True` только если оба значения `expression1` и имеют значение `expression2` `True` .</span><span class="sxs-lookup"><span data-stu-id="b35ee-116">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="b35ee-117">В следующей таблице показано, как `result` определяется.</span><span class="sxs-lookup"><span data-stu-id="b35ee-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="b35ee-118">Если `expression1` имеет значение </span><span class="sxs-lookup"><span data-stu-id="b35ee-118">If `expression1` is</span></span>|<span data-ttu-id="b35ee-119">И `expression2` является</span><span class="sxs-lookup"><span data-stu-id="b35ee-119">And `expression2` is</span></span>|<span data-ttu-id="b35ee-120">Значение `result` равно</span><span class="sxs-lookup"><span data-stu-id="b35ee-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="b35ee-121">При логическом сравнении `And` оператор всегда вычисляет оба выражения, которые могут включать вызовы процедур.</span><span class="sxs-lookup"><span data-stu-id="b35ee-121">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="b35ee-122">[Оператор AndAlso](andalso-operator.md) выполняет *сокращенное вычисление*, означающее, что если `expression1` имеет значение `False` , то `expression2` не вычисляется.</span><span class="sxs-lookup"><span data-stu-id="b35ee-122">The [AndAlso Operator](andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="b35ee-123">При применении к числовым значениям `And` оператор выполняет побитовое сравнение одинаково позиционированных битов в двух числовых выражениях и устанавливает соответствующий бит в `result` соответствии со следующей таблицей.</span><span class="sxs-lookup"><span data-stu-id="b35ee-123">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="b35ee-124">Если бит в `expression1` имеет значение</span><span class="sxs-lookup"><span data-stu-id="b35ee-124">If bit in `expression1` is</span></span>|<span data-ttu-id="b35ee-125">И bit в `expression2` имеет</span><span class="sxs-lookup"><span data-stu-id="b35ee-125">And bit in `expression2` is</span></span>|<span data-ttu-id="b35ee-126">Бит в `result` имеет значение</span><span class="sxs-lookup"><span data-stu-id="b35ee-126">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="b35ee-127">1</span><span class="sxs-lookup"><span data-stu-id="b35ee-127">1</span></span>|<span data-ttu-id="b35ee-128">1</span><span class="sxs-lookup"><span data-stu-id="b35ee-128">1</span></span>|<span data-ttu-id="b35ee-129">1</span><span class="sxs-lookup"><span data-stu-id="b35ee-129">1</span></span>|  
|<span data-ttu-id="b35ee-130">1</span><span class="sxs-lookup"><span data-stu-id="b35ee-130">1</span></span>|<span data-ttu-id="b35ee-131">0</span><span class="sxs-lookup"><span data-stu-id="b35ee-131">0</span></span>|<span data-ttu-id="b35ee-132">0</span><span class="sxs-lookup"><span data-stu-id="b35ee-132">0</span></span>|  
|<span data-ttu-id="b35ee-133">0</span><span class="sxs-lookup"><span data-stu-id="b35ee-133">0</span></span>|<span data-ttu-id="b35ee-134">1</span><span class="sxs-lookup"><span data-stu-id="b35ee-134">1</span></span>|<span data-ttu-id="b35ee-135">0</span><span class="sxs-lookup"><span data-stu-id="b35ee-135">0</span></span>|  
|<span data-ttu-id="b35ee-136">0</span><span class="sxs-lookup"><span data-stu-id="b35ee-136">0</span></span>|<span data-ttu-id="b35ee-137">0</span><span class="sxs-lookup"><span data-stu-id="b35ee-137">0</span></span>|<span data-ttu-id="b35ee-138">0</span><span class="sxs-lookup"><span data-stu-id="b35ee-138">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b35ee-139">Так как логические и побитовые операторы имеют более низкий приоритет, чем другие арифметические и реляционные операторы, все битовые операции должны быть заключены в круглые скобки для обеспечения точных результатов.</span><span class="sxs-lookup"><span data-stu-id="b35ee-139">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="b35ee-140">Типы данных</span><span class="sxs-lookup"><span data-stu-id="b35ee-140">Data Types</span></span>  

 <span data-ttu-id="b35ee-141">Если операнды состоят из одного `Boolean` выражения и одного числового выражения, Visual Basic преобразует `Boolean` выражение в числовое значение (– 1 для `True` и 0 для `False` ) и выполняет побитовую операцию.</span><span class="sxs-lookup"><span data-stu-id="b35ee-141">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="b35ee-142">Для логического сравнения тип данных результата — `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="b35ee-142">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="b35ee-143">Для побитового сравнения тип данных результата является числовым типом, подходящим для типов данных `expression1` и `expression2` .</span><span class="sxs-lookup"><span data-stu-id="b35ee-143">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="b35ee-144">См. таблицу "реляционные и побитовые сравнения" в разделе [типы данных результатов операторов](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="b35ee-144">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b35ee-145">`And`Оператор можно *перегрузить*, что означает, что класс или структура может переопределить свое поведение, когда операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="b35ee-145">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b35ee-146">Если код использует этот оператор для такого класса или структуры, убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="b35ee-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b35ee-147">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b35ee-147">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b35ee-148">Пример</span><span class="sxs-lookup"><span data-stu-id="b35ee-148">Example</span></span>  

 <span data-ttu-id="b35ee-149">В следующем примере оператор используется `And` для выполнения логического умножения двух выражений.</span><span class="sxs-lookup"><span data-stu-id="b35ee-149">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="b35ee-150">Результатом является `Boolean` значение, которое показывает, равны ли оба выражения `True` .</span><span class="sxs-lookup"><span data-stu-id="b35ee-150">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="b35ee-151">В предыдущем примере создаются результаты `True` и `False` соответственно.</span><span class="sxs-lookup"><span data-stu-id="b35ee-151">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b35ee-152">Пример</span><span class="sxs-lookup"><span data-stu-id="b35ee-152">Example</span></span>  

 <span data-ttu-id="b35ee-153">В следующем примере оператор используется `And` для выполнения логического умножения отдельных битов двух числовых выражений.</span><span class="sxs-lookup"><span data-stu-id="b35ee-153">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="b35ee-154">Бит в результирующем шаблоне задается, если для соответствующих битов в операндах задано значение 1.</span><span class="sxs-lookup"><span data-stu-id="b35ee-154">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="b35ee-155">В предыдущем примере выдается результат 8, 2 и 0 соответственно.</span><span class="sxs-lookup"><span data-stu-id="b35ee-155">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b35ee-156">См. также</span><span class="sxs-lookup"><span data-stu-id="b35ee-156">See also</span></span>

- [<span data-ttu-id="b35ee-157">Логические (побитовые) операторы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b35ee-157">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="b35ee-158">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b35ee-158">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="b35ee-159">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="b35ee-159">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="b35ee-160">Оператор AndAlso</span><span class="sxs-lookup"><span data-stu-id="b35ee-160">AndAlso Operator</span></span>](andalso-operator.md)
- [<span data-ttu-id="b35ee-161">Логические и побитовые операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b35ee-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
