---
description: 'Дополнительные сведения о инструкции: Exit (Visual Basic)'
title: Оператор Exit
ms.date: 07/20/2015
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
ms.openlocfilehash: 54af7fbf908dbad829cf6f08bf442dfe85e35610
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769132"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="dbbab-103">Оператор Exit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbbab-103">Exit Statement (Visual Basic)</span></span>

<span data-ttu-id="dbbab-104">Выходит из процедуры или блока и немедленно передает управление оператору после вызова процедуры или определения блока.</span><span class="sxs-lookup"><span data-stu-id="dbbab-104">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="dbbab-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dbbab-105">Syntax</span></span>

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a><span data-ttu-id="dbbab-106">Операторы</span><span class="sxs-lookup"><span data-stu-id="dbbab-106">Statements</span></span>

 `Exit Do`  
 <span data-ttu-id="dbbab-107">Немедленно завершает работу `Do` цикла, в котором он отображается.</span><span class="sxs-lookup"><span data-stu-id="dbbab-107">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="dbbab-108">Выполнение продолжится с оператора, следующего за `Loop` оператором.</span><span class="sxs-lookup"><span data-stu-id="dbbab-108">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="dbbab-109">`Exit Do` может использоваться только внутри `Do` цикла.</span><span class="sxs-lookup"><span data-stu-id="dbbab-109">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="dbbab-110">При использовании внутри вложенных `Do` циклов `Exit Do` выходит из внутреннего цикла и передает управление следующему более высокому уровню вложенности.</span><span class="sxs-lookup"><span data-stu-id="dbbab-110">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit For`  
 <span data-ttu-id="dbbab-111">Немедленно завершает работу `For` цикла, в котором он отображается.</span><span class="sxs-lookup"><span data-stu-id="dbbab-111">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="dbbab-112">Выполнение продолжится с оператора, следующего за `Next` оператором.</span><span class="sxs-lookup"><span data-stu-id="dbbab-112">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="dbbab-113">`Exit For`может использоваться только внутри `For` цикла... `Next` или `For Each` ... `Next`</span><span class="sxs-lookup"><span data-stu-id="dbbab-113">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="dbbab-114">При использовании внутри вложенных `For` циклов `Exit For` выходит из внутреннего цикла и передает управление следующему более высокому уровню вложенности.</span><span class="sxs-lookup"><span data-stu-id="dbbab-114">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit Function`  
 <span data-ttu-id="dbbab-115">Немедленно завершает процедуру, `Function` в которой она отображается.</span><span class="sxs-lookup"><span data-stu-id="dbbab-115">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="dbbab-116">Выполнение продолжится с оператора, следующего за инструкцией, вызвавшей `Function` процедуру.</span><span class="sxs-lookup"><span data-stu-id="dbbab-116">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="dbbab-117">`Exit Function` может использоваться только внутри `Function` процедуры.</span><span class="sxs-lookup"><span data-stu-id="dbbab-117">`Exit Function` can be used only inside a `Function` procedure.</span></span>

 <span data-ttu-id="dbbab-118">Чтобы указать возвращаемое значение, можно присвоить значение имени функции в строке перед `Exit Function` инструкцией.</span><span class="sxs-lookup"><span data-stu-id="dbbab-118">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="dbbab-119">Чтобы присвоить возвращаемое значение и выйти из функции в одной инструкции, можно использовать [оператор return](return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="dbbab-119">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](return-statement.md).</span></span>

 `Exit Property`  
 <span data-ttu-id="dbbab-120">Немедленно завершает процедуру, `Property` в которой она отображается.</span><span class="sxs-lookup"><span data-stu-id="dbbab-120">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="dbbab-121">Выполнение продолжится инструкцией, вызвавшей `Property` процедуру, то есть с инструкцией, запрашивающей или задавая значение свойства.</span><span class="sxs-lookup"><span data-stu-id="dbbab-121">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="dbbab-122">`Exit Property` может использоваться только внутри `Get` процедуры свойства или `Set` .</span><span class="sxs-lookup"><span data-stu-id="dbbab-122">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>

 <span data-ttu-id="dbbab-123">Чтобы указать возвращаемое значение в `Get` процедуре, можно присвоить значение имени функции в строке перед `Exit Property` инструкцией.</span><span class="sxs-lookup"><span data-stu-id="dbbab-123">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="dbbab-124">Чтобы присвоить возвращаемое значение и выйти из `Get` процедуры в одной инструкции, можно использовать `Return` инструкцию.</span><span class="sxs-lookup"><span data-stu-id="dbbab-124">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>

 <span data-ttu-id="dbbab-125">В `Set` процедуре `Exit Property` инструкция эквивалентна `Return` инструкции.</span><span class="sxs-lookup"><span data-stu-id="dbbab-125">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>

 `Exit Select`  
 <span data-ttu-id="dbbab-126">Немедленно завершает работу `Select Case` блока, в котором он отображается.</span><span class="sxs-lookup"><span data-stu-id="dbbab-126">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="dbbab-127">Выполнение продолжится с оператора, следующего за `End Select` оператором.</span><span class="sxs-lookup"><span data-stu-id="dbbab-127">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="dbbab-128">`Exit Select` может использоваться только внутри `Select Case` оператора.</span><span class="sxs-lookup"><span data-stu-id="dbbab-128">`Exit Select` can be used only inside a `Select Case` statement.</span></span>

 `Exit Sub`  
 <span data-ttu-id="dbbab-129">Немедленно завершает процедуру, `Sub` в которой она отображается.</span><span class="sxs-lookup"><span data-stu-id="dbbab-129">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="dbbab-130">Выполнение продолжится с оператора, следующего за инструкцией, вызвавшей `Sub` процедуру.</span><span class="sxs-lookup"><span data-stu-id="dbbab-130">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="dbbab-131">`Exit Sub` может использоваться только внутри `Sub` процедуры.</span><span class="sxs-lookup"><span data-stu-id="dbbab-131">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>

 <span data-ttu-id="dbbab-132">В `Sub` процедуре `Exit Sub` инструкция эквивалентна `Return` инструкции.</span><span class="sxs-lookup"><span data-stu-id="dbbab-132">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>

 `Exit Try`  
 <span data-ttu-id="dbbab-133">Немедленно завершает работу `Try` блока или, `Catch` в котором он отображается.</span><span class="sxs-lookup"><span data-stu-id="dbbab-133">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="dbbab-134">Выполнение продолжится с `Finally` блока, если таковой имеется, или с оператором, который следует `End Try` в противном случае.</span><span class="sxs-lookup"><span data-stu-id="dbbab-134">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="dbbab-135">`Exit Try` может использоваться только внутри `Try` `Catch` блока или, а не внутри `Finally` блока.</span><span class="sxs-lookup"><span data-stu-id="dbbab-135">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>

 `Exit While`  
 <span data-ttu-id="dbbab-136">Немедленно завершает работу `While` цикла, в котором он отображается.</span><span class="sxs-lookup"><span data-stu-id="dbbab-136">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="dbbab-137">Выполнение продолжится с оператора, следующего за `End While` оператором.</span><span class="sxs-lookup"><span data-stu-id="dbbab-137">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="dbbab-138">`Exit While` может использоваться только внутри `While` цикла.</span><span class="sxs-lookup"><span data-stu-id="dbbab-138">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="dbbab-139">При использовании внутри вложенных `While` циклов `Exit While` передает управление циклу, который является одним вложенным уровнем над циклом, где `Exit While` происходит.</span><span class="sxs-lookup"><span data-stu-id="dbbab-139">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>

## <a name="remarks"></a><span data-ttu-id="dbbab-140">Remarks</span><span class="sxs-lookup"><span data-stu-id="dbbab-140">Remarks</span></span>

<span data-ttu-id="dbbab-141">Не путайте `Exit` Операторы с `End` операторами.</span><span class="sxs-lookup"><span data-stu-id="dbbab-141">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="dbbab-142">`Exit` не определяет конец инструкции.</span><span class="sxs-lookup"><span data-stu-id="dbbab-142">`Exit` does not define the end of a statement.</span></span>

## <a name="example"></a><span data-ttu-id="dbbab-143">Пример</span><span class="sxs-lookup"><span data-stu-id="dbbab-143">Example</span></span>

<span data-ttu-id="dbbab-144">В следующем примере условие цикла останавливает цикл, если `index` переменная больше 100.</span><span class="sxs-lookup"><span data-stu-id="dbbab-144">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="dbbab-145">`If`Однако инструкция в цикле приводит к `Exit Do` остановке цикла, если переменная индекса больше 10.</span><span class="sxs-lookup"><span data-stu-id="dbbab-145">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a><span data-ttu-id="dbbab-146">Пример</span><span class="sxs-lookup"><span data-stu-id="dbbab-146">Example</span></span>

<span data-ttu-id="dbbab-147">В следующем примере возвращаемое значение присваивается имени функции `myFunction` , а затем используется `Exit Function` для возврата из функции:</span><span class="sxs-lookup"><span data-stu-id="dbbab-147">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function:</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a><span data-ttu-id="dbbab-148">Пример</span><span class="sxs-lookup"><span data-stu-id="dbbab-148">Example</span></span>

<span data-ttu-id="dbbab-149">В следующем примере [оператор return](return-statement.md) используется для назначения возвращаемого значения и выхода из функции:</span><span class="sxs-lookup"><span data-stu-id="dbbab-149">The following example uses the [Return Statement](return-statement.md) to assign the return value and exit the function:</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="dbbab-150">См. также</span><span class="sxs-lookup"><span data-stu-id="dbbab-150">See also</span></span>

- [<span data-ttu-id="dbbab-151">Оператор Continue</span><span class="sxs-lookup"><span data-stu-id="dbbab-151">Continue Statement</span></span>](continue-statement.md)
- [<span data-ttu-id="dbbab-152">Оператор Do…Loop</span><span class="sxs-lookup"><span data-stu-id="dbbab-152">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="dbbab-153">End, инструкция</span><span class="sxs-lookup"><span data-stu-id="dbbab-153">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="dbbab-154">Оператор For Each…Next</span><span class="sxs-lookup"><span data-stu-id="dbbab-154">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="dbbab-155">Оператор For…Next</span><span class="sxs-lookup"><span data-stu-id="dbbab-155">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="dbbab-156">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="dbbab-156">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="dbbab-157">Оператор Return</span><span class="sxs-lookup"><span data-stu-id="dbbab-157">Return Statement</span></span>](return-statement.md)
- [<span data-ttu-id="dbbab-158">Оператор Stop</span><span class="sxs-lookup"><span data-stu-id="dbbab-158">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="dbbab-159">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="dbbab-159">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="dbbab-160">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="dbbab-160">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
