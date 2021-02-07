---
description: 'Дополнительные сведения: оператор NOT (Visual Basic)'
title: Оператор Not
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 91f3525b52d6f38081b8e5ba208c193f714a4045
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665358"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="2360c-103">Оператор Not (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2360c-103">Not Operator (Visual Basic)</span></span>

<span data-ttu-id="2360c-104">Выполняет логическое отрицание `Boolean` выражения или побитовое отрицание в числовом выражении.</span><span class="sxs-lookup"><span data-stu-id="2360c-104">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2360c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2360c-105">Syntax</span></span>  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="2360c-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="2360c-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="2360c-107">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="2360c-107">Required.</span></span> <span data-ttu-id="2360c-108">Произвольное выражение типа `Boolean` или числового типа.</span><span class="sxs-lookup"><span data-stu-id="2360c-108">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="2360c-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="2360c-109">Required.</span></span> <span data-ttu-id="2360c-110">Произвольное выражение типа `Boolean` или числового типа.</span><span class="sxs-lookup"><span data-stu-id="2360c-110">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2360c-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="2360c-111">Remarks</span></span>  

 <span data-ttu-id="2360c-112">Для `Boolean` выражений в следующей таблице показано, как `result` определяется.</span><span class="sxs-lookup"><span data-stu-id="2360c-112">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="2360c-113">Если `expression` имеет значение </span><span class="sxs-lookup"><span data-stu-id="2360c-113">If `expression` is</span></span>|<span data-ttu-id="2360c-114">Значение `result` равно</span><span class="sxs-lookup"><span data-stu-id="2360c-114">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="2360c-115">Для числовых выражений `Not` оператор инвертирует битовые значения любого числового выражения и устанавливает соответствующий бит в `result` соответствии со следующей таблицей.</span><span class="sxs-lookup"><span data-stu-id="2360c-115">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="2360c-116">Если бит в `expression` имеет значение</span><span class="sxs-lookup"><span data-stu-id="2360c-116">If bit in `expression` is</span></span>|<span data-ttu-id="2360c-117">Бит в `result` имеет значение</span><span class="sxs-lookup"><span data-stu-id="2360c-117">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="2360c-118">1</span><span class="sxs-lookup"><span data-stu-id="2360c-118">1</span></span>|<span data-ttu-id="2360c-119">0</span><span class="sxs-lookup"><span data-stu-id="2360c-119">0</span></span>|  
|<span data-ttu-id="2360c-120">0</span><span class="sxs-lookup"><span data-stu-id="2360c-120">0</span></span>|<span data-ttu-id="2360c-121">1</span><span class="sxs-lookup"><span data-stu-id="2360c-121">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="2360c-122">Так как логические и побитовые операторы имеют более низкий приоритет, чем другие арифметические и реляционные операторы, все битовые операции должны быть заключены в круглые скобки, чтобы обеспечить точное выполнение.</span><span class="sxs-lookup"><span data-stu-id="2360c-122">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="2360c-123">Типы данных</span><span class="sxs-lookup"><span data-stu-id="2360c-123">Data Types</span></span>  

 <span data-ttu-id="2360c-124">Для логического отрицания тип данных результата — `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="2360c-124">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="2360c-125">Для побитового отрицания тип данных результата такой же, как и у `expression` .</span><span class="sxs-lookup"><span data-stu-id="2360c-125">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="2360c-126">Однако если выражение имеет значение `Decimal` , результатом будет `Long` .</span><span class="sxs-lookup"><span data-stu-id="2360c-126">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="2360c-127">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="2360c-127">Overloading</span></span>  

 <span data-ttu-id="2360c-128">`Not`Оператор можно *перегрузить*, что означает, что класс или структура может переопределить свое поведение, если его операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="2360c-128">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="2360c-129">Если код использует этот оператор для такого класса или структуры, убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="2360c-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="2360c-130">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2360c-130">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2360c-131">Пример</span><span class="sxs-lookup"><span data-stu-id="2360c-131">Example</span></span>  

 <span data-ttu-id="2360c-132">В следующем примере оператор используется `Not` для выполнения логического отрицания в `Boolean` выражении.</span><span class="sxs-lookup"><span data-stu-id="2360c-132">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="2360c-133">Результатом является `Boolean` значение, представляющее обратную величину значения выражения.</span><span class="sxs-lookup"><span data-stu-id="2360c-133">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="2360c-134">В предыдущем примере создаются результаты `False` и `True` соответственно.</span><span class="sxs-lookup"><span data-stu-id="2360c-134">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2360c-135">Пример</span><span class="sxs-lookup"><span data-stu-id="2360c-135">Example</span></span>  

 <span data-ttu-id="2360c-136">В следующем примере оператор используется `Not` для выполнения логического отрицания отдельных битов числового выражения.</span><span class="sxs-lookup"><span data-stu-id="2360c-136">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="2360c-137">Бит в результирующем шаблоне имеет значение, противоположное соответствующему биту в шаблоне операнда, включая бит знака.</span><span class="sxs-lookup"><span data-stu-id="2360c-137">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="2360c-138">В предыдущем примере создаются результаты – 11, – 9 и – 7 соответственно.</span><span class="sxs-lookup"><span data-stu-id="2360c-138">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2360c-139">См. также</span><span class="sxs-lookup"><span data-stu-id="2360c-139">See also</span></span>

- [<span data-ttu-id="2360c-140">Логические (побитовые) операторы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2360c-140">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="2360c-141">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2360c-141">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="2360c-142">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="2360c-142">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="2360c-143">Логические и побитовые операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2360c-143">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
