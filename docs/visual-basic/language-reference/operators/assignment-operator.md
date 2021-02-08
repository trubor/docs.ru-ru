---
description: 'Дополнительные сведения о операторе: = (Visual Basic)'
title: Оператор =
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 3cf45fb93bf5138f9e7fa5a43650019ab58674fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774256"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="40f10-103">Оператор = (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40f10-103">= Operator (Visual Basic)</span></span>

<span data-ttu-id="40f10-104">Присваивает значение переменной или свойству.</span><span class="sxs-lookup"><span data-stu-id="40f10-104">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40f10-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="40f10-105">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="40f10-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="40f10-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="40f10-107">Любая изменяемая переменная или любое свойство.</span><span class="sxs-lookup"><span data-stu-id="40f10-107">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="40f10-108">Любой литерал, константа или выражение.</span><span class="sxs-lookup"><span data-stu-id="40f10-108">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40f10-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="40f10-109">Remarks</span></span>  

 <span data-ttu-id="40f10-110">Элемент в левой части знака равенства ( `=` ) может быть простой скалярной переменной, свойством или элементом массива.</span><span class="sxs-lookup"><span data-stu-id="40f10-110">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="40f10-111">Переменная или свойство не может быть [ReadOnly](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="40f10-111">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="40f10-112">`=`Оператор присваивает значение справа переменной или свойству слева.</span><span class="sxs-lookup"><span data-stu-id="40f10-112">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40f10-113">`=`Оператор также используется в качестве оператора сравнения.</span><span class="sxs-lookup"><span data-stu-id="40f10-113">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="40f10-114">Дополнительные сведения см. в разделе [Операторы сравнения](comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="40f10-114">For details, see [Comparison Operators](comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="40f10-115">Перегрузка</span><span class="sxs-lookup"><span data-stu-id="40f10-115">Overloading</span></span>  

 <span data-ttu-id="40f10-116">`=`Оператор может быть перегружен только как оператор реляционного сравнения, а не как оператор присваивания.</span><span class="sxs-lookup"><span data-stu-id="40f10-116">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="40f10-117">Для получения дополнительной информации см. [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="40f10-117">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40f10-118">Пример</span><span class="sxs-lookup"><span data-stu-id="40f10-118">Example</span></span>  

 <span data-ttu-id="40f10-119">В следующем примере показан оператор присваивания.</span><span class="sxs-lookup"><span data-stu-id="40f10-119">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="40f10-120">Значение справа присваивается переменной слева.</span><span class="sxs-lookup"><span data-stu-id="40f10-120">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="40f10-121">См. также</span><span class="sxs-lookup"><span data-stu-id="40f10-121">See also</span></span>

- [<span data-ttu-id="40f10-122"> Оператор&=</span><span class="sxs-lookup"><span data-stu-id="40f10-122">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="40f10-123">Оператор \* =</span><span class="sxs-lookup"><span data-stu-id="40f10-123">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="40f10-124">Оператор + =</span><span class="sxs-lookup"><span data-stu-id="40f10-124">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="40f10-125">Оператор-= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40f10-125">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="40f10-126">Оператор/= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40f10-126">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="40f10-127">\\Оператор =</span><span class="sxs-lookup"><span data-stu-id="40f10-127">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="40f10-128">Оператор ^ =</span><span class="sxs-lookup"><span data-stu-id="40f10-128">^= Operator</span></span>](exponentiation-assignment-operator.md)
- [<span data-ttu-id="40f10-129">Операторы</span><span class="sxs-lookup"><span data-stu-id="40f10-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="40f10-130">Операторы сравнения</span><span class="sxs-lookup"><span data-stu-id="40f10-130">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="40f10-131">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="40f10-131">ReadOnly</span></span>](../modifiers/readonly.md)
- [<span data-ttu-id="40f10-132">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="40f10-132">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
