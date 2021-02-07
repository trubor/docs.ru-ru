---
description: 'Дополнительные сведения о операторе: * = (Visual Basic)'
title: Оператор *=
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: d5a88dc71a05c6375a09fe3f4b55eff704c13910
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665423"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="4aeae-103">Оператор \*= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4aeae-103">\*= Operator (Visual Basic)</span></span>

<span data-ttu-id="4aeae-104">Умножает значение переменной или свойства на значение выражения и присваивает результат переменной или свойству.</span><span class="sxs-lookup"><span data-stu-id="4aeae-104">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aeae-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4aeae-105">Syntax</span></span>  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="4aeae-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="4aeae-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="4aeae-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="4aeae-107">Required.</span></span> <span data-ttu-id="4aeae-108">Любая числовая переменная или свойство.</span><span class="sxs-lookup"><span data-stu-id="4aeae-108">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="4aeae-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="4aeae-109">Required.</span></span> <span data-ttu-id="4aeae-110">Произвольное числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="4aeae-110">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4aeae-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="4aeae-111">Remarks</span></span>  

 <span data-ttu-id="4aeae-112">Элемент в левой части `*=` оператора может быть простой скалярной переменной, свойством или элементом массива.</span><span class="sxs-lookup"><span data-stu-id="4aeae-112">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="4aeae-113">Переменная или свойство не может быть [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="4aeae-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="4aeae-114">`*=`Оператор вначале умножает значение выражения (в правой части оператора) на значение переменной или свойства (в левой части оператора) (слева).</span><span class="sxs-lookup"><span data-stu-id="4aeae-114">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="4aeae-115">Затем оператор присваивает результат этой операции переменной или свойству.</span><span class="sxs-lookup"><span data-stu-id="4aeae-115">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="4aeae-116">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="4aeae-116">Overloading</span></span>  

 <span data-ttu-id="4aeae-117">[Оператор \*](multiplication-operator.md) может быть *перегружен*, что означает, что класс или структура может переопределить свое поведение, если операнд имеет тип этого класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="4aeae-117">The [\* Operator](multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="4aeae-118">Перегрузка `*` оператора влияет на поведение `*=` оператора.</span><span class="sxs-lookup"><span data-stu-id="4aeae-118">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="4aeae-119">Если ваш код использует `*=` класс или структуру, перегрузки `*` , убедитесь, что вы понимаете его переопределенное поведение.</span><span class="sxs-lookup"><span data-stu-id="4aeae-119">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="4aeae-120">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4aeae-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4aeae-121">Пример</span><span class="sxs-lookup"><span data-stu-id="4aeae-121">Example</span></span>  

 <span data-ttu-id="4aeae-122">В следующем примере оператор используется `*=` для умножения одной `Integer` переменной на вторую и присваивания результата первой переменной.</span><span class="sxs-lookup"><span data-stu-id="4aeae-122">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="4aeae-123">См. также</span><span class="sxs-lookup"><span data-stu-id="4aeae-123">See also</span></span>

- [<span data-ttu-id="4aeae-124">\* Оператор</span><span class="sxs-lookup"><span data-stu-id="4aeae-124">\* Operator</span></span>](multiplication-operator.md)
- [<span data-ttu-id="4aeae-125">Операторы присваивания</span><span class="sxs-lookup"><span data-stu-id="4aeae-125">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="4aeae-126">Арифметические операторы</span><span class="sxs-lookup"><span data-stu-id="4aeae-126">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="4aeae-127">Порядок применения операторов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4aeae-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="4aeae-128">Список операторов, сгруппированных по функциональному назначению</span><span class="sxs-lookup"><span data-stu-id="4aeae-128">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="4aeae-129">Операторы</span><span class="sxs-lookup"><span data-stu-id="4aeae-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
