---
description: Дополнительные сведения см. в статье как вернуть значение из процедуры (Visual Basic).
title: Практическое руководство. Возврат значения из процедуры
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: c158f15b1e6acb7334d78037d84145981822e177
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476180"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="bdf53-103">Практическое руководство. Возврат значения из процедуры (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdf53-103">How to: Return a Value from a Procedure (Visual Basic)</span></span>

<span data-ttu-id="bdf53-104">`Function`Процедура возвращает значение в вызывающий код, выполняя инструкцию или выполняя инструкцию `Return` `Exit Function` или `End Function` .</span><span class="sxs-lookup"><span data-stu-id="bdf53-104">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="bdf53-105">Возврат значения с помощью оператора return</span><span class="sxs-lookup"><span data-stu-id="bdf53-105">To return a value using the Return statement</span></span>  
  
1. <span data-ttu-id="bdf53-106">Поместите `Return` оператор в точку завершения задачи процедуры.</span><span class="sxs-lookup"><span data-stu-id="bdf53-106">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2. <span data-ttu-id="bdf53-107">Используйте `Return` ключевое слово с выражением, которое возвращает значение, которое необходимо вернуть в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="bdf53-107">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3. <span data-ttu-id="bdf53-108">В одной и той же процедуре можно использовать несколько операторов `Return`.</span><span class="sxs-lookup"><span data-stu-id="bdf53-108">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="bdf53-109">Следующая `Function` процедура вычисляет самую длинную сторону (гипотенузу) правого треугольника и возвращает ее в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="bdf53-109">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="bdf53-110">В следующем примере показан типичный вызов метода `hypotenuse` , в котором хранится возвращаемое значение.</span><span class="sxs-lookup"><span data-stu-id="bdf53-110">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="bdf53-111">Возврат значения с помощью функции exit или функции End</span><span class="sxs-lookup"><span data-stu-id="bdf53-111">To return a value using Exit Function or End Function</span></span>  
  
1. <span data-ttu-id="bdf53-112">По крайней мере в одном месте `Function` процедуры присвойте значение имени процедуры.</span><span class="sxs-lookup"><span data-stu-id="bdf53-112">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2. <span data-ttu-id="bdf53-113">При выполнении `Exit Function` `End Function` инструкции или Visual Basic возвращает последнее значение, назначенное имени процедуры.</span><span class="sxs-lookup"><span data-stu-id="bdf53-113">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3. <span data-ttu-id="bdf53-114">В одной и той же процедуре можно использовать несколько операторов `Exit Function` и одновременно использовать операторы `Return` и `Exit Function`.</span><span class="sxs-lookup"><span data-stu-id="bdf53-114">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4. <span data-ttu-id="bdf53-115">В процедуре может быть только одна `End Function` инструкция `Function` .</span><span class="sxs-lookup"><span data-stu-id="bdf53-115">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="bdf53-116">Дополнительные сведения и пример см. в разделе "возвращаемое значение" в [операторе Function](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="bdf53-116">For more information and an example, see "Return Value" in [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf53-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="bdf53-117">See also</span></span>

- [<span data-ttu-id="bdf53-118">Процедуры</span><span class="sxs-lookup"><span data-stu-id="bdf53-118">Procedures</span></span>](./index.md)
- [<span data-ttu-id="bdf53-119">Подпрограммы</span><span class="sxs-lookup"><span data-stu-id="bdf53-119">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="bdf53-120">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="bdf53-120">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="bdf53-121">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="bdf53-121">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="bdf53-122">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="bdf53-122">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="bdf53-123">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="bdf53-123">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="bdf53-124">Оператор Return</span><span class="sxs-lookup"><span data-stu-id="bdf53-124">Return Statement</span></span>](../../../language-reference/statements/return-statement.md)
- [<span data-ttu-id="bdf53-125">Практическое руководство. Создание процедуры, возвращающей значение</span><span class="sxs-lookup"><span data-stu-id="bdf53-125">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="bdf53-126">Практическое руководство. Вызов процедуры, возвращающей значение</span><span class="sxs-lookup"><span data-stu-id="bdf53-126">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
