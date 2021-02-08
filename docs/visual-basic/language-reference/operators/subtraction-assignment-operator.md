---
description: Дополнительные сведения о операторе:-= (Visual Basic)
title: Оператор -=
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: 55574fa56d0ebe02fa5aef1a2711dfb3e5161a9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795278"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="05783-103">Оператор -= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05783-103">-= Operator (Visual Basic)</span></span>

<span data-ttu-id="05783-104">Вычитает значение выражения из значения переменной или свойства и присваивает результат переменной или свойству.</span><span class="sxs-lookup"><span data-stu-id="05783-104">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05783-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="05783-105">Syntax</span></span>  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="05783-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="05783-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="05783-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="05783-107">Required.</span></span> <span data-ttu-id="05783-108">Любая числовая переменная или свойство.</span><span class="sxs-lookup"><span data-stu-id="05783-108">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="05783-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="05783-109">Required.</span></span> <span data-ttu-id="05783-110">Произвольное числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="05783-110">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05783-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="05783-111">Remarks</span></span>  

 <span data-ttu-id="05783-112">Элемент в левой части `-=` оператора может быть простой скалярной переменной, свойством или элементом массива.</span><span class="sxs-lookup"><span data-stu-id="05783-112">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="05783-113">Переменная или свойство не может быть [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="05783-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="05783-114">`-=`Оператор вначале вычитает значение выражения (в правой части оператора) из значения переменной или свойства (в левой части оператора) (слева).</span><span class="sxs-lookup"><span data-stu-id="05783-114">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="05783-115">Затем оператор присваивает результат этой операции переменной или свойству.</span><span class="sxs-lookup"><span data-stu-id="05783-115">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="05783-116">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="05783-116">Overloading</span></span>  

 <span data-ttu-id="05783-117">[Оператор-operator (Visual Basic)](subtraction-operator.md) может быть *перегружен*, что означает, что класс или структура может переопределить свое поведение, если операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="05783-117">The [- Operator (Visual Basic)](subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="05783-118">Перегрузка `-` оператора влияет на поведение `-=` оператора.</span><span class="sxs-lookup"><span data-stu-id="05783-118">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="05783-119">Если ваш код использует `-=` класс или структуру, перегрузки `-` , убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="05783-119">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="05783-120">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="05783-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05783-121">Пример</span><span class="sxs-lookup"><span data-stu-id="05783-121">Example</span></span>  

 <span data-ttu-id="05783-122">В следующем примере оператор используется `-=` для вычитания одной `Integer` переменной из другой и присваивает результат второй переменной.</span><span class="sxs-lookup"><span data-stu-id="05783-122">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="05783-123">См. также</span><span class="sxs-lookup"><span data-stu-id="05783-123">See also</span></span>

- [<span data-ttu-id="05783-124">Оператор - (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05783-124">- Operator (Visual Basic)</span></span>](subtraction-operator.md)
- [<span data-ttu-id="05783-125">Операторы присваивания</span><span class="sxs-lookup"><span data-stu-id="05783-125">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="05783-126">Арифметические операторы</span><span class="sxs-lookup"><span data-stu-id="05783-126">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="05783-127">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05783-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="05783-128">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="05783-128">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="05783-129">Операторы</span><span class="sxs-lookup"><span data-stu-id="05783-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
