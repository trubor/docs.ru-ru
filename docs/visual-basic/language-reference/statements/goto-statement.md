---
description: 'Дополнительные сведения о инструкции: GoTo'
title: Оператор GoTo
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: 804baec130111562225b09cbdc7b5fb2d73adba5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769056"
---
# <a name="goto-statement"></a><span data-ttu-id="2df67-103">Оператор GoTo</span><span class="sxs-lookup"><span data-stu-id="2df67-103">GoTo Statement</span></span>

<span data-ttu-id="2df67-104">Безусловно подразделяется на указанную строку в процедуре.</span><span class="sxs-lookup"><span data-stu-id="2df67-104">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2df67-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2df67-105">Syntax</span></span>  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="2df67-106">Отделение</span><span class="sxs-lookup"><span data-stu-id="2df67-106">Part</span></span>  

 `line`  
 <span data-ttu-id="2df67-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="2df67-107">Required.</span></span> <span data-ttu-id="2df67-108">Метка любой линии.</span><span class="sxs-lookup"><span data-stu-id="2df67-108">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2df67-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="2df67-109">Remarks</span></span>  

 <span data-ttu-id="2df67-110">`GoTo`Оператор может создать ветвь только для строк в процедуре, в которой она отображается.</span><span class="sxs-lookup"><span data-stu-id="2df67-110">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="2df67-111">Строка должна иметь метку, которая `GoTo` может ссылаться на.</span><span class="sxs-lookup"><span data-stu-id="2df67-111">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="2df67-112">Дополнительные сведения см. [в разделе инструкции. Метки](../../programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="2df67-112">For more information, see [How to: Label Statements](../../programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2df67-113">`GoTo` инструкции могут усложнить чтение и поддержку кода.</span><span class="sxs-lookup"><span data-stu-id="2df67-113">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="2df67-114">Везде, где это возможно, следует использовать структуру элементов управления.</span><span class="sxs-lookup"><span data-stu-id="2df67-114">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="2df67-115">Дополнительные сведения см. в разделе [Поток управления](../../programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="2df67-115">For more information, see [Control Flow](../../programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="2df67-116">Нельзя использовать `GoTo` оператор для ветвления извне `For` ... `Next` , `For Each` ... `Next` , `SyncLock` ... `End SyncLock` , `Try` . `Catch` .. ... `Finally` , `With` ... `End With` или `Using` ... `End Using` конструкция к метке внутри.</span><span class="sxs-lookup"><span data-stu-id="2df67-116">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="2df67-117">Ветвление и конструкции try</span><span class="sxs-lookup"><span data-stu-id="2df67-117">Branching and Try Constructions</span></span>  

 <span data-ttu-id="2df67-118">В `Try` ... `Catch` ...`Finally` для создания ветвления с помощью оператора применяются следующие правила `GoTo` .</span><span class="sxs-lookup"><span data-stu-id="2df67-118">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="2df67-119">Блок или область</span><span class="sxs-lookup"><span data-stu-id="2df67-119">Block or region</span></span>|<span data-ttu-id="2df67-120">Ветвление вне</span><span class="sxs-lookup"><span data-stu-id="2df67-120">Branching in from outside</span></span>|<span data-ttu-id="2df67-121">Ветвление из внутрь</span><span class="sxs-lookup"><span data-stu-id="2df67-121">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="2df67-122">`Try` блок</span><span class="sxs-lookup"><span data-stu-id="2df67-122">`Try` block</span></span>|<span data-ttu-id="2df67-123">Только из `Catch` блока одной конструкции <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2df67-123">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="2df67-124">Только за пределами всей конструкции</span><span class="sxs-lookup"><span data-stu-id="2df67-124">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="2df67-125">`Catch` блок</span><span class="sxs-lookup"><span data-stu-id="2df67-125">`Catch` block</span></span>|<span data-ttu-id="2df67-126">Никогда не разрешено</span><span class="sxs-lookup"><span data-stu-id="2df67-126">Never allowed</span></span>|<span data-ttu-id="2df67-127">Только за пределами всей конструкции или с `Try` блоком той же конструкции <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2df67-127">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="2df67-128">`Finally` блок</span><span class="sxs-lookup"><span data-stu-id="2df67-128">`Finally` block</span></span>|<span data-ttu-id="2df67-129">Никогда не разрешено</span><span class="sxs-lookup"><span data-stu-id="2df67-129">Never allowed</span></span>|<span data-ttu-id="2df67-130">Никогда не разрешено</span><span class="sxs-lookup"><span data-stu-id="2df67-130">Never allowed</span></span>|  
  
 <span data-ttu-id="2df67-131"><sup>1</sup> , если один `Try` ... `Catch` ...`Finally` Конструкция вложена в другую, `Catch` блок может выполнять ветвление в `Try` блок на своем собственном уровне вложенности, но не в другой `Try` блок.</span><span class="sxs-lookup"><span data-stu-id="2df67-131"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="2df67-132">Вложенный `Try` ... `Catch` ...`Finally` конструкция должна полностью содержаться в `Try` `Catch` блоке или конструкции, внутри которой она вложена.</span><span class="sxs-lookup"><span data-stu-id="2df67-132">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="2df67-133">На следующем рисунке показана одна `Try` конструкция, вложенная в другую.</span><span class="sxs-lookup"><span data-stu-id="2df67-133">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="2df67-134">Различные ветви между блоками двух конструкций указываются как допустимые или недопустимые.</span><span class="sxs-lookup"><span data-stu-id="2df67-134">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Графическая схема ветвления в конструкциях Try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="2df67-136">Пример</span><span class="sxs-lookup"><span data-stu-id="2df67-136">Example</span></span>  

 <span data-ttu-id="2df67-137">В следующем примере оператор используется `GoTo` для перехода к меткам линии в процедуре.</span><span class="sxs-lookup"><span data-stu-id="2df67-137">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="2df67-138">См. также</span><span class="sxs-lookup"><span data-stu-id="2df67-138">See also</span></span>

- [<span data-ttu-id="2df67-139">Оператор Do…Loop</span><span class="sxs-lookup"><span data-stu-id="2df67-139">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="2df67-140">Оператор For…Next</span><span class="sxs-lookup"><span data-stu-id="2df67-140">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="2df67-141">Оператор For Each…Next</span><span class="sxs-lookup"><span data-stu-id="2df67-141">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="2df67-142">Оператор If…Then…Else</span><span class="sxs-lookup"><span data-stu-id="2df67-142">If...Then...Else Statement</span></span>](if-then-else-statement.md)
- [<span data-ttu-id="2df67-143">Оператор Select…Case</span><span class="sxs-lookup"><span data-stu-id="2df67-143">Select...Case Statement</span></span>](select-case-statement.md)
- [<span data-ttu-id="2df67-144">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="2df67-144">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="2df67-145">Оператор While…End While</span><span class="sxs-lookup"><span data-stu-id="2df67-145">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="2df67-146">Оператор With…End With</span><span class="sxs-lookup"><span data-stu-id="2df67-146">With...End With Statement</span></span>](with-end-with-statement.md)
