---
description: Дополнительные сведения об операторе:/= (Visual Basic)
title: Оператор /=
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: 3020372be18f554df18fa6dac539ab9d0b2f725e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666034"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="a00bf-103">Оператор /= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a00bf-103">/= Operator (Visual Basic)</span></span>

<span data-ttu-id="a00bf-104">Делит значение переменной или свойства на значение выражения и присваивает результат с плавающей запятой переменной или свойству.</span><span class="sxs-lookup"><span data-stu-id="a00bf-104">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a00bf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a00bf-105">Syntax</span></span>  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="a00bf-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="a00bf-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="a00bf-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="a00bf-107">Required.</span></span> <span data-ttu-id="a00bf-108">Любая числовая переменная или свойство.</span><span class="sxs-lookup"><span data-stu-id="a00bf-108">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="a00bf-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="a00bf-109">Required.</span></span> <span data-ttu-id="a00bf-110">Произвольное числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="a00bf-110">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a00bf-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="a00bf-111">Remarks</span></span>  

 <span data-ttu-id="a00bf-112">Элемент в левой части `/=` оператора может быть простой скалярной переменной, свойством или элементом массива.</span><span class="sxs-lookup"><span data-stu-id="a00bf-112">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="a00bf-113">Переменная или свойство не может быть [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="a00bf-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="a00bf-114">`/=`Оператор сначала делит значение переменной или свойства (в левой части оператора) на значение выражения (в правой части оператора). в противном случае.</span><span class="sxs-lookup"><span data-stu-id="a00bf-114">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="a00bf-115">Затем оператор присваивает результат операции с плавающей запятой переменной или свойству.</span><span class="sxs-lookup"><span data-stu-id="a00bf-115">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="a00bf-116">Эта инструкция присваивает `Double` значение переменной или свойству слева.</span><span class="sxs-lookup"><span data-stu-id="a00bf-116">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="a00bf-117">Если `Option Strict` имеет значение `On` , `variableorproperty` должно быть `Double` .</span><span class="sxs-lookup"><span data-stu-id="a00bf-117">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="a00bf-118">Если `Option Strict` параметр имеет значение `Off` , Visual Basic выполняет неявное преобразование и присваивает результирующее значение `variableorproperty` с возможной ошибкой во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="a00bf-118">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="a00bf-119">Дополнительные сведения см. в разделе [расширяющие и сужающие преобразования](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) и [Option](../statements/option-strict-statement.md)parallelism.</span><span class="sxs-lookup"><span data-stu-id="a00bf-119">For more information, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a00bf-120">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="a00bf-120">Overloading</span></span>  

 <span data-ttu-id="a00bf-121">[Оператор/(Visual Basic)](floating-point-division-operator.md) может быть *перегружен*, что означает, что класс или структура может переопределить свое поведение, когда операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="a00bf-121">The [/ Operator (Visual Basic)](floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a00bf-122">Перегрузка `/` оператора влияет на поведение `/=` оператора.</span><span class="sxs-lookup"><span data-stu-id="a00bf-122">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="a00bf-123">Если ваш код использует `/=` класс или структуру, перегрузки `/` , убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="a00bf-123">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a00bf-124">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a00bf-124">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a00bf-125">Пример</span><span class="sxs-lookup"><span data-stu-id="a00bf-125">Example</span></span>  

 <span data-ttu-id="a00bf-126">В следующем примере оператор используется `/=` для разделения одной `Integer` переменной на вторую и присваивания значения частного для первой переменной.</span><span class="sxs-lookup"><span data-stu-id="a00bf-126">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="a00bf-127">См. также</span><span class="sxs-lookup"><span data-stu-id="a00bf-127">See also</span></span>

- [<span data-ttu-id="a00bf-128">Оператор/(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a00bf-128">/ Operator (Visual Basic)</span></span>](floating-point-division-operator.md)
- [<span data-ttu-id="a00bf-129">\\Оператор =</span><span class="sxs-lookup"><span data-stu-id="a00bf-129">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="a00bf-130">Операторы присваивания</span><span class="sxs-lookup"><span data-stu-id="a00bf-130">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="a00bf-131">Арифметические операторы</span><span class="sxs-lookup"><span data-stu-id="a00bf-131">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="a00bf-132">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a00bf-132">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="a00bf-133">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="a00bf-133">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="a00bf-134">Операторы</span><span class="sxs-lookup"><span data-stu-id="a00bf-134">Statements</span></span>](../../programming-guide/language-features/statements.md)
