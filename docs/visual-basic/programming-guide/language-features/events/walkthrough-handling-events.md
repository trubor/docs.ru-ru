---
description: Дополнительные сведения см. в разделе Пошаговое руководство. Обработка событий (Visual Basic)
title: Обработка событий
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 5101bd2287c81e03efb69b398d6cc961d3e6d9dc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436180"
---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="11cc0-103">Пошаговое руководство. Обработка событий (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11cc0-103">Walkthrough: Handling Events (Visual Basic)</span></span>

<span data-ttu-id="11cc0-104">Это второй из двух разделов, демонстрирующих работу с событиями.</span><span class="sxs-lookup"><span data-stu-id="11cc0-104">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="11cc0-105">В первом разделе [Пошаговое руководство. объявление и создание событий](walkthrough-declaring-and-raising-events.md)показано, как объявлять и создавать события.</span><span class="sxs-lookup"><span data-stu-id="11cc0-105">The first topic, [Walkthrough: Declaring and Raising Events](walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="11cc0-106">В этом разделе используется форма и класс из этого пошагового руководства, чтобы продемонстрировать, как обрабатывались события, когда они выполняются.</span><span class="sxs-lookup"><span data-stu-id="11cc0-106">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="11cc0-107">В `Widget` примере класса используются традиционные инструкции по обработке событий.</span><span class="sxs-lookup"><span data-stu-id="11cc0-107">The `Widget` class example uses traditional event-handling statements.</span></span> <span data-ttu-id="11cc0-108">Visual Basic предоставляет другие методы для работы с событиями.</span><span class="sxs-lookup"><span data-stu-id="11cc0-108">Visual Basic provides other techniques for working with events.</span></span> <span data-ttu-id="11cc0-109">В качестве упражнения можно изменить этот пример для использования `AddHandler` `Handles` инструкций и.</span><span class="sxs-lookup"><span data-stu-id="11cc0-109">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="11cc0-110">Для управления событием PercentDone класса Widget</span><span class="sxs-lookup"><span data-stu-id="11cc0-110">To handle the PercentDone event of the Widget class</span></span>  
  
1. <span data-ttu-id="11cc0-111">Поместите следующий код в `Form1` :</span><span class="sxs-lookup"><span data-stu-id="11cc0-111">Place the following code in `Form1`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     <span data-ttu-id="11cc0-112">`WithEvents`Ключевое слово указывает, что переменная `mWidget` используется для управления событиями объекта.</span><span class="sxs-lookup"><span data-stu-id="11cc0-112">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="11cc0-113">Тип объекта указывается путем указания имени класса, из которого будет создан объект.</span><span class="sxs-lookup"><span data-stu-id="11cc0-113">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="11cc0-114">Переменная `mWidget` объявлена в, `Form1` поскольку `WithEvents` переменные должны быть уровня класса.</span><span class="sxs-lookup"><span data-stu-id="11cc0-114">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="11cc0-115">Это справедливо независимо от типа класса, в котором они размещены.</span><span class="sxs-lookup"><span data-stu-id="11cc0-115">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="11cc0-116">Переменная `mblnCancel` используется для отмены `LongTask` метода.</span><span class="sxs-lookup"><span data-stu-id="11cc0-116">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="11cc0-117">Написание кода для обработчика события</span><span class="sxs-lookup"><span data-stu-id="11cc0-117">Writing Code to Handle an Event</span></span>  

 <span data-ttu-id="11cc0-118">Как только вы объявили переменную с помощью `WithEvents` , имя переменной отображается в левом раскрывающемся списке **редактора кода** класса.</span><span class="sxs-lookup"><span data-stu-id="11cc0-118">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="11cc0-119">При выборе в `mWidget` правом раскрывающемся `Widget` списке отображаются события класса.</span><span class="sxs-lookup"><span data-stu-id="11cc0-119">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="11cc0-120">При выборе события отображается соответствующая процедура события с префиксом `mWidget` и символом подчеркивания.</span><span class="sxs-lookup"><span data-stu-id="11cc0-120">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="11cc0-121">Всем процедурам события, связанным с `WithEvents` переменной, присваивается имя переменной в виде префикса.</span><span class="sxs-lookup"><span data-stu-id="11cc0-121">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="11cc0-122">Чтобы обработать событие</span><span class="sxs-lookup"><span data-stu-id="11cc0-122">To handle an event</span></span>  
  
1. <span data-ttu-id="11cc0-123">Выберите `mWidget` из левого раскрывающегося списка в **редакторе кода**.</span><span class="sxs-lookup"><span data-stu-id="11cc0-123">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2. <span data-ttu-id="11cc0-124">Выберите `PercentDone` событие из правого раскрывающегося списка.</span><span class="sxs-lookup"><span data-stu-id="11cc0-124">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="11cc0-125">**Редактор кода** открывает `mWidget_PercentDone` процедуру события.</span><span class="sxs-lookup"><span data-stu-id="11cc0-125">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="11cc0-126">**Редактор кода** удобен, но не является обязательным для вставки новых обработчиков событий.</span><span class="sxs-lookup"><span data-stu-id="11cc0-126">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="11cc0-127">В этом пошаговом руководстве более прямым просто скопировать обработчики событий непосредственно в код.</span><span class="sxs-lookup"><span data-stu-id="11cc0-127">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3. <span data-ttu-id="11cc0-128">Добавьте следующий код в обработчик событий `mWidget_PercentDone` .</span><span class="sxs-lookup"><span data-stu-id="11cc0-128">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     <span data-ttu-id="11cc0-129">При каждом `PercentDone` возникновении события процедура события отображает процент завершения в `Label` элементе управления.</span><span class="sxs-lookup"><span data-stu-id="11cc0-129">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="11cc0-130">`DoEvents`Метод позволяет перекрасить метку, а также дает пользователю возможность нажать кнопку **Отмена** .</span><span class="sxs-lookup"><span data-stu-id="11cc0-130">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="11cc0-131">Добавьте следующий код для `Button2_Click` обработчика событий:</span><span class="sxs-lookup"><span data-stu-id="11cc0-131">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 <span data-ttu-id="11cc0-132">Если пользователь нажимает кнопку **Отмена** во время `LongTask` выполнения, `Button2_Click` событие выполняется сразу же после того, как `DoEvents` инструкция допускает обработку события.</span><span class="sxs-lookup"><span data-stu-id="11cc0-132">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="11cc0-133">Переменной уровня класса присваивается `mblnCancel` значение `True` , а `mWidget_PercentDone` затем событие проверяется и присваивает `ByRef Cancel` аргументу значение `True` .</span><span class="sxs-lookup"><span data-stu-id="11cc0-133">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="11cc0-134">Подключение переменной WithEvents к объекту</span><span class="sxs-lookup"><span data-stu-id="11cc0-134">Connecting a WithEvents Variable to an Object</span></span>  

 <span data-ttu-id="11cc0-135">`Form1` теперь настроен на обработку `Widget` событий объекта.</span><span class="sxs-lookup"><span data-stu-id="11cc0-135">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="11cc0-136">Все, что остается, — найти `Widget` кое-что.</span><span class="sxs-lookup"><span data-stu-id="11cc0-136">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="11cc0-137">При объявлении переменной `WithEvents` во время разработки объект не связан с ним.</span><span class="sxs-lookup"><span data-stu-id="11cc0-137">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="11cc0-138">Переменная аналогична `WithEvents` любой другой объектной переменной.</span><span class="sxs-lookup"><span data-stu-id="11cc0-138">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="11cc0-139">Необходимо создать объект и присвоить ему ссылку на `WithEvents` переменную.</span><span class="sxs-lookup"><span data-stu-id="11cc0-139">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="11cc0-140">Создание объекта и присвоение ему ссылки</span><span class="sxs-lookup"><span data-stu-id="11cc0-140">To create an object and assign a reference to it</span></span>  
  
1. <span data-ttu-id="11cc0-141">Выберите **(события Form1)** в левом раскрывающемся списке в **редакторе кода**.</span><span class="sxs-lookup"><span data-stu-id="11cc0-141">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2. <span data-ttu-id="11cc0-142">Выберите `Load` событие из правого раскрывающегося списка.</span><span class="sxs-lookup"><span data-stu-id="11cc0-142">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="11cc0-143">**Редактор кода** открывает `Form1_Load` процедуру события.</span><span class="sxs-lookup"><span data-stu-id="11cc0-143">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3. <span data-ttu-id="11cc0-144">Добавьте следующий код для `Form1_Load` процедуры события, чтобы создать `Widget` :</span><span class="sxs-lookup"><span data-stu-id="11cc0-144">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 <span data-ttu-id="11cc0-145">При выполнении этого кода Visual Basic создает `Widget` объект и подключает его события к процедурам событий, связанным с `mWidget` .</span><span class="sxs-lookup"><span data-stu-id="11cc0-145">When this code executes, Visual Basic creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="11cc0-146">С этого момента каждый раз, когда `Widget` вызывает `PercentDone` событие, `mWidget_PercentDone` выполняется процедура события.</span><span class="sxs-lookup"><span data-stu-id="11cc0-146">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="11cc0-147">Вызов метода LongTask</span><span class="sxs-lookup"><span data-stu-id="11cc0-147">To call the LongTask method</span></span>  
  
- <span data-ttu-id="11cc0-148">Добавьте следующий код в обработчик событий `Button1_Click` .</span><span class="sxs-lookup"><span data-stu-id="11cc0-148">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 <span data-ttu-id="11cc0-149">Перед `LongTask` вызовом метода необходимо инициализировать метку, которая отображает процент завершения, а флаг уровня класса `Boolean` для отмены метода должен иметь значение `False` .</span><span class="sxs-lookup"><span data-stu-id="11cc0-149">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="11cc0-150">`LongTask` вызывается с длительностью задачи в 12,2 секунд.</span><span class="sxs-lookup"><span data-stu-id="11cc0-150">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="11cc0-151">`PercentDone`Событие вызывается раз в секунду с каждой третьей стороной.</span><span class="sxs-lookup"><span data-stu-id="11cc0-151">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="11cc0-152">При каждом возникновении события `mWidget_PercentDone` выполняется процедура события.</span><span class="sxs-lookup"><span data-stu-id="11cc0-152">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="11cc0-153">По `LongTask` завершении проверяется, `mblnCancel` `LongTask` завершилось ли нормальное завершение или остановлено, так как `mblnCancel` было установлено значение `True` .</span><span class="sxs-lookup"><span data-stu-id="11cc0-153">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="11cc0-154">Процент завершения обновляется только в первом случае.</span><span class="sxs-lookup"><span data-stu-id="11cc0-154">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="11cc0-155">Чтобы выполнить программу, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="11cc0-155">To run the program</span></span>  
  
1. <span data-ttu-id="11cc0-156">Нажмите клавишу F5, чтобы перевести проект в режим выполнения.</span><span class="sxs-lookup"><span data-stu-id="11cc0-156">Press F5 to put the project in run mode.</span></span>  
  
2. <span data-ttu-id="11cc0-157">Нажмите кнопку **запустить задачу** .</span><span class="sxs-lookup"><span data-stu-id="11cc0-157">Click the **Start Task** button.</span></span> <span data-ttu-id="11cc0-158">При каждом `PercentDone` возникновении события метка обновляется в процентах от завершенной задачи.</span><span class="sxs-lookup"><span data-stu-id="11cc0-158">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3. <span data-ttu-id="11cc0-159">Нажмите кнопку **Отмена** , чтобы остановить задачу.</span><span class="sxs-lookup"><span data-stu-id="11cc0-159">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="11cc0-160">Обратите внимание, что внешний вид кнопки **Отмена** не меняется сразу же после нажатия.</span><span class="sxs-lookup"><span data-stu-id="11cc0-160">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="11cc0-161">`Click`Событие не может произойти, пока `My.Application.DoEvents` инструкция не разрешит обработку событий.</span><span class="sxs-lookup"><span data-stu-id="11cc0-161">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="11cc0-162">`My.Application.DoEvents`Метод не обрабатывает события точно так же, как и форма.</span><span class="sxs-lookup"><span data-stu-id="11cc0-162">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="11cc0-163">Например, в этом пошаговом руководстве необходимо дважды нажать кнопку **Отмена** .</span><span class="sxs-lookup"><span data-stu-id="11cc0-163">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="11cc0-164">Чтобы форма могла напрямую управлять событиями, можно использовать многопоточность.</span><span class="sxs-lookup"><span data-stu-id="11cc0-164">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="11cc0-165">Дополнительные сведения см. в разделе [управляемые потоки](../../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="11cc0-165">For more information, see [Managed Threading](../../../../standard/threading/index.md).</span></span>
  
 <span data-ttu-id="11cc0-166">Может оказаться полезным запустить программу с помощью F11 и пошаговое выполнение кода.</span><span class="sxs-lookup"><span data-stu-id="11cc0-166">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="11cc0-167">Вы можете ясно видеть, как работает выполнение `LongTask` , а затем ненадолго `Form1` перезапускать каждый раз при `PercentDone` возникновении события.</span><span class="sxs-lookup"><span data-stu-id="11cc0-167">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="11cc0-168">Что произойдет, если при обратном выполнении кода `Form1` `LongTask` метод был вызван повторно?</span><span class="sxs-lookup"><span data-stu-id="11cc0-168">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="11cc0-169">В худшем случае может произойти переполнение стека, если `LongTask` вызывалось каждый раз при возникновении события.</span><span class="sxs-lookup"><span data-stu-id="11cc0-169">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="11cc0-170">Можно `mWidget` присвоить переменной обработку событий для другого `Widget` объекта, назначив ссылку на новый объект `Widget` в `mWidget` .</span><span class="sxs-lookup"><span data-stu-id="11cc0-170">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="11cc0-171">На самом деле код можно сделать при `Button1_Click` каждом нажатии кнопки.</span><span class="sxs-lookup"><span data-stu-id="11cc0-171">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="11cc0-172">Для управления событиями для другого мини-приложения</span><span class="sxs-lookup"><span data-stu-id="11cc0-172">To handle events for a different widget</span></span>  
  
- <span data-ttu-id="11cc0-173">Добавьте следующую строку кода в `Button1_Click` процедуру, непосредственно перед строкой, которая считывает `mWidget.LongTask(12.2, 0.33)` :</span><span class="sxs-lookup"><span data-stu-id="11cc0-173">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 <span data-ttu-id="11cc0-174">Приведенный выше код создает новый при `Widget` каждом нажатии кнопки.</span><span class="sxs-lookup"><span data-stu-id="11cc0-174">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="11cc0-175">Как только `LongTask` метод завершается, ссылка на `Widget` освобождается и `Widget` уничтожается.</span><span class="sxs-lookup"><span data-stu-id="11cc0-175">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="11cc0-176">`WithEvents`Переменная может содержать только одну ссылку на объект за раз, поэтому при присвоении другому объекту значения `Widget` `mWidget` `Widget` события предыдущего объекта больше не будут обрабатываться.</span><span class="sxs-lookup"><span data-stu-id="11cc0-176">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="11cc0-177">Если `mWidget` является единственной объектной переменной, содержащей ссылку на старую `Widget` , объект уничтожается.</span><span class="sxs-lookup"><span data-stu-id="11cc0-177">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="11cc0-178">Если требуется обрабатывать события из нескольких `Widget` объектов, используйте `AddHandler` инструкцию для обработки событий из каждого объекта отдельно.</span><span class="sxs-lookup"><span data-stu-id="11cc0-178">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11cc0-179">Можно объявить столько `WithEvents` переменных, сколько требуется, но массивы `WithEvents` переменных не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="11cc0-179">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11cc0-180">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="11cc0-180">See also</span></span>

- [<span data-ttu-id="11cc0-181">Пошаговое руководство. Объявление и вызов событий</span><span class="sxs-lookup"><span data-stu-id="11cc0-181">Walkthrough: Declaring and Raising Events</span></span>](walkthrough-declaring-and-raising-events.md)
- [<span data-ttu-id="11cc0-182">События</span><span class="sxs-lookup"><span data-stu-id="11cc0-182">Events</span></span>](index.md)
