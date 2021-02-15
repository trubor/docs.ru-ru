---
description: Дополнительные сведения об операторах и выражениях в Visual Basic
title: Операторы и выражения
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: 526051e16da29cd139abf587e1393ad331fdcdaa
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471400"
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="6940a-103">Операторы и выражения в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6940a-103">Operators and Expressions in Visual Basic</span></span>

<span data-ttu-id="6940a-104">*Оператор* представляет собой элемент кода, который выполняет операцию с одним элементом кода или несколькими, содержащими значения.</span><span class="sxs-lookup"><span data-stu-id="6940a-104">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="6940a-105">К элементам значений относятся переменные, константы, литералы, свойства, возвращаемые значения из процедур `Function` и `Operator`, а также выражения.</span><span class="sxs-lookup"><span data-stu-id="6940a-105">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="6940a-106">*Выражение* представляет собой набор элементов значений в сочетании с операторами, результатом которого является новое значение.</span><span class="sxs-lookup"><span data-stu-id="6940a-106">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="6940a-107">Операторы работают с элементами значений, выполняя вычисления, сравнения и другие операции.</span><span class="sxs-lookup"><span data-stu-id="6940a-107">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="6940a-108">Типы операторов</span><span class="sxs-lookup"><span data-stu-id="6940a-108">Types of Operators</span></span>  

 <span data-ttu-id="6940a-109">Visual Basic предоставляет следующие типы операторов:</span><span class="sxs-lookup"><span data-stu-id="6940a-109">Visual Basic provides the following types of operators:</span></span>  
  
- <span data-ttu-id="6940a-110">[Арифметические операторы](arithmetic-operators.md) выполняют обычные вычисления с числовыми значениями, включая сдвиг их битовых шаблонов.</span><span class="sxs-lookup"><span data-stu-id="6940a-110">[Arithmetic Operators](arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
- <span data-ttu-id="6940a-111">[Операторы сравнения](comparison-operators.md) сравнивают два выражения и возвращают значение `Boolean`, соответствующее результату сравнения.</span><span class="sxs-lookup"><span data-stu-id="6940a-111">[Comparison Operators](comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
- <span data-ttu-id="6940a-112">[Операторы объединения](concatenation-operators.md) соединяют несколько строк в одну.</span><span class="sxs-lookup"><span data-stu-id="6940a-112">[Concatenation Operators](concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
- <span data-ttu-id="6940a-113">[Логические и побитовые операторы в Visual Basic](logical-and-bitwise-operators.md) объединяют `Boolean` или числовые значения и возвращают результат того же типа данных, что и значения.</span><span class="sxs-lookup"><span data-stu-id="6940a-113">[Logical and Bitwise Operators in Visual Basic](logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="6940a-114">Элементы значений, объединенные с оператором, называются *операндами* этого оператора.</span><span class="sxs-lookup"><span data-stu-id="6940a-114">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="6940a-115">Операторы, объединенные с элементами значений, формируют выражения. Исключением является оператор присваивания, который образует *инструкцию*.</span><span class="sxs-lookup"><span data-stu-id="6940a-115">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="6940a-116">Дополнительные сведения см. в разделе [Инструкции](../statements.md).</span><span class="sxs-lookup"><span data-stu-id="6940a-116">For more information, see [Statements](../statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="6940a-117">Вычисление выражений</span><span class="sxs-lookup"><span data-stu-id="6940a-117">Evaluation of Expressions</span></span>  

 <span data-ttu-id="6940a-118">Конечный результат выражения представляет собой значение, которое обычно имеет знакомый тип данных, например `Boolean`, `String` или числовой тип.</span><span class="sxs-lookup"><span data-stu-id="6940a-118">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="6940a-119">Ниже приведены примеры выражений.</span><span class="sxs-lookup"><span data-stu-id="6940a-119">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="6940a-120">Несколько операторов могут выполнять действия в одном выражении или инструкции, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="6940a-120">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 <span data-ttu-id="6940a-121">В предыдущем примере Visual Basic выполняет операции в выражении с правой стороны оператора присваивания ( `=` ), а затем присваивает результирующее значение переменной `x` слева.</span><span class="sxs-lookup"><span data-stu-id="6940a-121">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="6940a-122">С практической точки зрения в выражение можно объединять сколько угодно операторов, но следует учитывать [приоритет операторов в Visual Basic](../../../language-reference/operators/operator-precedence.md) для получения желаемых результатов.</span><span class="sxs-lookup"><span data-stu-id="6940a-122">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  

## <a name="see-also"></a><span data-ttu-id="6940a-123">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6940a-123">See also</span></span>

- [<span data-ttu-id="6940a-124">Операторы</span><span class="sxs-lookup"><span data-stu-id="6940a-124">Operators</span></span>](../../../language-reference/operators/index.md)
- [<span data-ttu-id="6940a-125">Эффективное сочетание операторов</span><span class="sxs-lookup"><span data-stu-id="6940a-125">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
- [<span data-ttu-id="6940a-126">Операторы</span><span class="sxs-lookup"><span data-stu-id="6940a-126">Statements</span></span>](../../../language-reference/statements/index.md)
