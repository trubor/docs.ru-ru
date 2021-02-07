---
description: Дополнительные сведения о инструкции Continue (Visual Basic)
title: Оператор Continue
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: c6d67e766b2551956795803076efe639ba3c8c99
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673873"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="c22b7-103">Оператор Continue (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c22b7-103">Continue Statement (Visual Basic)</span></span>

<span data-ttu-id="c22b7-104">Немедленно передает управление следующей итерации цикла.</span><span class="sxs-lookup"><span data-stu-id="c22b7-104">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c22b7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c22b7-105">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="c22b7-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="c22b7-106">Remarks</span></span>  

 <span data-ttu-id="c22b7-107">Можно переносить из `Do` `For` цикла, или `While` в следующую итерацию этого цикла.</span><span class="sxs-lookup"><span data-stu-id="c22b7-107">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="c22b7-108">Элемент управления сразу же передается в условие цикла, что эквивалентно передаче `For` инструкции или или `While` `Do` `Loop` инструкции или, содержащей `Until` `While` предложение OR.</span><span class="sxs-lookup"><span data-stu-id="c22b7-108">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="c22b7-109">Можно использовать `Continue` в любом расположении в цикле, допускающем передачу данных.</span><span class="sxs-lookup"><span data-stu-id="c22b7-109">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="c22b7-110">Правила, допускающие перемещение элементов управления, аналогичны [инструкциям оператора goto](goto-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c22b7-110">The rules allowing transfer of control are the same as with the [GoTo Statement](goto-statement.md).</span></span>  
  
 <span data-ttu-id="c22b7-111">Например, если цикл полностью содержится в `Try` блоке, `Catch` блоке или `Finally` блоке, можно использовать `Continue` для перемещения цикла.</span><span class="sxs-lookup"><span data-stu-id="c22b7-111">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="c22b7-112">Если, с другой стороны, `Try` структура... `End Try` содержится в цикле, нельзя использовать `Continue` для передачи управления из `Finally` блока, и ее можно использовать для передачи из `Try` блока или только в том `Catch` случае, если полностью передать из `Try` структуры... `End Try` .</span><span class="sxs-lookup"><span data-stu-id="c22b7-112">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="c22b7-113">При наличии вложенных циклов одного и того же типа, например `Do` цикла в другом `Do` цикле, `Continue Do` оператор переходит к следующей итерации самого внутреннего `Do` цикла, который его содержит.</span><span class="sxs-lookup"><span data-stu-id="c22b7-113">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="c22b7-114">Нельзя использовать `Continue` для перехода к следующей итерации содержащего цикла того же типа.</span><span class="sxs-lookup"><span data-stu-id="c22b7-114">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="c22b7-115">При наличии вложенных циклов разных типов, например цикла в `Do` `For` цикле, можно перейти к следующей итерации любого цикла, используя либо `Continue Do` или `Continue For` .</span><span class="sxs-lookup"><span data-stu-id="c22b7-115">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c22b7-116">Пример</span><span class="sxs-lookup"><span data-stu-id="c22b7-116">Example</span></span>  

 <span data-ttu-id="c22b7-117">В следующем примере кода инструкция используется `Continue While` для перехода к следующему столбцу массива, если делитель равен нулю.</span><span class="sxs-lookup"><span data-stu-id="c22b7-117">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="c22b7-118">`Continue While`Находится внутри `For` цикла.</span><span class="sxs-lookup"><span data-stu-id="c22b7-118">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="c22b7-119">Он передает `While col < lastcol` оператору, который является следующей итерацией самого внутреннего `While` цикла, содержащего `For` цикл.</span><span class="sxs-lookup"><span data-stu-id="c22b7-119">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="c22b7-120">См. также</span><span class="sxs-lookup"><span data-stu-id="c22b7-120">See also</span></span>

- [<span data-ttu-id="c22b7-121">Оператор Do…Loop</span><span class="sxs-lookup"><span data-stu-id="c22b7-121">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="c22b7-122">Оператор For…Next</span><span class="sxs-lookup"><span data-stu-id="c22b7-122">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="c22b7-123">Оператор While…End While</span><span class="sxs-lookup"><span data-stu-id="c22b7-123">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="c22b7-124">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="c22b7-124">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
