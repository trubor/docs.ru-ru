---
description: 'Дополнительные сведения о: для... Оператор Next (Visual Basic)'
title: Оператор For…Next
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: f26d9cb1885d9d22b96d622f44325aad64e34d1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769082"
---
# <a name="fornext-statement-visual-basic"></a><span data-ttu-id="e8434-103">Оператор For... Next (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8434-103">For...Next Statement (Visual Basic)</span></span>

<span data-ttu-id="e8434-104">Повторяет группу инструкций указанное число раз.</span><span class="sxs-lookup"><span data-stu-id="e8434-104">Repeats a group of statements a specified number of times.</span></span>

## <a name="syntax"></a><span data-ttu-id="e8434-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e8434-105">Syntax</span></span>

```vb
For counter [ As datatype ] = start To end [ Step step ]
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ counter ]
```

## <a name="parts"></a><span data-ttu-id="e8434-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="e8434-106">Parts</span></span>

|<span data-ttu-id="e8434-107">Отделение</span><span class="sxs-lookup"><span data-stu-id="e8434-107">Part</span></span>|<span data-ttu-id="e8434-108">Описание</span><span class="sxs-lookup"><span data-stu-id="e8434-108">Description</span></span>|
|----------|-----------------|
|`counter`|<span data-ttu-id="e8434-109">Требуется в `For` инструкции.</span><span class="sxs-lookup"><span data-stu-id="e8434-109">Required in the `For` statement.</span></span> <span data-ttu-id="e8434-110">Числовая переменная.</span><span class="sxs-lookup"><span data-stu-id="e8434-110">Numeric variable.</span></span> <span data-ttu-id="e8434-111">Управляющая переменная для цикла.</span><span class="sxs-lookup"><span data-stu-id="e8434-111">The control variable for the loop.</span></span> <span data-ttu-id="e8434-112">Дополнительные сведения см. в подразделе [аргумент Counter](#BKMK_Counter) далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="e8434-112">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`datatype`|<span data-ttu-id="e8434-113">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="e8434-113">Optional.</span></span> <span data-ttu-id="e8434-114">Тип данных `counter` .</span><span class="sxs-lookup"><span data-stu-id="e8434-114">Data type of `counter`.</span></span> <span data-ttu-id="e8434-115">Дополнительные сведения см. в подразделе [аргумент Counter](#BKMK_Counter) далее в этой статье.</span><span class="sxs-lookup"><span data-stu-id="e8434-115">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`start`|<span data-ttu-id="e8434-116">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="e8434-116">Required.</span></span> <span data-ttu-id="e8434-117">Числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="e8434-117">Numeric expression.</span></span> <span data-ttu-id="e8434-118">Начальное значение `counter`.</span><span class="sxs-lookup"><span data-stu-id="e8434-118">The initial value of `counter`.</span></span>|
|`end`|<span data-ttu-id="e8434-119">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="e8434-119">Required.</span></span> <span data-ttu-id="e8434-120">Числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="e8434-120">Numeric expression.</span></span> <span data-ttu-id="e8434-121">Конечное значение `counter` .</span><span class="sxs-lookup"><span data-stu-id="e8434-121">The final value of `counter`.</span></span>|
|`step`|<span data-ttu-id="e8434-122">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="e8434-122">Optional.</span></span> <span data-ttu-id="e8434-123">Числовое выражение.</span><span class="sxs-lookup"><span data-stu-id="e8434-123">Numeric expression.</span></span> <span data-ttu-id="e8434-124">Величина, на которую `counter` увеличивается каждый раз с помощью цикла.</span><span class="sxs-lookup"><span data-stu-id="e8434-124">The amount by which `counter` is incremented each time through the loop.</span></span>|
|`statements`|<span data-ttu-id="e8434-125">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="e8434-125">Optional.</span></span> <span data-ttu-id="e8434-126">Одна или несколько инструкций между `For` и `Next` выполняются указанное число раз.</span><span class="sxs-lookup"><span data-stu-id="e8434-126">One or more statements between `For` and `Next` that run the specified number of times.</span></span>|
|`Continue For`|<span data-ttu-id="e8434-127">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="e8434-127">Optional.</span></span> <span data-ttu-id="e8434-128">Передает управление в следующую итерацию цикла.</span><span class="sxs-lookup"><span data-stu-id="e8434-128">Transfers control to the next loop iteration.</span></span>|
|`Exit For`|<span data-ttu-id="e8434-129">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="e8434-129">Optional.</span></span> <span data-ttu-id="e8434-130">Передает управление за пределы `For` цикла.</span><span class="sxs-lookup"><span data-stu-id="e8434-130">Transfers control out of the `For` loop.</span></span>|
|`Next`|<span data-ttu-id="e8434-131">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="e8434-131">Required.</span></span> <span data-ttu-id="e8434-132">Завершает определение `For` цикла.</span><span class="sxs-lookup"><span data-stu-id="e8434-132">Terminates the definition of the `For` loop.</span></span>|

> [!NOTE]
> <span data-ttu-id="e8434-133">`To`Ключевое слово используется в этом операторе для указания диапазона счетчика.</span><span class="sxs-lookup"><span data-stu-id="e8434-133">The `To` keyword is used in this statement to specify the range for the counter.</span></span> <span data-ttu-id="e8434-134">Это ключевое слово также можно использовать в [SELECT... Оператор Case](select-case-statement.md) и в объявлениях массивов.</span><span class="sxs-lookup"><span data-stu-id="e8434-134">You can also use this keyword in the [Select...Case Statement](select-case-statement.md) and in array declarations.</span></span> <span data-ttu-id="e8434-135">Дополнительные сведения об объявлениях массивов см. в разделе [оператор Dim](dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e8434-135">For more information about array declarations, see [Dim Statement](dim-statement.md).</span></span>

## <a name="simple-examples"></a><span data-ttu-id="e8434-136"> Простые примеры</span><span class="sxs-lookup"><span data-stu-id="e8434-136">Simple Examples</span></span>

<span data-ttu-id="e8434-137">Используйте `For` структуру..., `Next` Если нужно повторить набор инструкций заданное число раз.</span><span class="sxs-lookup"><span data-stu-id="e8434-137">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span></span>

<span data-ttu-id="e8434-138">В следующем примере `index` переменная начинается со значения 1 и увеличивается при каждой итерации цикла, после чего значение `index` достигает 5.</span><span class="sxs-lookup"><span data-stu-id="e8434-138">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span></span>

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

<span data-ttu-id="e8434-139">В следующем примере `number` переменная начинается с 2 и уменьшается на 0,25 в каждой итерации цикла, после чего значение `number` достигнет 0.</span><span class="sxs-lookup"><span data-stu-id="e8434-139">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span></span> <span data-ttu-id="e8434-140">`Step`Аргумент класса `-.25` сокращает значение на 0,25 при каждой итерации цикла.</span><span class="sxs-lookup"><span data-stu-id="e8434-140">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> <span data-ttu-id="e8434-141">Ответ [... Конец оператора while](while-end-while-statement.md) или [Do... Оператор Loop](do-loop-statement.md) хорошо работает, если заранее неизвестно, сколько раз нужно выполнять инструкции в цикле.</span><span class="sxs-lookup"><span data-stu-id="e8434-141">A [While...End While Statement](while-end-while-statement.md) or [Do...Loop Statement](do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span></span> <span data-ttu-id="e8434-142">Однако, если вы планируете выполнять цикл определенное число раз, `For` `Next` лучше выбрать цикл....</span><span class="sxs-lookup"><span data-stu-id="e8434-142">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span></span> <span data-ttu-id="e8434-143">Число итераций определяется при первом входе в цикл.</span><span class="sxs-lookup"><span data-stu-id="e8434-143">You determine the number of iterations when you first enter the loop.</span></span>

## <a name="nesting-loops"></a><span data-ttu-id="e8434-144">Вложенные циклы</span><span class="sxs-lookup"><span data-stu-id="e8434-144">Nesting Loops</span></span>

<span data-ttu-id="e8434-145">Можно вложить `For` циклы, поместив один цикл в другой.</span><span class="sxs-lookup"><span data-stu-id="e8434-145">You can nest `For` loops by putting one loop within another.</span></span> <span data-ttu-id="e8434-146">В следующем примере показаны вложенные `For` структуры... `Next` , имеющие разные значения шага.</span><span class="sxs-lookup"><span data-stu-id="e8434-146">The following example demonstrates nested `For`...`Next` structures that have different step values.</span></span> <span data-ttu-id="e8434-147">Внешний цикл создает строку для каждой итерации цикла.</span><span class="sxs-lookup"><span data-stu-id="e8434-147">The outer loop creates a string for every iteration of the loop.</span></span> <span data-ttu-id="e8434-148">Внутренний цикл уменьшает переменную счетчика цикла для каждой итерации цикла.</span><span class="sxs-lookup"><span data-stu-id="e8434-148">The inner loop decrements a loop counter variable for every iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

<span data-ttu-id="e8434-149">При вложенных циклах каждый цикл должен иметь уникальную `counter` переменную.</span><span class="sxs-lookup"><span data-stu-id="e8434-149">When nesting loops, each loop must have a unique `counter` variable.</span></span>

<span data-ttu-id="e8434-150">Вы также можете вкладывать различные виды управления в друг друга.</span><span class="sxs-lookup"><span data-stu-id="e8434-150">You can also nest different kinds control structures within each other.</span></span> <span data-ttu-id="e8434-151">Дополнительные сведения см. в разделе [вложенные структуры управления](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="e8434-151">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

## <a name="exit-for-and-continue-for"></a><span data-ttu-id="e8434-152">Выход и продолжение для</span><span class="sxs-lookup"><span data-stu-id="e8434-152">Exit For and Continue For</span></span>

<span data-ttu-id="e8434-153">`Exit For`Оператор немедленно завершает работу `For` ...`Next`</span><span class="sxs-lookup"><span data-stu-id="e8434-153">The `Exit For` statement immediately exits the `For`…`Next`</span></span> <span data-ttu-id="e8434-154">выполняет цикл и передает управление оператору, который следует за `Next` оператором.</span><span class="sxs-lookup"><span data-stu-id="e8434-154">loop and transfers control to the statement that follows the `Next` statement.</span></span>

<span data-ttu-id="e8434-155">`Continue For`Оператор передает управление сразу в следующую итерацию цикла.</span><span class="sxs-lookup"><span data-stu-id="e8434-155">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span></span> <span data-ttu-id="e8434-156">Дополнительные сведения см. в разделе [оператор continue](continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e8434-156">For more information, see [Continue Statement](continue-statement.md).</span></span>

<span data-ttu-id="e8434-157">В следующем примере показано использование `Continue For` `Exit For` операторов и.</span><span class="sxs-lookup"><span data-stu-id="e8434-157">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span></span>

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

<span data-ttu-id="e8434-158">Можно разместить любое количество `Exit For` операторов в `For` ...`Next`</span><span class="sxs-lookup"><span data-stu-id="e8434-158">You can put any number of `Exit For` statements in a `For`…`Next`</span></span> <span data-ttu-id="e8434-159">повторить.</span><span class="sxs-lookup"><span data-stu-id="e8434-159">loop.</span></span> <span data-ttu-id="e8434-160">При использовании внутри вложенного `For` ...`Next`</span><span class="sxs-lookup"><span data-stu-id="e8434-160">When used within nested `For`…`Next`</span></span> <span data-ttu-id="e8434-161">выполняет цикл, `Exit For` выходит из внутреннего цикла и передает управление следующему более высокому уровню вложенности.</span><span class="sxs-lookup"><span data-stu-id="e8434-161">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

<span data-ttu-id="e8434-162">`Exit For` часто используется после вычисления некоторого условия (например, в `If` ... `Then` ...`Else` структура).</span><span class="sxs-lookup"><span data-stu-id="e8434-162">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span></span> <span data-ttu-id="e8434-163">Может потребоваться использовать `Exit For` для следующих условий:</span><span class="sxs-lookup"><span data-stu-id="e8434-163">You might want to use `Exit For` for the following conditions:</span></span>

- <span data-ttu-id="e8434-164">Продолжение итерации не требуется или невозможно.</span><span class="sxs-lookup"><span data-stu-id="e8434-164">Continuing to iterate is unnecessary or impossible.</span></span> <span data-ttu-id="e8434-165">Это условие может быть создано с помощью ошибочного значения или запроса на завершение.</span><span class="sxs-lookup"><span data-stu-id="e8434-165">An erroneous value or a termination request might create this condition.</span></span>

- <span data-ttu-id="e8434-166">А.. `Try` . `Catch` ...`Finally` перехватывает исключение.</span><span class="sxs-lookup"><span data-stu-id="e8434-166">A `Try`...`Catch`...`Finally` statement catches an exception.</span></span> <span data-ttu-id="e8434-167">`Exit For`В конце блока можно использовать `Finally` .</span><span class="sxs-lookup"><span data-stu-id="e8434-167">You might use `Exit For` at the end of the `Finally` block.</span></span>

- <span data-ttu-id="e8434-168">У вас есть бесконечный цикл, который может выполняться с большим или даже бесконечным числом раз.</span><span class="sxs-lookup"><span data-stu-id="e8434-168">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="e8434-169">При обнаружении такого условия можно использовать `Exit For` для экранирования цикла.</span><span class="sxs-lookup"><span data-stu-id="e8434-169">If you detect such a condition, you can use `Exit For` to escape the loop.</span></span> <span data-ttu-id="e8434-170">Дополнительные сведения см. в разделе [Do... Loop, инструкция](do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e8434-170">For more information, see [Do...Loop Statement](do-loop-statement.md).</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="e8434-171">Техническая реализация</span><span class="sxs-lookup"><span data-stu-id="e8434-171">Technical Implementation</span></span>

<span data-ttu-id="e8434-172">При `For` запуске цикла... `Next` Visual Basic вычисляет `start` , `end` и `step` .</span><span class="sxs-lookup"><span data-stu-id="e8434-172">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span></span> <span data-ttu-id="e8434-173">Visual Basic вычисляет эти значения только в данный момент, а затем присваивает значение `start` `counter` .</span><span class="sxs-lookup"><span data-stu-id="e8434-173">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span></span> <span data-ttu-id="e8434-174">Перед выполнением блока операторов Visual Basic сравнивается `counter` с `end` .</span><span class="sxs-lookup"><span data-stu-id="e8434-174">Before the statement block runs, Visual Basic compares `counter` to `end`.</span></span> <span data-ttu-id="e8434-175">Если `counter` уже больше `end` значения (или меньше `step` , если имеет отрицательное значение), `For` цикл завершается, и управление передается оператору, следующему за `Next` оператором.</span><span class="sxs-lookup"><span data-stu-id="e8434-175">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span></span> <span data-ttu-id="e8434-176">В противном случае выполняется блок операторов.</span><span class="sxs-lookup"><span data-stu-id="e8434-176">Otherwise, the statement block runs.</span></span>

<span data-ttu-id="e8434-177">Каждый раз, когда Visual Basic обнаруживает `Next` оператор, он увеличивается на `counter` `step` и возвращается в `For` оператор.</span><span class="sxs-lookup"><span data-stu-id="e8434-177">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span></span> <span data-ttu-id="e8434-178">Затем он сравнивает `counter` с `end` и снова либо выполняет блок, либо выходит из цикла, в зависимости от результата.</span><span class="sxs-lookup"><span data-stu-id="e8434-178">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span></span> <span data-ttu-id="e8434-179">Этот процесс выполняется до тех пор `counter` , пока не будет пройден `end` или `Exit For` не встретится оператор.</span><span class="sxs-lookup"><span data-stu-id="e8434-179">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span></span>

<span data-ttu-id="e8434-180">Цикл не останавливается, пока не будет `counter` пройден `end` .</span><span class="sxs-lookup"><span data-stu-id="e8434-180">The loop doesn't stop until `counter` has passed `end`.</span></span> <span data-ttu-id="e8434-181">Если `counter` равно `end` , цикл продолжится.</span><span class="sxs-lookup"><span data-stu-id="e8434-181">If `counter` is equal to `end`, the loop continues.</span></span> <span data-ttu-id="e8434-182">Сравнение, которое определяет, следует ли запускать блок, `counter`  <=  `end` Если `step` является положительным и `counter`  >=  `end` `step` отрицательным.</span><span class="sxs-lookup"><span data-stu-id="e8434-182">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span></span>

<span data-ttu-id="e8434-183">Если изменить значение `counter` во время цикла, код может оказаться труднее для чтения и отладки.</span><span class="sxs-lookup"><span data-stu-id="e8434-183">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span></span> <span data-ttu-id="e8434-184">Изменение значения `start` , `end` или `step` не влияет на значения итерации, которые были определены при первом входе в цикл.</span><span class="sxs-lookup"><span data-stu-id="e8434-184">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span></span>

<span data-ttu-id="e8434-185">При вложении циклов компилятор сообщает об ошибке, если обнаруживает `Next` оператор внешнего уровня вложенности перед `Next` инструкцией внутреннего уровня.</span><span class="sxs-lookup"><span data-stu-id="e8434-185">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span></span> <span data-ttu-id="e8434-186">Однако компилятор может обнаружить эту перекрытие ошибки только в том случае, если указать `counter` в каждой `Next` инструкции.</span><span class="sxs-lookup"><span data-stu-id="e8434-186">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span></span>

### <a name="step-argument"></a><span data-ttu-id="e8434-187">Аргумент Step</span><span class="sxs-lookup"><span data-stu-id="e8434-187">Step Argument</span></span>

<span data-ttu-id="e8434-188">Значение `step` может быть либо положительным, либо отрицательным.</span><span class="sxs-lookup"><span data-stu-id="e8434-188">The value of `step` can be either positive or negative.</span></span> <span data-ttu-id="e8434-189">Этот параметр определяет обработку цикла в соответствии со следующей таблицей.</span><span class="sxs-lookup"><span data-stu-id="e8434-189">This parameter determines loop processing according to the following table:</span></span>

|<span data-ttu-id="e8434-190">**Значение шага**</span><span class="sxs-lookup"><span data-stu-id="e8434-190">**Step value**</span></span>|<span data-ttu-id="e8434-191">**Цикл выполняется, если**</span><span class="sxs-lookup"><span data-stu-id="e8434-191">**Loop executes if**</span></span>|
|--------------------|--------------------------|
|<span data-ttu-id="e8434-192">Положительный или нулевой</span><span class="sxs-lookup"><span data-stu-id="e8434-192">Positive or zero</span></span>|`counter` <= `end`|
|<span data-ttu-id="e8434-193">Отрицательное число</span><span class="sxs-lookup"><span data-stu-id="e8434-193">Negative</span></span>|`counter` >= `end`|

<span data-ttu-id="e8434-194">Значение `step` по умолчанию — 1.</span><span class="sxs-lookup"><span data-stu-id="e8434-194">The default value of `step` is 1.</span></span>

### <a name="counter-argument"></a><a name="BKMK_Counter"></a> <span data-ttu-id="e8434-195">Аргумент счетчика</span><span class="sxs-lookup"><span data-stu-id="e8434-195">Counter Argument</span></span>

<span data-ttu-id="e8434-196">В следующей таблице показано `counter` , определяет ли новая локальная переменная, областью действия которой является весь `For…Next` цикл.</span><span class="sxs-lookup"><span data-stu-id="e8434-196">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span></span> <span data-ttu-id="e8434-197">Это определение зависит от того, существует ли оно `datatype` и `counter` уже определено ли оно.</span><span class="sxs-lookup"><span data-stu-id="e8434-197">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span></span>

|<span data-ttu-id="e8434-198">`datatype`Имеется?</span><span class="sxs-lookup"><span data-stu-id="e8434-198">Is `datatype` present?</span></span>|<span data-ttu-id="e8434-199">`counter`Уже определено?</span><span class="sxs-lookup"><span data-stu-id="e8434-199">Is `counter` already defined?</span></span>|<span data-ttu-id="e8434-200">Результат ( `counter` определяет, определена ли новая локальная переменная в пределах всего `For...Next` цикла)</span><span class="sxs-lookup"><span data-stu-id="e8434-200">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span></span>|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="e8434-201">Нет</span><span class="sxs-lookup"><span data-stu-id="e8434-201">No</span></span>|<span data-ttu-id="e8434-202">Да</span><span class="sxs-lookup"><span data-stu-id="e8434-202">Yes</span></span>|<span data-ttu-id="e8434-203">Нет, так как `counter` уже определено.</span><span class="sxs-lookup"><span data-stu-id="e8434-203">No, because `counter` is already defined.</span></span> <span data-ttu-id="e8434-204">Если область действия `counter` не является локальной для процедуры, возникает предупреждение во время компиляции.</span><span class="sxs-lookup"><span data-stu-id="e8434-204">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span></span>|
|<span data-ttu-id="e8434-205">Нет</span><span class="sxs-lookup"><span data-stu-id="e8434-205">No</span></span>|<span data-ttu-id="e8434-206">Нет</span><span class="sxs-lookup"><span data-stu-id="e8434-206">No</span></span>|<span data-ttu-id="e8434-207">Да.</span><span class="sxs-lookup"><span data-stu-id="e8434-207">Yes.</span></span> <span data-ttu-id="e8434-208">Тип данных выводится из `start` `end` выражений, и `step` .</span><span class="sxs-lookup"><span data-stu-id="e8434-208">The data type is inferred from the `start`, `end`, and `step` expressions.</span></span> <span data-ttu-id="e8434-209">Дополнительные сведения о выводе типа см. в разделе [Option Infer](option-infer-statement.md) и [определение локального типа](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="e8434-209">For information about type inference, see [Option Infer Statement](option-infer-statement.md) and [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>|
|<span data-ttu-id="e8434-210">Да</span><span class="sxs-lookup"><span data-stu-id="e8434-210">Yes</span></span>|<span data-ttu-id="e8434-211">Да</span><span class="sxs-lookup"><span data-stu-id="e8434-211">Yes</span></span>|<span data-ttu-id="e8434-212">Да, но только в том случае, если существующая `counter` переменная определена за пределами процедуры.</span><span class="sxs-lookup"><span data-stu-id="e8434-212">Yes, but only if the existing `counter` variable is defined outside the procedure.</span></span> <span data-ttu-id="e8434-213">Эта переменная остается отдельной.</span><span class="sxs-lookup"><span data-stu-id="e8434-213">That variable remains separate.</span></span> <span data-ttu-id="e8434-214">Если область существующей `counter` переменной является локальной для процедуры, возникает ошибка времени компиляции.</span><span class="sxs-lookup"><span data-stu-id="e8434-214">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span></span>|
|<span data-ttu-id="e8434-215">Да</span><span class="sxs-lookup"><span data-stu-id="e8434-215">Yes</span></span>|<span data-ttu-id="e8434-216">Нет</span><span class="sxs-lookup"><span data-stu-id="e8434-216">No</span></span>|<span data-ttu-id="e8434-217">Да.</span><span class="sxs-lookup"><span data-stu-id="e8434-217">Yes.</span></span>|

<span data-ttu-id="e8434-218">Тип данных параметра `counter` определяет тип итерации, который должен быть одним из следующих типов:</span><span class="sxs-lookup"><span data-stu-id="e8434-218">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span></span>

- <span data-ttu-id="e8434-219">A `Byte` , `SByte` , `UShort` , `Short` , `UInteger` , `Integer` , `ULong` , `Long` , `Decimal` , `Single` или `Double` .</span><span class="sxs-lookup"><span data-stu-id="e8434-219">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span></span>

- <span data-ttu-id="e8434-220">Перечисление, объявляемое с помощью [инструкции enum](enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e8434-220">An enumeration that you declare by using an [Enum Statement](enum-statement.md).</span></span>

- <span data-ttu-id="e8434-221">Объект `Object`.</span><span class="sxs-lookup"><span data-stu-id="e8434-221">An `Object`.</span></span>

- <span data-ttu-id="e8434-222">Тип `T` , имеющий следующие операторы, где `B` — это тип, который можно использовать в `Boolean` выражении.</span><span class="sxs-lookup"><span data-stu-id="e8434-222">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span></span>

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

<span data-ttu-id="e8434-223">При необходимости можно указать `counter` переменную в `Next` инструкции.</span><span class="sxs-lookup"><span data-stu-id="e8434-223">You can optionally specify the `counter` variable in the `Next` statement.</span></span> <span data-ttu-id="e8434-224">Этот синтаксис повышает удобочитаемость программы, особенно при наличии вложенных `For` циклов.</span><span class="sxs-lookup"><span data-stu-id="e8434-224">This syntax improves the readability of your program, especially if you have nested `For` loops.</span></span> <span data-ttu-id="e8434-225">Необходимо указать переменную, которая отображается в соответствующем `For` операторе.</span><span class="sxs-lookup"><span data-stu-id="e8434-225">You must specify the variable that appears in the corresponding `For` statement.</span></span>

<span data-ttu-id="e8434-226">`start`Выражения, `end` и `step` могут иметь любой тип данных, который расширяется до типа `counter` .</span><span class="sxs-lookup"><span data-stu-id="e8434-226">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span></span> <span data-ttu-id="e8434-227">При использовании определяемого пользователем типа для может потребоваться `counter` определить `CType` оператор преобразования для преобразования типов `start` , `end` или `step` в тип `counter` .</span><span class="sxs-lookup"><span data-stu-id="e8434-227">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span></span>

## <a name="example"></a><span data-ttu-id="e8434-228">Пример</span><span class="sxs-lookup"><span data-stu-id="e8434-228">Example</span></span>

<span data-ttu-id="e8434-229">В следующем примере удаляются все элементы из универсального списка.</span><span class="sxs-lookup"><span data-stu-id="e8434-229">The following example removes all elements from a generic list.</span></span> <span data-ttu-id="e8434-230">Вместо a [для каждого... Следующий оператор](for-each-next-statement.md). в примере показана `For` инструкция... `Next` , которая выполняет итерацию в убывающем порядке.</span><span class="sxs-lookup"><span data-stu-id="e8434-230">Instead of a [For Each...Next Statement](for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span></span> <span data-ttu-id="e8434-231">В этом примере используется этот метод `removeAt` , поскольку метод заставляет элементы после удаленного элемента иметь меньшее значение индекса.</span><span class="sxs-lookup"><span data-stu-id="e8434-231">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span></span>

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a><span data-ttu-id="e8434-232">Пример</span><span class="sxs-lookup"><span data-stu-id="e8434-232">Example</span></span>

<span data-ttu-id="e8434-233">В следующем примере перебирается перечисление, объявленное с помощью [инструкции enum](enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e8434-233">The following example iterates through an enumeration that's declared by using an [Enum Statement](enum-statement.md).</span></span>

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a><span data-ttu-id="e8434-234">Пример</span><span class="sxs-lookup"><span data-stu-id="e8434-234">Example</span></span>

<span data-ttu-id="e8434-235">В следующем примере параметры инструкции используют класс, который содержит перегрузки операторов для `+` операторов,, `-` `>=` и `<=` .</span><span class="sxs-lookup"><span data-stu-id="e8434-235">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span></span>

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a><span data-ttu-id="e8434-236">См. также</span><span class="sxs-lookup"><span data-stu-id="e8434-236">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="e8434-237">Циклические структуры</span><span class="sxs-lookup"><span data-stu-id="e8434-237">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="e8434-238">Оператор While…End While</span><span class="sxs-lookup"><span data-stu-id="e8434-238">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="e8434-239">Оператор Do…Loop</span><span class="sxs-lookup"><span data-stu-id="e8434-239">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="e8434-240">Вложенные структуры управления</span><span class="sxs-lookup"><span data-stu-id="e8434-240">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="e8434-241">Оператор Exit</span><span class="sxs-lookup"><span data-stu-id="e8434-241">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="e8434-242">Коллекции</span><span class="sxs-lookup"><span data-stu-id="e8434-242">Collections</span></span>](../../programming-guide/concepts/collections.md)
