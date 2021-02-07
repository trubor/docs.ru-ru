---
description: 'Дополнительные сведения: оператор return (Visual Basic)'
title: Оператор Return
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: 62086090ede7e634b09d3edc3dc42feb28d15793
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741202"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="77ee0-103">Оператор Return (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77ee0-103">Return Statement (Visual Basic)</span></span>

<span data-ttu-id="77ee0-104">Возвращает управление коду, который вызвал `Function` процедуру,, `Sub` `Get` , `Set` или `Operator` .</span><span class="sxs-lookup"><span data-stu-id="77ee0-104">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77ee0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="77ee0-105">Syntax</span></span>  
  
```vb  
Return  
' -or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="77ee0-106">Отделение</span><span class="sxs-lookup"><span data-stu-id="77ee0-106">Part</span></span>  

 `expression`  
 <span data-ttu-id="77ee0-107">Требуется в `Function` процедуре, `Get` или `Operator` .</span><span class="sxs-lookup"><span data-stu-id="77ee0-107">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="77ee0-108">Выражение, представляющее значение, возвращаемое вызывающему коду.</span><span class="sxs-lookup"><span data-stu-id="77ee0-108">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77ee0-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="77ee0-109">Remarks</span></span>  

 <span data-ttu-id="77ee0-110">В `Sub` процедуре или `Set` `Return` инструкция эквивалентна `Exit Sub` `Exit Property` оператору или и `expression` не должна быть указана.</span><span class="sxs-lookup"><span data-stu-id="77ee0-110">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="77ee0-111">В `Function` процедуре, `Get` или `Operator` `Return` инструкция должна включать оператор `expression` и `expression` должен иметь тип данных, преобразуемый в возвращаемый тип процедуры.</span><span class="sxs-lookup"><span data-stu-id="77ee0-111">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="77ee0-112">В `Function` процедуре или `Get` вы также можете назначить выражение имени процедуры, которое будет использоваться в качестве возвращаемого значения, а затем выполнить `Exit Function` `Exit Property` инструкцию или.</span><span class="sxs-lookup"><span data-stu-id="77ee0-112">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="77ee0-113">В `Operator` процедуре необходимо использовать `Return expression` .</span><span class="sxs-lookup"><span data-stu-id="77ee0-113">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="77ee0-114">В одной процедуре можно включить столько инструкций, сколько `Return` необходимо.</span><span class="sxs-lookup"><span data-stu-id="77ee0-114">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="77ee0-115">Код в `Finally` блоке выполняется после `Return` обнаружения оператора в `Try` `Catch` блоке или, но перед `Return` выполнением этой инструкции.</span><span class="sxs-lookup"><span data-stu-id="77ee0-115">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="77ee0-116">`Return`Инструкция не может быть включена в `Finally` блок.</span><span class="sxs-lookup"><span data-stu-id="77ee0-116">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77ee0-117">Пример</span><span class="sxs-lookup"><span data-stu-id="77ee0-117">Example</span></span>  

 <span data-ttu-id="77ee0-118">В следующем примере оператор используется `Return` несколько раз для возврата к вызывающему коду, если процедура не должна предпринимать никаких других действий.</span><span class="sxs-lookup"><span data-stu-id="77ee0-118">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="77ee0-119">См. также</span><span class="sxs-lookup"><span data-stu-id="77ee0-119">See also</span></span>

- [<span data-ttu-id="77ee0-120">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="77ee0-120">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="77ee0-121">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="77ee0-121">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="77ee0-122">Оператор Get</span><span class="sxs-lookup"><span data-stu-id="77ee0-122">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="77ee0-123">Инструкция SET</span><span class="sxs-lookup"><span data-stu-id="77ee0-123">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="77ee0-124">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="77ee0-124">Operator Statement</span></span>](operator-statement.md)
- [<span data-ttu-id="77ee0-125">Property Statement</span><span class="sxs-lookup"><span data-stu-id="77ee0-125">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="77ee0-126">Оператор Exit</span><span class="sxs-lookup"><span data-stu-id="77ee0-126">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="77ee0-127">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="77ee0-127">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
