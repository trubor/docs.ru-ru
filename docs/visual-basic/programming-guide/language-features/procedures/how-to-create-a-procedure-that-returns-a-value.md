---
description: Дополнительные сведения о том, как создать процедуру, возвращающую значение (Visual Basic).
title: Практическое руководство. Создание процедуры, возвращающей значение
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: fa2ea50febd1cc4e7aecf1e6f5cca671789b36fd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100467060"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="03bb3-103">Практическое руководство. Создание процедуры, возвращающей значение (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03bb3-103">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>

<span data-ttu-id="03bb3-104">Для `Function` возврата значения в вызывающий код используется процедура.</span><span class="sxs-lookup"><span data-stu-id="03bb3-104">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="03bb3-105">Создание процедуры, возвращающей значение</span><span class="sxs-lookup"><span data-stu-id="03bb3-105">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="03bb3-106">За пределами любой другой процедуры используйте `Function` оператор, за которым следует `End Function` оператор.</span><span class="sxs-lookup"><span data-stu-id="03bb3-106">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="03bb3-107">В `Function` инструкции используйте `Function` ключевое слово с именем процедуры, а затем список параметров в круглых скобках.</span><span class="sxs-lookup"><span data-stu-id="03bb3-107">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="03bb3-108">Используйте круглые скобки с `As` предложением, чтобы указать тип данных возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="03bb3-108">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4. <span data-ttu-id="03bb3-109">Поместите операторы кода процедуры между `Function` `End Function` операторами и.</span><span class="sxs-lookup"><span data-stu-id="03bb3-109">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5. <span data-ttu-id="03bb3-110">Используйте `Return` оператор, чтобы вернуть значение в вызывающий код.</span><span class="sxs-lookup"><span data-stu-id="03bb3-110">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="03bb3-111">Следующая `Function` процедура вычисляет самую длинную сторону (гипотенузу) правого треугольника, учитывая значения двух других сторон.</span><span class="sxs-lookup"><span data-stu-id="03bb3-111">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="03bb3-112">В следующем примере показан типичный вызов метода `hypotenuse` .</span><span class="sxs-lookup"><span data-stu-id="03bb3-112">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="03bb3-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="03bb3-113">See also</span></span>

- [<span data-ttu-id="03bb3-114">Процедуры</span><span class="sxs-lookup"><span data-stu-id="03bb3-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="03bb3-115">Подпрограммы</span><span class="sxs-lookup"><span data-stu-id="03bb3-115">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="03bb3-116">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="03bb3-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="03bb3-117">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="03bb3-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="03bb3-118">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="03bb3-118">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="03bb3-119">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="03bb3-119">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="03bb3-120">Практическое руководство. Возврат значения из процедуры</span><span class="sxs-lookup"><span data-stu-id="03bb3-120">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="03bb3-121">Практическое руководство. Вызов процедуры, возвращающей значение</span><span class="sxs-lookup"><span data-stu-id="03bb3-121">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
