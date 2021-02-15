---
description: 'Дополнительные сведения: структуры принятия решений (Visual Basic)'
title: Структуры решений
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: 76b63d2cdc238ec5590d11a6a802f55866990a3a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480691"
---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="33226-103">Структуры решений (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33226-103">Decision Structures (Visual Basic)</span></span>

<span data-ttu-id="33226-104">Visual Basic позволяет тестировать условия и выполнять различные операции в зависимости от результатов этого теста.</span><span class="sxs-lookup"><span data-stu-id="33226-104">Visual Basic lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="33226-105">Можно проверить наличие условия, которое имеет значение true или false, для различных значений выражения или для различных исключений, создаваемых при выполнении последовательности инструкций.</span><span class="sxs-lookup"><span data-stu-id="33226-105">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="33226-106">На следующем рисунке показана структура принятия решений, которая проверяет истинность условия и принимает различные действия в зависимости от того, имеет ли оно значение true или false.</span><span class="sxs-lookup"><span data-stu-id="33226-106">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 ![Блок-схема if... Затем... Else.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="33226-108">Если... Затем... Else, конструкция</span><span class="sxs-lookup"><span data-stu-id="33226-108">If...Then...Else Construction</span></span>  

 <span data-ttu-id="33226-109">`If...Then...Else` операторы позволяют проверить одно или несколько условий и выполнить одну или несколько инструкций в зависимости от каждого условия.</span><span class="sxs-lookup"><span data-stu-id="33226-109">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="33226-110">Проверить условия и выполнить действия можно следующими способами.</span><span class="sxs-lookup"><span data-stu-id="33226-110">You can test conditions and take actions in the following ways:</span></span>  
  
- <span data-ttu-id="33226-111">Выполнить одну или несколько инструкций, если условие `True`</span><span class="sxs-lookup"><span data-stu-id="33226-111">Run one or more statements if a condition is `True`</span></span>  
  
- <span data-ttu-id="33226-112">Выполнить одну или несколько инструкций, если условие `False`</span><span class="sxs-lookup"><span data-stu-id="33226-112">Run one or more statements if a condition is `False`</span></span>  
  
- <span data-ttu-id="33226-113">Запускать некоторые инструкции, если условие имеет значение `True` , а другие — `False`</span><span class="sxs-lookup"><span data-stu-id="33226-113">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
- <span data-ttu-id="33226-114">Проверить дополнительное условие, если предыдущие условия `False`</span><span class="sxs-lookup"><span data-stu-id="33226-114">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="33226-115">Структура элемента управления, которая предоставляет все эти возможности, — это [If... Затем... Else, инструкция](../../../language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="33226-115">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="33226-116">Можно использовать однострочную версию, если имеется только один тест и один оператор для выполнения.</span><span class="sxs-lookup"><span data-stu-id="33226-116">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="33226-117">При наличии более сложного набора условий и действий можно использовать версию из нескольких строк.</span><span class="sxs-lookup"><span data-stu-id="33226-117">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="33226-118">Выберите... Конструкция CASE</span><span class="sxs-lookup"><span data-stu-id="33226-118">Select...Case Construction</span></span>  

 <span data-ttu-id="33226-119">`Select...Case`Конструкция позволяет оценивать выражение один раз и выполнять разные наборы инструкций на основе различных возможных значений.</span><span class="sxs-lookup"><span data-stu-id="33226-119">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="33226-120">Дополнительные сведения см. в разделе [SELECT... Case, инструкция](../../../language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="33226-120">For more information, see [Select...Case Statement](../../../language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="33226-121">Попробуйте... Перехватить... Finally, создание</span><span class="sxs-lookup"><span data-stu-id="33226-121">Try...Catch...Finally Construction</span></span>  

 <span data-ttu-id="33226-122">`Try...Catch...Finally` операторы позволяют запускать набор инструкций в среде, сохраняющей управление, если какая-либо из инструкций вызывает исключение.</span><span class="sxs-lookup"><span data-stu-id="33226-122">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="33226-123">Для разных исключений можно выполнять различные действия.</span><span class="sxs-lookup"><span data-stu-id="33226-123">You can take different actions for different exceptions.</span></span> <span data-ttu-id="33226-124">При необходимости можно указать блок кода, который будет выполняться перед выходом из всей `Try...Catch...Finally` конструкции, независимо от того, что происходит.</span><span class="sxs-lookup"><span data-stu-id="33226-124">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="33226-125">Дополнительные сведения см. в разделе [Оператор Try...Catch...Finally](../../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="33226-125">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33226-126">Для многих структур управления при щелчке ключевого слова все ключевые слова в структуре выделяются.</span><span class="sxs-lookup"><span data-stu-id="33226-126">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="33226-127">Например, если щелкнуть `If` `If...Then...Else` конструкцию, `If` будут выделены все экземпляры,,, `Then` `ElseIf` `Else` и `End If` в конструкции.</span><span class="sxs-lookup"><span data-stu-id="33226-127">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="33226-128">Чтобы перейти к следующему или предыдущему выделенному ключевому слову, нажмите клавиши CTRL + SHIFT + стрелка вниз или CTRL + SHIFT + стрелка вверх.</span><span class="sxs-lookup"><span data-stu-id="33226-128">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33226-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="33226-129">See also</span></span>

- [<span data-ttu-id="33226-130">Поток управления</span><span class="sxs-lookup"><span data-stu-id="33226-130">Control Flow</span></span>](index.md)
- [<span data-ttu-id="33226-131">Циклические структуры</span><span class="sxs-lookup"><span data-stu-id="33226-131">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="33226-132">Другие структуры управления</span><span class="sxs-lookup"><span data-stu-id="33226-132">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="33226-133">Вложенные структуры управления</span><span class="sxs-lookup"><span data-stu-id="33226-133">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="33226-134">Оператор If</span><span class="sxs-lookup"><span data-stu-id="33226-134">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
