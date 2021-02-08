---
description: 'Дополнительные сведения о: Do... Оператор Loop (Visual Basic)'
title: Оператор Do…Loop
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: d170074c44d1692517f6b51abd4a6b3d005941c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795187"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="118fa-103">Оператор Do...Loop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="118fa-103">Do...Loop Statement (Visual Basic)</span></span>

<span data-ttu-id="118fa-104">Повторяет блок инструкций `Boolean` , пока условие находится `True` в состоянии или до тех пор, пока условие не станет `True` .</span><span class="sxs-lookup"><span data-stu-id="118fa-104">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="118fa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="118fa-105">Syntax</span></span>  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="118fa-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="118fa-106">Parts</span></span>  
  
|<span data-ttu-id="118fa-107">Термин</span><span class="sxs-lookup"><span data-stu-id="118fa-107">Term</span></span>|<span data-ttu-id="118fa-108">Определение</span><span class="sxs-lookup"><span data-stu-id="118fa-108">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="118fa-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="118fa-109">Required.</span></span> <span data-ttu-id="118fa-110">Запускает определение `Do` цикла.</span><span class="sxs-lookup"><span data-stu-id="118fa-110">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="118fa-111">Является обязательным, если используется параметр `Until`.</span><span class="sxs-lookup"><span data-stu-id="118fa-111">Required unless `Until` is used.</span></span> <span data-ttu-id="118fa-112">Повторите цикл, пока `condition` не будет `False` .</span><span class="sxs-lookup"><span data-stu-id="118fa-112">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="118fa-113">Является обязательным, если используется параметр `While`.</span><span class="sxs-lookup"><span data-stu-id="118fa-113">Required unless `While` is used.</span></span> <span data-ttu-id="118fa-114">Повторите цикл, пока `condition` не будет `True` .</span><span class="sxs-lookup"><span data-stu-id="118fa-114">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="118fa-115">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="118fa-115">Optional.</span></span> <span data-ttu-id="118fa-116">Выражение `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="118fa-116">`Boolean` expression.</span></span> <span data-ttu-id="118fa-117">Если `condition` имеет значение `Nothing` , Visual Basic обрабатывает его как `False` .</span><span class="sxs-lookup"><span data-stu-id="118fa-117">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="118fa-118">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="118fa-118">Optional.</span></span> <span data-ttu-id="118fa-119">Одна или несколько инструкций, повторяемых в, или до, `condition` имеют `True` .</span><span class="sxs-lookup"><span data-stu-id="118fa-119">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="118fa-120">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="118fa-120">Optional.</span></span> <span data-ttu-id="118fa-121">Передает управление следующей итерации `Do` цикла.</span><span class="sxs-lookup"><span data-stu-id="118fa-121">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="118fa-122">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="118fa-122">Optional.</span></span> <span data-ttu-id="118fa-123">Передает управление за пределы `Do` цикла.</span><span class="sxs-lookup"><span data-stu-id="118fa-123">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="118fa-124">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="118fa-124">Required.</span></span> <span data-ttu-id="118fa-125">Завершает определение `Do` цикла.</span><span class="sxs-lookup"><span data-stu-id="118fa-125">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="118fa-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="118fa-126">Remarks</span></span>  

 <span data-ttu-id="118fa-127">Используйте `Do...Loop` структуру, если нужно повторить набор инструкций неопределенное число раз, пока не будет удовлетворено условие.</span><span class="sxs-lookup"><span data-stu-id="118fa-127">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="118fa-128">Если нужно повторить инструкции заданное число раз, то [для... ](for-next-statement.md) Обычно лучше подходит следующий оператор.</span><span class="sxs-lookup"><span data-stu-id="118fa-128">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="118fa-129">Можно использовать либо `While` , либо `Until` , чтобы указать `condition` , но не оба.</span><span class="sxs-lookup"><span data-stu-id="118fa-129">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="118fa-130">Тест можно выполнять `condition` только один раз, в начале или в конце цикла.</span><span class="sxs-lookup"><span data-stu-id="118fa-130">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="118fa-131">Если проверка выполняется в `condition` начале цикла (в `Do` операторе), цикл может не выполняться даже один раз.</span><span class="sxs-lookup"><span data-stu-id="118fa-131">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="118fa-132">Если протестировать в конце цикла (в `Loop` операторе), цикл всегда выполняется по крайней мере один раз.</span><span class="sxs-lookup"><span data-stu-id="118fa-132">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="118fa-133">Условие обычно является результатом сравнения двух значений, но может быть любым выражением, результатом вычисления которого является [логическое значение типа данных](../data-types/boolean-data-type.md) ( `True` или `False` ).</span><span class="sxs-lookup"><span data-stu-id="118fa-133">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="118fa-134">Сюда относятся значения других типов данных, например числовые типы, которые были преобразованы в `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="118fa-134">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="118fa-135">Можно вложить `Do` циклы, поместив один цикл в другой.</span><span class="sxs-lookup"><span data-stu-id="118fa-135">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="118fa-136">Можно также вкладывать различные виды управляющих структур друг в друга.</span><span class="sxs-lookup"><span data-stu-id="118fa-136">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="118fa-137">Дополнительные сведения см. в разделе [вложенные структуры управления](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="118fa-137">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="118fa-138">Эта `Do...Loop` структура обеспечивает большую гибкость, чем [while... Оператор End While](while-end-while-statement.md) , так как он позволяет решить, следует ли завершать цикл при `condition` остановке `True` или при первом преобразовании `True` .</span><span class="sxs-lookup"><span data-stu-id="118fa-138">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="118fa-139">Он также позволяет тестироваться `condition` как в начале, так и в конце цикла.</span><span class="sxs-lookup"><span data-stu-id="118fa-139">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="118fa-140">Выйти</span><span class="sxs-lookup"><span data-stu-id="118fa-140">Exit Do</span></span>  

 <span data-ttu-id="118fa-141">Оператор [Exit Do](exit-statement.md) может предоставить альтернативный способ выхода из `Do…Loop` .</span><span class="sxs-lookup"><span data-stu-id="118fa-141">The [Exit Do](exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="118fa-142">`Exit Do` немедленно передает управление оператору, следующему за `Loop` оператором.</span><span class="sxs-lookup"><span data-stu-id="118fa-142">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="118fa-143">`Exit Do` часто используется после вычисления некоторого условия, например в `If...Then...Else` структуре.</span><span class="sxs-lookup"><span data-stu-id="118fa-143">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="118fa-144">Может потребоваться выйти из цикла, если обнаруживается условие, которое делает ненужным или невозможным продолжение итераций, например ошибочное значение или запрос на завершение.</span><span class="sxs-lookup"><span data-stu-id="118fa-144">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="118fa-145">Одно из них `Exit Do` — Проверка на наличие условия, которое может вызвать *бесконечный цикл*, то есть цикл, который может выполнять большое или даже бесконечное число раз.</span><span class="sxs-lookup"><span data-stu-id="118fa-145">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="118fa-146">`Exit Do`Для экранирования цикла можно использовать.</span><span class="sxs-lookup"><span data-stu-id="118fa-146">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="118fa-147">В можно включить любое количество `Exit Do` операторов в любом месте `Do…Loop` .</span><span class="sxs-lookup"><span data-stu-id="118fa-147">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="118fa-148">При использовании внутри вложенных `Do` циклов `Exit Do` передает управление за пределы самого внутреннего цикла и в следующий более высокий уровень вложенности.</span><span class="sxs-lookup"><span data-stu-id="118fa-148">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="118fa-149">Пример</span><span class="sxs-lookup"><span data-stu-id="118fa-149">Example</span></span>  

 <span data-ttu-id="118fa-150">В следующем примере операторы в цикле продолжают выполняться до тех пор, пока `index` переменная не будет больше 10.</span><span class="sxs-lookup"><span data-stu-id="118fa-150">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="118fa-151">`Until`Предложение находится в конце цикла.</span><span class="sxs-lookup"><span data-stu-id="118fa-151">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="118fa-152">Пример</span><span class="sxs-lookup"><span data-stu-id="118fa-152">Example</span></span>  

 <span data-ttu-id="118fa-153">В следующем примере `While` вместо предложения используется предложение, которое `Until` `condition` проверяется в начале цикла, а не в конце.</span><span class="sxs-lookup"><span data-stu-id="118fa-153">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="118fa-154">Пример</span><span class="sxs-lookup"><span data-stu-id="118fa-154">Example</span></span>  

 <span data-ttu-id="118fa-155">В следующем примере `condition` останавливается цикл, если `index` переменная больше 100.</span><span class="sxs-lookup"><span data-stu-id="118fa-155">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="118fa-156">`If`Однако инструкция в цикле приводит к `Exit Do` остановке цикла, если переменная индекса больше 10.</span><span class="sxs-lookup"><span data-stu-id="118fa-156">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="118fa-157">Пример</span><span class="sxs-lookup"><span data-stu-id="118fa-157">Example</span></span>  

 <span data-ttu-id="118fa-158">В следующем примере считываются все строки в текстовом файле.</span><span class="sxs-lookup"><span data-stu-id="118fa-158">The following example reads all lines in a text file.</span></span> <span data-ttu-id="118fa-159"><xref:System.IO.File.OpenText%2A>Метод открывает файл и возвращает объект <xref:System.IO.StreamReader> , считывающий символы.</span><span class="sxs-lookup"><span data-stu-id="118fa-159">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="118fa-160">В `Do...Loop` условии <xref:System.IO.StreamReader.Peek%2A> метод `StreamReader` определяет наличие дополнительных символов.</span><span class="sxs-lookup"><span data-stu-id="118fa-160">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="118fa-161">См. также</span><span class="sxs-lookup"><span data-stu-id="118fa-161">See also</span></span>

- [<span data-ttu-id="118fa-162">Циклические структуры</span><span class="sxs-lookup"><span data-stu-id="118fa-162">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="118fa-163">Оператор For…Next</span><span class="sxs-lookup"><span data-stu-id="118fa-163">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="118fa-164">Логический тип данных</span><span class="sxs-lookup"><span data-stu-id="118fa-164">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="118fa-165">Вложенные структуры управления</span><span class="sxs-lookup"><span data-stu-id="118fa-165">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="118fa-166">Оператор Exit</span><span class="sxs-lookup"><span data-stu-id="118fa-166">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="118fa-167">Оператор While…End While</span><span class="sxs-lookup"><span data-stu-id="118fa-167">While...End While Statement</span></span>](while-end-while-statement.md)
