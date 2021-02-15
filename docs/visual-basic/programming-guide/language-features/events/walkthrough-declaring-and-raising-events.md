---
description: Дополнительные сведения см. в разделе Пошаговое руководство. объявление и вызов событий (Visual Basic)
title: Объявление и вызов событий
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 98e9d2eabd1ace06de9f8cc7931013093d864e7a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466384"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="24419-103">Пошаговое руководство. Объявление и создание событий (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24419-103">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>

<span data-ttu-id="24419-104">В этом пошаговом руководстве показано, как объявить и вызвать события для класса с именем `Widget` .</span><span class="sxs-lookup"><span data-stu-id="24419-104">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="24419-105">После выполнения этих действий может потребоваться прочитать сопутствующий раздел [Пошаговое руководство. Обработка событий](walkthrough-handling-events.md), в которой показано, как использовать события из `Widget` объектов для предоставления сведений о состоянии в приложении.</span><span class="sxs-lookup"><span data-stu-id="24419-105">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="24419-106">Класс Widget</span><span class="sxs-lookup"><span data-stu-id="24419-106">The Widget Class</span></span>  

 <span data-ttu-id="24419-107">Предположим, что в момент, когда у вас есть `Widget` класс.</span><span class="sxs-lookup"><span data-stu-id="24419-107">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="24419-108">В `Widget` классе есть метод, выполнение которого может занять много времени, и вы хотите, чтобы приложение могло поместить какой-либо индикатор завершения.</span><span class="sxs-lookup"><span data-stu-id="24419-108">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="24419-109">Конечно, можно сделать так, чтобы `Widget` объект отображал диалоговое окно «процент завершения», но в каждом проекте, где использовался этот класс, будет задержаться это диалоговое окно `Widget` .</span><span class="sxs-lookup"><span data-stu-id="24419-109">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="24419-110">Хорошим принципом проектирования объектов является предоставление приложению, использующему объект, обработку пользовательского интерфейса, если только цель объекта не заключается в управлении формой или диалоговым окном.</span><span class="sxs-lookup"><span data-stu-id="24419-110">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="24419-111">Целью `Widget` является выполнение других задач, поэтому лучше добавить `PercentDone` событие и позволить процедуре, вызывающей методы, обменять `Widget` это событие и отображать обновления состояния.</span><span class="sxs-lookup"><span data-stu-id="24419-111">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="24419-112">`PercentDone`Событие может также предоставлять механизм отмены задачи.</span><span class="sxs-lookup"><span data-stu-id="24419-112">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="24419-113">Создание примера кода для этого раздела</span><span class="sxs-lookup"><span data-stu-id="24419-113">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="24419-114">Откройте новый проект приложения Windows Visual Basic и создайте форму с именем `Form1` .</span><span class="sxs-lookup"><span data-stu-id="24419-114">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="24419-115">Добавьте две кнопки и метку в `Form1` .</span><span class="sxs-lookup"><span data-stu-id="24419-115">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="24419-116">Присвойте им имена, как показано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="24419-116">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="24419-117">Объект</span><span class="sxs-lookup"><span data-stu-id="24419-117">Object</span></span>|<span data-ttu-id="24419-118">Свойство.</span><span class="sxs-lookup"><span data-stu-id="24419-118">Property</span></span>|<span data-ttu-id="24419-119">Параметр</span><span class="sxs-lookup"><span data-stu-id="24419-119">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="24419-120">Задача запуска</span><span class="sxs-lookup"><span data-stu-id="24419-120">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="24419-121">Отменить</span><span class="sxs-lookup"><span data-stu-id="24419-121">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="24419-122">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="24419-122">`(Name)`, `Text`</span></span>|<span data-ttu-id="24419-123">Лблперцентдоне, 0</span><span class="sxs-lookup"><span data-stu-id="24419-123">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="24419-124">В меню **проект** выберите команду **Добавить класс** , чтобы добавить в проект класс с именем `Widget.vb` .</span><span class="sxs-lookup"><span data-stu-id="24419-124">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="24419-125">Объявление события для класса Widget</span><span class="sxs-lookup"><span data-stu-id="24419-125">To declare an event for the Widget class</span></span>  
  
- <span data-ttu-id="24419-126">Используйте `Event` ключевое слово для объявления события в `Widget` классе.</span><span class="sxs-lookup"><span data-stu-id="24419-126">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="24419-127">Обратите внимание, что событие может иметь `ByVal` `ByRef` аргументы и, как показано в описании `Widget` `PercentDone` события:</span><span class="sxs-lookup"><span data-stu-id="24419-127">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="24419-128">Когда вызывающий объект получает `PercentDone` событие, `Percent` аргумент содержит процент завершенной задачи.</span><span class="sxs-lookup"><span data-stu-id="24419-128">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="24419-129">`Cancel`Аргумент может иметь значение, чтобы `True` отменить метод, вызвавший событие.</span><span class="sxs-lookup"><span data-stu-id="24419-129">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24419-130">Аргументы событий можно объявлять так же, как аргументы процедур, со следующими исключениями: события не могут иметь `Optional` аргументы или `ParamArray` , а события не имеют возвращаемых значений.</span><span class="sxs-lookup"><span data-stu-id="24419-130">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="24419-131">`PercentDone`Событие вызывается `LongTask` методом `Widget` класса.</span><span class="sxs-lookup"><span data-stu-id="24419-131">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="24419-132">`LongTask` принимает два аргумента: продолжительность времени, в течение которого метод должен выполнять работу, и минимальный интервал времени до `LongTask` приостановки для вызова `PercentDone` события.</span><span class="sxs-lookup"><span data-stu-id="24419-132">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="24419-133">Вызов события PercentDone</span><span class="sxs-lookup"><span data-stu-id="24419-133">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="24419-134">Чтобы упростить доступ к `Timer` свойству, используемому этим классом, добавьте `Imports` оператор в верхнюю часть раздела объявлений модуля класса, над `Class Widget` оператором.</span><span class="sxs-lookup"><span data-stu-id="24419-134">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="24419-135">Добавьте в класс `Widget` приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="24419-135">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="24419-136">Когда приложение вызывает `LongTask` метод, `Widget` класс вызывает `PercentDone` событие каждые `MinimumInterval` секунды.</span><span class="sxs-lookup"><span data-stu-id="24419-136">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="24419-137">При возвращении события `LongTask` проверяет, `Cancel` был ли аргумент установлен в значение `True` .</span><span class="sxs-lookup"><span data-stu-id="24419-137">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="24419-138">Здесь требуется несколько отказов от ответственности.</span><span class="sxs-lookup"><span data-stu-id="24419-138">A few disclaimers are necessary here.</span></span> <span data-ttu-id="24419-139">Для простоты `LongTask` процедура предполагает, что вы заранее понимаете, сколько времени займет задача.</span><span class="sxs-lookup"><span data-stu-id="24419-139">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="24419-140">Это практически не так.</span><span class="sxs-lookup"><span data-stu-id="24419-140">This is almost never the case.</span></span> <span data-ttu-id="24419-141">Разделение задач на фрагменты даже размера может быть трудной задачей, и часто самое важное для пользователей — просто время, прошедшего до того, как получится, что что-то происходит.</span><span class="sxs-lookup"><span data-stu-id="24419-141">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="24419-142">Возможно, вы заметили другой изъян в этом примере.</span><span class="sxs-lookup"><span data-stu-id="24419-142">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="24419-143">`Timer`Свойство возвращает количество секунд, прошедших с полуночи, поэтому приложение зависает, если оно запускается непосредственно перед полуночью.</span><span class="sxs-lookup"><span data-stu-id="24419-143">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="24419-144">Более аккуратный подход к измерению времени приведет к рассмотрению таких условий, как, например, с точки зрения, или избежать их вообще, используя такие свойства, как `Now` .</span><span class="sxs-lookup"><span data-stu-id="24419-144">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="24419-145">Теперь, когда `Widget` класс может создавать события, можно перейти к следующему пошаговому руководству.</span><span class="sxs-lookup"><span data-stu-id="24419-145">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="24419-146">[Пошаговое руководство. Обработка событий](walkthrough-handling-events.md) демонстрирует использование `WithEvents` для связывания обработчика событий с `PercentDone` событием.</span><span class="sxs-lookup"><span data-stu-id="24419-146">[Walkthrough: Handling Events](walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24419-147">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="24419-147">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="24419-148">Пошаговое руководство. Обработка событий</span><span class="sxs-lookup"><span data-stu-id="24419-148">Walkthrough: Handling Events</span></span>](walkthrough-handling-events.md)
- [<span data-ttu-id="24419-149">События</span><span class="sxs-lookup"><span data-stu-id="24419-149">Events</span></span>](index.md)
