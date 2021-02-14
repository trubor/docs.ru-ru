---
description: Дополнительные сведения см. в статье как проверить, совпадают ли два объекта (Visual Basic)
title: Практическое руководство. Проверка совпадения двух объектов
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: a0136d9db487ad0ce70b9d55ff8ee014ec30b05a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100435542"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="a24e0-103">Практическое руководство. Проверка совпадения двух объектов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a24e0-103">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>

<span data-ttu-id="a24e0-104">При наличии двух переменных, ссылающихся на объекты, можно использовать либо `Is` `IsNot` оператор OR, либо и то, и другое, чтобы определить, ссылаются ли они на один и тот же экземпляр.</span><span class="sxs-lookup"><span data-stu-id="a24e0-104">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="a24e0-105">Проверка того, совпадают ли два объекта</span><span class="sxs-lookup"><span data-stu-id="a24e0-105">To test whether two objects are the same</span></span>  
  
- <span data-ttu-id="a24e0-106">Используйте [оператор is](../../../language-reference/operators/is-operator.md) или [IsNot](../../../language-reference/operators/isnot-operator.md) с двумя переменными в качестве операндов.</span><span class="sxs-lookup"><span data-stu-id="a24e0-106">Use the [Is Operator](../../../language-reference/operators/is-operator.md) or the [IsNot Operator](../../../language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="a24e0-107">Может потребоваться выполнить определенное действие в зависимости от того, ссылаются ли два объекта на один и тот же экземпляр.</span><span class="sxs-lookup"><span data-stu-id="a24e0-107">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="a24e0-108">Предыдущий пример сравнивает элемент управления с `c` активным элементом управления в форме `f` .</span><span class="sxs-lookup"><span data-stu-id="a24e0-108">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="a24e0-109">Если активный элемент управления отсутствует или имеется, но он не является одним и тем же экземпляром элемента управления `c` , то `If` выполнение инструкции завершается ошибкой и процедура возвращается без дальнейшей обработки.</span><span class="sxs-lookup"><span data-stu-id="a24e0-109">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="a24e0-110">Независимо от того, используется ли `Is` `IsNot` для вас персональное удобство.</span><span class="sxs-lookup"><span data-stu-id="a24e0-110">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="a24e0-111">Один из них может быть проще читать, чем другой в данном выражении.</span><span class="sxs-lookup"><span data-stu-id="a24e0-111">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a24e0-112">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a24e0-112">See also</span></span>

- [<span data-ttu-id="a24e0-113">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a24e0-113">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
