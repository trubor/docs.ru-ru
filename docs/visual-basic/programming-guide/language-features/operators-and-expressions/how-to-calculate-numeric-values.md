---
description: Дополнительные сведения см. в статье как вычислить числовые значения (Visual Basic).
title: Практическое руководство. Вычисление числовых значений
ms.date: 07/20/2015
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
ms.openlocfilehash: 35acd7b9b1732514a8fe4399b6a815dce62b2468
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100435594"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="7a13e-103">Практическое руководство. Вычисление числовых значений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a13e-103">How to: Calculate Numeric Values (Visual Basic)</span></span>

<span data-ttu-id="7a13e-104">Числовые значения можно вычислить с помощью числовых выражений.</span><span class="sxs-lookup"><span data-stu-id="7a13e-104">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="7a13e-105">*Числовое выражение* представляет собой выражение, которое содержит литералы, константы и переменные, представляющие числовые значения, и операторы, действующие на эти значения.</span><span class="sxs-lookup"><span data-stu-id="7a13e-105">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="7a13e-106">Вычисление числовых значений</span><span class="sxs-lookup"><span data-stu-id="7a13e-106">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="7a13e-107">Вычисление числового значения</span><span class="sxs-lookup"><span data-stu-id="7a13e-107">To calculate a numeric value</span></span>  
  
- <span data-ttu-id="7a13e-108">Объедините один или несколько числовых литералов, констант и переменных в числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="7a13e-108">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="7a13e-109">В следующем примере показаны некоторые допустимые числовые выражения.</span><span class="sxs-lookup"><span data-stu-id="7a13e-109">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="7a13e-110">Первые три строки показывают литерал, константу и переменную.</span><span class="sxs-lookup"><span data-stu-id="7a13e-110">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="7a13e-111">Каждый из них формирует допустимое числовое выражение самим собой.</span><span class="sxs-lookup"><span data-stu-id="7a13e-111">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="7a13e-112">В последней строке показано сочетание переменной с двумя литералами.</span><span class="sxs-lookup"><span data-stu-id="7a13e-112">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="7a13e-113">Обратите внимание, что числовое выражение не формирует полную инструкцию Visual Basic сам по себе.</span><span class="sxs-lookup"><span data-stu-id="7a13e-113">Note that a numeric expression does not form a complete Visual Basic statement by itself.</span></span> <span data-ttu-id="7a13e-114">Выражение необходимо использовать как часть полной инструкции.</span><span class="sxs-lookup"><span data-stu-id="7a13e-114">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="7a13e-115">Сохранение числового значения</span><span class="sxs-lookup"><span data-stu-id="7a13e-115">To store a numeric value</span></span>  
  
- <span data-ttu-id="7a13e-116">Оператор присваивания можно использовать для назначения переменной значения, представленного числовым выражением, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="7a13e-116">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     <span data-ttu-id="7a13e-117">В предыдущем примере значение выражения в правой части оператора равенства ( `=` ) присваивается переменной `j` в левой части оператора, поэтому `j` результатом вычисления будет 276.</span><span class="sxs-lookup"><span data-stu-id="7a13e-117">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="7a13e-118">Дополнительные сведения см. в разделе [Инструкции](../../../language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="7a13e-118">For more information, see [Statements](../../../language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="7a13e-119">Несколько операторов</span><span class="sxs-lookup"><span data-stu-id="7a13e-119">Multiple Operators</span></span>  

 <span data-ttu-id="7a13e-120">Если числовое выражение содержит более одного оператора, порядок их вычисления определяется правилами приоритета операторов.</span><span class="sxs-lookup"><span data-stu-id="7a13e-120">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="7a13e-121">Чтобы переопределить правила приоритета операторов, заключите выражения в круглые скобки, как в приведенном выше примере. выражения, заключенные в кавычки, оцениваются первыми.</span><span class="sxs-lookup"><span data-stu-id="7a13e-121">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="7a13e-122">Переопределение приоритета обычного оператора</span><span class="sxs-lookup"><span data-stu-id="7a13e-122">To override normal operator precedence</span></span>  
  
- <span data-ttu-id="7a13e-123">Используйте круглые скобки, чтобы заключать операции, которые необходимо выполнить первыми.</span><span class="sxs-lookup"><span data-stu-id="7a13e-123">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="7a13e-124">В следующем примере показаны два разных результата с одинаковыми операндами и операторами.</span><span class="sxs-lookup"><span data-stu-id="7a13e-124">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     <span data-ttu-id="7a13e-125">В предыдущем примере вычисление для `j` выполняет оператор сложения ( `+` ) сначала, так как круглые скобки `(67 + i)` обопределяют нормальный приоритет, а присваиваемое значение `j` — 276 (4 раза 69).</span><span class="sxs-lookup"><span data-stu-id="7a13e-125">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="7a13e-126">Вычисление для `k` выполняет операторы в нормальном порядке ( `*` до `+` ), а присваиваемое ему значение `k` равно 270 (268 плюс 2).</span><span class="sxs-lookup"><span data-stu-id="7a13e-126">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="7a13e-127">Дополнительные сведения см. [в разделе приоритет операторов в Visual Basic](../../../language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="7a13e-127">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a13e-128">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7a13e-128">See also</span></span>

- [<span data-ttu-id="7a13e-129">Операторы и выражения</span><span class="sxs-lookup"><span data-stu-id="7a13e-129">Operators and Expressions</span></span>](index.md)
- [<span data-ttu-id="7a13e-130">Сравнения значений</span><span class="sxs-lookup"><span data-stu-id="7a13e-130">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="7a13e-131">Операторы</span><span class="sxs-lookup"><span data-stu-id="7a13e-131">Statements</span></span>](../../../language-reference/statements/index.md)
- [<span data-ttu-id="7a13e-132">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a13e-132">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="7a13e-133">Арифметические операторы</span><span class="sxs-lookup"><span data-stu-id="7a13e-133">Arithmetic Operators</span></span>](../../../language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="7a13e-134">Эффективное сочетание операторов</span><span class="sxs-lookup"><span data-stu-id="7a13e-134">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
