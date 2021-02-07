---
description: 'Дополнительные сведения: SELECT... Оператор Case (Visual Basic)'
title: Оператор Select…Case
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: 4f8edecd0a0b1afd59e182a372e308c3829a9b93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741137"
---
# <a name="selectcase-statement-visual-basic"></a><span data-ttu-id="9b7c6-103">Оператор Select...Case (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b7c6-103">Select...Case Statement (Visual Basic)</span></span>

<span data-ttu-id="9b7c6-104">Выполняет одну из нескольких групп инструкций в зависимости от значения выражения.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-104">Runs one of several groups of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b7c6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9b7c6-105">Syntax</span></span>  
  
```vb  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a><span data-ttu-id="9b7c6-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="9b7c6-106">Parts</span></span>  
  
|<span data-ttu-id="9b7c6-107">Термин</span><span class="sxs-lookup"><span data-stu-id="9b7c6-107">Term</span></span>|<span data-ttu-id="9b7c6-108">Определение</span><span class="sxs-lookup"><span data-stu-id="9b7c6-108">Definition</span></span>|  
|---|---|  
|`testexpression`|<span data-ttu-id="9b7c6-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-109">Required.</span></span> <span data-ttu-id="9b7c6-110">Выражение.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-110">Expression.</span></span> <span data-ttu-id="9b7c6-111">Необходимо вычислить до одного из простейших типов данных (,,,,,,,,,,,,,, `Boolean` `Byte` `Char` `Date` `Double` `Decimal` `Integer` `Long` `Object` `SByte` `Short` `Single` `String` `UInteger` `ULong` и `UShort` ).</span><span class="sxs-lookup"><span data-stu-id="9b7c6-111">Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).</span></span>|  
|`expressionlist`|<span data-ttu-id="9b7c6-112">Требуется в `Case` операторе.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-112">Required in a `Case` statement.</span></span> <span data-ttu-id="9b7c6-113">Список предложений выражений, представляющих значения соответствия для `testexpression` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-113">List of expression clauses representing match values for `testexpression`.</span></span> <span data-ttu-id="9b7c6-114">Несколько предложений выражений разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-114">Multiple expression clauses are separated by commas.</span></span> <span data-ttu-id="9b7c6-115">Каждое предложение может принимать одну из следующих форм:</span><span class="sxs-lookup"><span data-stu-id="9b7c6-115">Each clause can take one of the following forms:</span></span><br /><br /> <span data-ttu-id="9b7c6-116">-   *expression1* `To` *выражение2*</span><span class="sxs-lookup"><span data-stu-id="9b7c6-116">-   *expression1* `To` *expression2*</span></span><br /><span data-ttu-id="9b7c6-117">-[ `Is` ] *компарисоноператор* *выражение*</span><span class="sxs-lookup"><span data-stu-id="9b7c6-117">-   [ `Is` ] *comparisonoperator* *expression*</span></span><br /><span data-ttu-id="9b7c6-118">-   *выражение*</span><span class="sxs-lookup"><span data-stu-id="9b7c6-118">-   *expression*</span></span><br /><br /> <span data-ttu-id="9b7c6-119">Используйте `To` ключевое слово, чтобы указать границы диапазона значений соответствия для `testexpression` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-119">Use the `To` keyword to specify the boundaries of a range of match values for `testexpression`.</span></span> <span data-ttu-id="9b7c6-120">Значение `expression1` должно быть меньше или равно значению `expression2` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-120">The value of `expression1` must be less than or equal to the value of `expression2`.</span></span><br /><br /> <span data-ttu-id="9b7c6-121">Используйте `Is` ключевое слово с оператором сравнения ( `=` , `<>` ,,, `<` `<=` `>` или `>=` ), чтобы указать ограничение на значения сопоставления для `testexpression` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-121">Use the `Is` keyword with a comparison operator (`=`, `<>`, `<`, `<=`, `>`, or `>=`) to specify a restriction on the match values for `testexpression`.</span></span> <span data-ttu-id="9b7c6-122">Если `Is` ключевое слово не указано, оно автоматически вставляется перед *компарисоноператор*.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-122">If the `Is` keyword is not supplied, it is automatically inserted before *comparisonoperator*.</span></span><br /><br /> <span data-ttu-id="9b7c6-123">Форма, указывающая только `expression` , рассматривается как особый случай формы, `Is` где *компарисоноператор* — знак равенства ( `=` ).</span><span class="sxs-lookup"><span data-stu-id="9b7c6-123">The form specifying only `expression` is treated as a special case of the `Is` form where *comparisonoperator* is the equal sign (`=`).</span></span> <span data-ttu-id="9b7c6-124">Эта форма вычисляется как `testexpression`  =  `expression` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-124">This form is evaluated as `testexpression` = `expression`.</span></span><br /><br /> <span data-ttu-id="9b7c6-125">Выражения в `expressionlist` могут быть любого типа данных при условии, что они неявно преобразуются в тип, `testexpression` а подходящее значение `comparisonoperator` допустимо для двух типов, с которыми он используется.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-125">The expressions in `expressionlist` can be of any data type, provided they are implicitly convertible to the type of `testexpression` and the appropriate `comparisonoperator` is valid for the two types it is being used with.</span></span>|  
|`statements`|<span data-ttu-id="9b7c6-126">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-126">Optional.</span></span> <span data-ttu-id="9b7c6-127">Одна или несколько следующих инструкций `Case` , которые выполняются, если `testexpression` совпадают с любым предложением в `expressionlist` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-127">One or more statements following `Case` that run if `testexpression` matches any clause in `expressionlist`.</span></span>|  
|`elsestatements`|<span data-ttu-id="9b7c6-128">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-128">Optional.</span></span> <span data-ttu-id="9b7c6-129">Одна или несколько следующих инструкций `Case Else` , которые выполняются, если не `testexpression` соответствуют ни одному из предложений в `expressionlist` ни одной из `Case` инструкций.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-129">One or more statements following `Case Else` that run if `testexpression` does not match any clause in the `expressionlist` of any of the `Case` statements.</span></span>|  
|`End Select`|<span data-ttu-id="9b7c6-130">Завершает определение `Select` конструкции.... `Case`</span><span class="sxs-lookup"><span data-stu-id="9b7c6-130">Terminates the definition of the `Select`...`Case` construction.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b7c6-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="9b7c6-131">Remarks</span></span>  

 <span data-ttu-id="9b7c6-132">Если `testexpression` соответствует любому `Case` `expressionlist` предложению, инструкции, следующие за этим `Case` оператором, выполняются до следующей `Case` `Case Else` инструкции, или `End Select` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-132">If `testexpression` matches any `Case` `expressionlist` clause, the statements following that `Case` statement run up to the next `Case`, `Case Else`, or `End Select` statement.</span></span> <span data-ttu-id="9b7c6-133">Затем управление передается следующему оператору `End Select` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-133">Control then passes to the statement following `End Select`.</span></span> <span data-ttu-id="9b7c6-134">Если `testexpression` соответствует `expressionlist` предложению в более чем одном `Case` предложении, выполняются только инструкции, следующие за первым совпадением.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-134">If `testexpression` matches an `expressionlist` clause in more than one `Case` clause, only the statements following the first match run.</span></span>  
  
 <span data-ttu-id="9b7c6-135">`Case Else`Оператор используется для представления `elsestatements` для запуска, если между `testexpression` `expressionlist` предложением и в других инструкциях не найдено совпадений `Case` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-135">The `Case Else` statement is used to introduce the `elsestatements` to run if no match is found between the `testexpression` and an `expressionlist` clause in any of the other `Case` statements.</span></span> <span data-ttu-id="9b7c6-136">Хотя это и не является обязательным, рекомендуется иметь `Case Else` в конструкции оператор, `Select Case` обрабатывающий непредвиденные `testexpression` значения.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-136">Although not required, it is a good idea to have a `Case Else` statement in your `Select Case` construction to handle unforeseen `testexpression` values.</span></span> <span data-ttu-id="9b7c6-137">Если `Case` `expressionlist` предложение не совпадает `testexpression` и отсутствует `Case Else` оператор, управление передается оператору ниже `End Select` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-137">If no `Case` `expressionlist` clause matches `testexpression` and there is no `Case Else` statement, control passes to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="9b7c6-138">В каждом предложении можно использовать несколько выражений или диапазонов `Case` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-138">You can use multiple expressions or ranges in each `Case` clause.</span></span> <span data-ttu-id="9b7c6-139">Например, следующая строка допустима.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-139">For example, the following line is valid.</span></span>  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> <span data-ttu-id="9b7c6-140">`Is`Ключевое слово, используемое в `Case` `Case Else` операторах и, не совпадает с [оператором is](../operators/is-operator.md), который используется для сравнения ссылок на объекты.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-140">The `Is` keyword used in the `Case` and `Case Else` statements is not the same as the [Is Operator](../operators/is-operator.md), which is used for object reference comparison.</span></span>  
  
 <span data-ttu-id="9b7c6-141">Можно указать диапазоны и несколько выражений для символьных строк.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-141">You can specify ranges and multiple expressions for character strings.</span></span> <span data-ttu-id="9b7c6-142">В следующем примере `Case` соответствует любой строке, которая равна «яблоки», имеет значение между «гайкями» и «полный курс» в алфавитном порядке или содержит точно то же значение, что и текущее значение `testItem` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-142">In the following example, `Case` matches any string that is exactly equal to "apples", has a value between "nuts" and "soup" in alphabetical order, or contains the exact same value as the current value of `testItem`.</span></span>  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 <span data-ttu-id="9b7c6-143">Параметр `Option Compare` может влиять на сравнения строк.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-143">The setting of `Option Compare` can affect string comparisons.</span></span> <span data-ttu-id="9b7c6-144">В `Option Compare Text` строках «яблоки» и «яблоки» сравниваются как одинаковые, но в противном случае — `Option Compare Binary` нет.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-144">Under `Option Compare Text`, the strings "Apples" and "apples" compare as equal, but under `Option Compare Binary`, they do not.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b7c6-145">`Case`Оператор с несколькими предложениями может демонстрировать поведение, называемое *сокращенным вычислением*.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-145">A `Case` statement with multiple clauses can exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="9b7c6-146">Visual Basic вычисляет предложения слева направо, и если одно из них создает совпадение с `testexpression` , оставшиеся предложения не оцениваются.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-146">Visual Basic evaluates the clauses from left to right, and if one produces a match with `testexpression`, the remaining clauses are not evaluated.</span></span> <span data-ttu-id="9b7c6-147">Сокращенное вычисление может повысить производительность, но может привести к непредвиденным результатам, если ожидается вычисление каждого выражения в `expressionlist` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-147">Short-circuiting can improve performance, but it can produce unexpected results if you are expecting every expression in `expressionlist` to be evaluated.</span></span> <span data-ttu-id="9b7c6-148">Дополнительные сведения об сокращенном вычислении см. в разделе [логические выражения](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="9b7c6-148">For more information on short-circuiting, see [Boolean Expressions](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span></span>  
  
 <span data-ttu-id="9b7c6-149">Если код в `Case` `Case Else` блоке инструкций или не требует выполнения каких-либо инструкций в блоке, он может выйти из блока с помощью `Exit Select` инструкции.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-149">If the code within a `Case` or `Case Else` statement block does not need to run any more of the statements in the block, it can exit the block by using the `Exit Select` statement.</span></span> <span data-ttu-id="9b7c6-150">Это немедленно передает управление оператору, приведенному ниже `End Select` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-150">This transfers control immediately to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="9b7c6-151">`Select Case` конструкции могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-151">`Select Case` constructions can be nested.</span></span> <span data-ttu-id="9b7c6-152">Каждая вложенная `Select Case` конструкция должна иметь соответствующий `End Select` оператор и должна быть полностью заключена в один `Case` `Case Else` блок инструкций или внешней конструкции, `Select Case` внутри которой он вложен.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-152">Each nested `Select Case` construction must have a matching `End Select` statement and must be completely contained within a single `Case` or `Case Else` statement block of the outer `Select Case` construction within which it is nested.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b7c6-153">Пример</span><span class="sxs-lookup"><span data-stu-id="9b7c6-153">Example</span></span>  

 <span data-ttu-id="9b7c6-154">В следующем примере конструкция используется `Select Case` для записи строки, соответствующей значению переменной `number` .</span><span class="sxs-lookup"><span data-stu-id="9b7c6-154">The following example uses a `Select Case` construction to write a line corresponding to the value of the variable `number`.</span></span> <span data-ttu-id="9b7c6-155">Вторая `Case` инструкция содержит значение, совпадающее с текущим значением `number` , поэтому инструкция, записывающая "между 6 и 8 включительно", выполняется.</span><span class="sxs-lookup"><span data-stu-id="9b7c6-155">The second `Case` statement contains the value that matches the current value of `number`, so the statement that writes "Between 6 and 8, inclusive" runs.</span></span>  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a><span data-ttu-id="9b7c6-156">См. также</span><span class="sxs-lookup"><span data-stu-id="9b7c6-156">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [<span data-ttu-id="9b7c6-157">End, инструкция</span><span class="sxs-lookup"><span data-stu-id="9b7c6-157">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="9b7c6-158">Оператор If…Then…Else</span><span class="sxs-lookup"><span data-stu-id="9b7c6-158">If...Then...Else Statement</span></span>](if-then-else-statement.md)
- [<span data-ttu-id="9b7c6-159">Оператор Option Compare</span><span class="sxs-lookup"><span data-stu-id="9b7c6-159">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="9b7c6-160">Оператор Exit</span><span class="sxs-lookup"><span data-stu-id="9b7c6-160">Exit Statement</span></span>](exit-statement.md)
