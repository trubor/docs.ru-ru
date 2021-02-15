---
description: 'Дополнительные сведения: эффективная комбинация операторов (Visual Basic)'
title: Эффективное сочетание операторов
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: a4d2d0c1caeea95dd8d34b2033a398d26bcf63ef
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476271"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="52f5e-103">Эффективное сочетание операторов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52f5e-103">Efficient Combination of Operators (Visual Basic)</span></span>

<span data-ttu-id="52f5e-104">Сложные выражения могут содержать множество различных операторов.</span><span class="sxs-lookup"><span data-stu-id="52f5e-104">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="52f5e-105">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="52f5e-105">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="52f5e-106">Создание сложных выражений, например, в предыдущем примере, требует тщательного понимания правил приоритета операторов.</span><span class="sxs-lookup"><span data-stu-id="52f5e-106">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="52f5e-107">Дополнительные сведения см. [в разделе приоритет операторов в Visual Basic](../../../language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="52f5e-107">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="52f5e-108">Выражения в скобках</span><span class="sxs-lookup"><span data-stu-id="52f5e-108">Parenthetical Expressions</span></span>  

 <span data-ttu-id="52f5e-109">Часто требуется, чтобы операции продвигается в порядке, отличном от того, который определяется приоритетом операторов.</span><span class="sxs-lookup"><span data-stu-id="52f5e-109">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="52f5e-110">Рассмотрим следующий пример.</span><span class="sxs-lookup"><span data-stu-id="52f5e-110">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="52f5e-111">Предыдущий пример умножается на `z` `y` , а затем добавляет результат в `4` .</span><span class="sxs-lookup"><span data-stu-id="52f5e-111">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="52f5e-112">Но если вы хотите добавить `y` и `4` перед умножением результата на `z` , можно переопределить нормальный приоритет операторов с помощью круглых скобок.</span><span class="sxs-lookup"><span data-stu-id="52f5e-112">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="52f5e-113">Заключив выражение в круглые скобки, вы принудительно выдаете выражение первым, независимо от приоритета операторов.</span><span class="sxs-lookup"><span data-stu-id="52f5e-113">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="52f5e-114">Чтобы выполнить предыдущий пример для первого добавления, можно переписать его, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="52f5e-114">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="52f5e-115">В предыдущем примере добавляются `y` `4` функции и, а затем вычисляется сумма по `z` .</span><span class="sxs-lookup"><span data-stu-id="52f5e-115">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="52f5e-116">Вложенные выражения в скобках</span><span class="sxs-lookup"><span data-stu-id="52f5e-116">Nested Parenthetical Expressions</span></span>  

 <span data-ttu-id="52f5e-117">Можно вкладывать выражения на нескольких уровнях круглых скобок для более детального переопределения приоритета.</span><span class="sxs-lookup"><span data-stu-id="52f5e-117">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="52f5e-118">Выражения, наиболее глубоко вложенные в круглые скобки, сначала оцениваются, за которыми следуют более глубокий уровень вложенности, и так далее, и, наконец, выражения за пределами круглых скобок.</span><span class="sxs-lookup"><span data-stu-id="52f5e-118">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="52f5e-119">Это показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="52f5e-119">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="52f5e-120">В предыдущем примере `z + 2` вычисляется первым, а затем другими выражениями в скобках.</span><span class="sxs-lookup"><span data-stu-id="52f5e-120">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="52f5e-121">Возведение в степень, которое обычно имеет более высокий приоритет, чем сложение или умножение, в этом примере вычисляется последним, так как другие выражения заключаются в круглые скобки.</span><span class="sxs-lookup"><span data-stu-id="52f5e-121">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52f5e-122">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="52f5e-122">See also</span></span>

- [<span data-ttu-id="52f5e-123">Арифметические операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52f5e-123">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="52f5e-124">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52f5e-124">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="52f5e-125">Логические и побитовые операторы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52f5e-125">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
- [<span data-ttu-id="52f5e-126">Логические (побитовые) операторы (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52f5e-126">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="52f5e-127">Логические выражения</span><span class="sxs-lookup"><span data-stu-id="52f5e-127">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="52f5e-128">Сравнения значений</span><span class="sxs-lookup"><span data-stu-id="52f5e-128">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="52f5e-129">Практическое руководство. Вычисление числовых значений</span><span class="sxs-lookup"><span data-stu-id="52f5e-129">How to: Calculate Numeric Values</span></span>](how-to-calculate-numeric-values.md)
- [<span data-ttu-id="52f5e-130">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52f5e-130">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
