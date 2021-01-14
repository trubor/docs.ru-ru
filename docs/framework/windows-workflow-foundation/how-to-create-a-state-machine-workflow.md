---
title: Практическое руководство. Создание рабочего процесса конечного автомата
description: В этой статье создается рабочий процесс, использующий как встроенные действия, такие как действие StateMachine, так и пользовательские действия.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 8e977a182d55143f8d877d61a0f0345bbe6bded4
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190472"
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="660c3-103">Практическое руководство. Создание рабочего процесса конечного автомата</span><span class="sxs-lookup"><span data-stu-id="660c3-103">How to: Create a State Machine Workflow</span></span>

<span data-ttu-id="660c3-104">Рабочие процессы могут создаваться как из встроенных, так и из пользовательских действий.</span><span class="sxs-lookup"><span data-stu-id="660c3-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="660c3-105">В этом разделе описывается создание рабочего процесса, который использует как встроенные действия, такие как <xref:System.Activities.Statements.StateMachine> действие, так и пользовательские действия из предыдущего раздела [инструкции. Создание действия](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="660c3-105">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="660c3-106">Рабочий процесс моделирует игру по угадыванию числа.</span><span class="sxs-lookup"><span data-stu-id="660c3-106">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="660c3-107">Каждый раздел в учебнике «Приступая к работе» построен на основе предыдущих разделов.</span><span class="sxs-lookup"><span data-stu-id="660c3-107">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="660c3-108">Для выполнения этой статьи сначала необходимо выполнить действия [по созданию действия](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="660c3-108">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="660c3-109">Создание рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="660c3-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="660c3-110">Щелкните правой кнопкой мыши **NumberGuessWorkflowActivities** в **Обозреватель решений** и выберите **добавить**, **новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="660c3-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="660c3-111">В узле **установленные** **Общие элементы** выберите **Рабочий процесс**.</span><span class="sxs-lookup"><span data-stu-id="660c3-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="660c3-112">В списке **Рабочий процесс** выберите пункт **Действие**.</span><span class="sxs-lookup"><span data-stu-id="660c3-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="660c3-113">Введите `StateMachineNumberGuessWorkflow` в поле **имя** и нажмите кнопку **добавить**.</span><span class="sxs-lookup"><span data-stu-id="660c3-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="660c3-114">Перетащите действие **StateMachine** из раздела **конечный автомат** на **панели элементов** и поместите его в метку **Перетащите сюда действие** в рабочей области конструктора рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="660c3-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="660c3-115">Создание переменных и аргументов рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="660c3-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="660c3-116">Дважды щелкните **StateMachineNumberGuessWorkflow. XAML** в **Обозреватель решений** , чтобы отобразить рабочий процесс в конструкторе, если он еще не отображается.</span><span class="sxs-lookup"><span data-stu-id="660c3-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="660c3-117">Щелкните **аргументы** в левой нижней части конструктора рабочих процессов, чтобы отобразить панель **аргументы** .</span><span class="sxs-lookup"><span data-stu-id="660c3-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="660c3-118">Нажмите кнопку **Создать аргумент**.</span><span class="sxs-lookup"><span data-stu-id="660c3-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="660c3-119">Введите в `MaxNumber` поле **имя** , выберите **в** раскрывающемся списке **направление** значение **Int32** , а затем нажмите клавишу ВВОД  , чтобы сохранить аргумент.</span><span class="sxs-lookup"><span data-stu-id="660c3-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="660c3-120">Нажмите кнопку **Создать аргумент**.</span><span class="sxs-lookup"><span data-stu-id="660c3-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="660c3-121">Введите `Turns` в поле **имя** , которое находится ниже вновь добавленного `MaxNumber` аргумента,  выберите из раскрывающегося списка **направление** , выберите **Int32** из раскрывающегося списка **тип аргумента** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="660c3-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="660c3-122">В левом нижнем углу конструктора действий нажмите кнопку **Аргументы**, чтобы закрыть панель **Аргументы**.</span><span class="sxs-lookup"><span data-stu-id="660c3-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="660c3-123">Щелкните **переменные** в левой нижней части конструктора рабочих процессов, чтобы отобразить панель **переменные** .</span><span class="sxs-lookup"><span data-stu-id="660c3-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="660c3-124">Нажмите кнопку **Создать переменную**.</span><span class="sxs-lookup"><span data-stu-id="660c3-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="660c3-125">Если поле **создать переменную** не отображается, щелкните <xref:System.Activities.Statements.StateMachine> действие в области конструктора рабочих процессов, чтобы выбрать его.</span><span class="sxs-lookup"><span data-stu-id="660c3-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="660c3-126">Введите `Guess` в поле **имя** , выберите **Int32** в раскрывающемся списке **тип переменной** и нажмите клавишу ВВОД, чтобы сохранить переменную.</span><span class="sxs-lookup"><span data-stu-id="660c3-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="660c3-127">Нажмите кнопку **Создать переменную**.</span><span class="sxs-lookup"><span data-stu-id="660c3-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="660c3-128">Введите `Target` в поле **имя** , выберите **Int32** в раскрывающемся списке **тип переменной** и нажмите клавишу ВВОД, чтобы сохранить переменную.</span><span class="sxs-lookup"><span data-stu-id="660c3-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="660c3-129">В левом нижнем углу конструктора действий нажмите кнопку **Переменные**, чтобы закрыть панель **Переменные**.</span><span class="sxs-lookup"><span data-stu-id="660c3-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="660c3-130">Добавление действий рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="660c3-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="660c3-131">Щелкните **State1** , чтобы выбрать его.</span><span class="sxs-lookup"><span data-stu-id="660c3-131">Click **State1** to select it.</span></span> <span data-ttu-id="660c3-132">В **окне Свойства** измените **DisplayName** на `Initialize Target` .</span><span class="sxs-lookup"><span data-stu-id="660c3-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="660c3-133">Если **окно Свойства** не отображается, в меню **вид** выберите пункт **окно свойств** .</span><span class="sxs-lookup"><span data-stu-id="660c3-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="660c3-134">Дважды щелкните только что переименованное **целевое состояние инициализации** в конструкторе рабочих процессов, чтобы развернуть его.</span><span class="sxs-lookup"><span data-stu-id="660c3-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3. <span data-ttu-id="660c3-135">Перетащите действие **Assign (назначение** ) из раздела **примитивы** на **панели элементов** и поместите его в раздел **Entry (запись** ) состояния.</span><span class="sxs-lookup"><span data-stu-id="660c3-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="660c3-136">Введите `Target` в поле **to** и следующее выражение в поле **введите выражение C#** или **введите выражение VB** .</span><span class="sxs-lookup"><span data-stu-id="660c3-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="660c3-137">Если окно **Панель элементов** не отображается, выберите пункт **Панель элементов** в меню **Вид**.</span><span class="sxs-lookup"><span data-stu-id="660c3-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4. <span data-ttu-id="660c3-138">Вернитесь к общему представлению конечного автомата в конструкторе рабочих процессов, щелкнув **StateMachine** в окне Навигатор в верхней части конструктора рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="660c3-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5. <span data-ttu-id="660c3-139">Перетащите действие **State** из раздела **конечный автомат** на **панели элементов** в конструктор рабочих процессов и наведите его на состояние **Инициализация целевого объекта** .</span><span class="sxs-lookup"><span data-stu-id="660c3-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="660c3-140">Обратите внимание, что рядом с целевым состоянием **инициализации** будут отображаться четыре треугольника, когда новое состояние находится над ним.</span><span class="sxs-lookup"><span data-stu-id="660c3-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="660c3-141">Удалите новое состояние на треугольнике, расположенном непосредственно под целевым состоянием **инициализации** .</span><span class="sxs-lookup"><span data-stu-id="660c3-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="660c3-142">Это помещает новое состояние в рабочий процесс и создает переход от целевого состояния **инициализации** к новому состоянию.</span><span class="sxs-lookup"><span data-stu-id="660c3-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6. <span data-ttu-id="660c3-143">Щелкните **State1** , чтобы выбрать его, измените **DisplayName** на `Enter Guess` , а затем дважды щелкните состояние в конструкторе рабочих процессов, чтобы развернуть его.</span><span class="sxs-lookup"><span data-stu-id="660c3-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7. <span data-ttu-id="660c3-144">Перетащите действие **WriteLine** из раздела **примитивы** **области элементов** и поместите его в раздел **запись** состояния.</span><span class="sxs-lookup"><span data-stu-id="660c3-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8. <span data-ttu-id="660c3-145">Введите следующее выражение в поле свойства **текст** для **WriteLine**.</span><span class="sxs-lookup"><span data-stu-id="660c3-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="660c3-146">Перетащите действие **Assign (назначение** ) из раздела **примитивы** на **панели элементов** и поместите в раздел **Exit** состояния.</span><span class="sxs-lookup"><span data-stu-id="660c3-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="660c3-147">Введите `Turns` в поле **Кому** и `Turns + 1` в поле **введите выражение C#** или **введите выражение VB** .</span><span class="sxs-lookup"><span data-stu-id="660c3-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="660c3-148">Вернитесь к общему представлению конечного автомата в конструкторе рабочих процессов, щелкнув **StateMachine** в окне Навигатор в верхней части конструктора рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="660c3-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="660c3-149">Перетащите действие **FinalState** из раздела **конечный автомат** на **панели элементов**, наведите его на пункт **Перейти** к состоянию вытягивания и поместите его на треугольник, расположенный справа от состояния « **Ввод** предположения», чтобы переход создавался между **вводом Guess** и **FinalState**.</span><span class="sxs-lookup"><span data-stu-id="660c3-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="660c3-150">По умолчанию используется имя перехода **T2**.</span><span class="sxs-lookup"><span data-stu-id="660c3-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="660c3-151">Щелкните переход в конструкторе рабочих процессов, чтобы выбрать его, и задайте для свойства **DisplayName** значение **верное**.</span><span class="sxs-lookup"><span data-stu-id="660c3-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="660c3-152">Затем щелкните и выберите **FinalState** и перетащите его вправо, чтобы место для полного перехода отображалось без переименования одного из двух состояний.</span><span class="sxs-lookup"><span data-stu-id="660c3-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="660c3-153">Это позволит упростить выполнение оставшихся действий в учебнике.</span><span class="sxs-lookup"><span data-stu-id="660c3-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="660c3-154">Дважды щелкните вновь переименованный **правильный** переход в конструкторе рабочих процессов, чтобы развернуть его.</span><span class="sxs-lookup"><span data-stu-id="660c3-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="660c3-155">Перетащите действие **ReadInt** из раздела **NumberGuessWorkflowActivities** на **панели элементов** и поместите его в раздел **Trigger** перехода.</span><span class="sxs-lookup"><span data-stu-id="660c3-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="660c3-156">В **окне Свойства** для действия **ReadInt** введите, `"EnterGuess"` включая кавычки, в поле значение свойства **BookmarkName** и введите `Guess` в поле значение свойства **результата** .</span><span class="sxs-lookup"><span data-stu-id="660c3-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="660c3-157">Введите следующее выражение в поле значение свойства **условия** **правильного** перехода.</span><span class="sxs-lookup"><span data-stu-id="660c3-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="660c3-158">Вернитесь к общему представлению конечного автомата в конструкторе рабочих процессов, щелкнув **StateMachine** в окне Навигатор в верхней части конструктора рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="660c3-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="660c3-159">Переход происходит при получении события триггера и оценке <xref:System.Activities.Statements.Transition.Condition%2A> значением `True` (если оно присутствует).</span><span class="sxs-lookup"><span data-stu-id="660c3-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="660c3-160">Для этого перехода, если пользователь `Guess` соответствует созданному случайным образом `Target` , управление передается в **FinalState** и завершает рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="660c3-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="660c3-161">В зависимости от того, верно ли предположение, Рабочий процесс должен перейти в **FinalState** или вернуться в состояние **подбора** для другой попытки.</span><span class="sxs-lookup"><span data-stu-id="660c3-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="660c3-162">Оба перехода используют один и тот же триггер ожидания получения предположения пользователя через действие **ReadInt** .</span><span class="sxs-lookup"><span data-stu-id="660c3-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="660c3-163">Это называется общим переходом.</span><span class="sxs-lookup"><span data-stu-id="660c3-163">This is called a shared transition.</span></span> <span data-ttu-id="660c3-164">Чтобы создать общий переход, щелкните окружность, указывающий начало правильного перехода с **предположения** , и перетащите его в нужное состояние.</span><span class="sxs-lookup"><span data-stu-id="660c3-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="660c3-165">В этом случае переход является самопереходом, поэтому перетащите начальную точку **правильного** перехода и поместите его обратно в нижнюю часть состояния « **Ввод предположения** ».</span><span class="sxs-lookup"><span data-stu-id="660c3-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="660c3-166">После создания перехода выберите его в конструкторе рабочих процессов и присвойте его  свойству DisplayName **неверное значение угадать**.</span><span class="sxs-lookup"><span data-stu-id="660c3-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="660c3-167">Общие переходы также можно создать в конструкторе переходов, щелкнув **Добавить общий переход триггера** в нижней части конструктора переходов, а затем выбрав нужное целевое состояние из раскрывающегося списка **Доступные состояния для подключения** .</span><span class="sxs-lookup"><span data-stu-id="660c3-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
    > [!NOTE]
    > <span data-ttu-id="660c3-168">Обратите внимание, что если состояние <xref:System.Activities.Statements.Transition.Condition%2A> перехода оценивается как `false` (или все условия общего перехода триггера оцениваются как `false`), переход не выполняется, а все триггеры для всех переходов из состояния будут запланированы заново.</span><span class="sxs-lookup"><span data-stu-id="660c3-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="660c3-169">В этом учебнике такая ситуация невозможна из-за способа настройки условий (имеются определенные действия для случая, если догадка верна или неверна).</span><span class="sxs-lookup"><span data-stu-id="660c3-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="660c3-170">Дважды щелкните **некорректный** переход в конструкторе рабочих процессов, чтобы развернуть его.</span><span class="sxs-lookup"><span data-stu-id="660c3-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="660c3-171">Обратите внимание, что для **триггера** уже задано то же действие **ReadInt** , которое было использовано в правильном переходе с **предположения** .</span><span class="sxs-lookup"><span data-stu-id="660c3-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="660c3-172">Введите следующее выражение в поле значение свойства **Condition** .</span><span class="sxs-lookup"><span data-stu-id="660c3-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="660c3-173">Перетащите действие **If** из раздела **поток управления** на **панели элементов** и поместите его в раздел Action ( **действие** ) перехода.</span><span class="sxs-lookup"><span data-stu-id="660c3-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="660c3-174">Введите следующее выражение в поле значение свойства **Condition** действия **If** .</span><span class="sxs-lookup"><span data-stu-id="660c3-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```text
    Guess < Target
    ```  
  
24. <span data-ttu-id="660c3-175">Перетащите два действия **WriteLine** из раздела **примитивы** на **панели элементов** и поместите их так, чтобы один из них находящегося в разделе **then** действия **If** , а другой — в разделе **else** .</span><span class="sxs-lookup"><span data-stu-id="660c3-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="660c3-176">Щелкните действие **WriteLine** в разделе **then (затем** ), чтобы выбрать его, и введите следующее выражение в поле значение свойства **текста** .</span><span class="sxs-lookup"><span data-stu-id="660c3-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="660c3-177">Щелкните действие **WriteLine** в разделе **else** , чтобы выбрать его, и введите следующее выражение в поле значение свойства **текста** .</span><span class="sxs-lookup"><span data-stu-id="660c3-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="660c3-178">Вернитесь к общему представлению конечного автомата в конструкторе рабочих процессов, щелкнув **StateMachine** в окне Навигатор в верхней части конструктора рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="660c3-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="660c3-179">В следующем примере показан завершенный рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="660c3-179">The following example illustrates the completed workflow.</span></span>  
  
     ![Иллюстрация, показывающая Завершенный рабочий процесс конечного автомата.](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="660c3-181">Построение рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="660c3-181">To build the workflow</span></span>  
  
1. <span data-ttu-id="660c3-182">Чтобы построить решение, нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="660c3-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="660c3-183">Инструкции по запуску рабочего процесса см. в следующем разделе [: запуск рабочего процесса](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="660c3-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="660c3-184">Если вы уже выполнили [инструкции](how-to-run-a-workflow.md) по выполнению этапа рабочего процесса с другим стилем рабочего процесса и хотите запустить его с помощью рабочего процесса конечного автомата из этого шага, перейдите к разделу [Создание и запуск приложения](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) , [посвященного запуску рабочего процесса](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="660c3-184">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="660c3-185">См. также</span><span class="sxs-lookup"><span data-stu-id="660c3-185">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="660c3-186">Программирование в Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="660c3-186">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="660c3-187">Разработка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="660c3-187">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="660c3-188">Учебник по началу работы</span><span class="sxs-lookup"><span data-stu-id="660c3-188">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="660c3-189">Практическое руководство. Создание действия</span><span class="sxs-lookup"><span data-stu-id="660c3-189">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="660c3-190">Практическое руководство. Запуск рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="660c3-190">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
