---
title: Практическое руководство. Создание рабочего процесса c блок-схемой
description: В этой статье описывается создание рабочего процесса, который использует как встроенные действия, так и пользовательские действия из предыдущей статьи.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 185d7aea-68a6-4bd8-adde-45050f33170a
ms.openlocfilehash: eb30a3a21ffc4cffe64d2f5d0bc741728f1ea87d
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190485"
---
# <a name="how-to-create-a-flowchart-workflow"></a><span data-ttu-id="79d43-103">Практическое руководство. Создание рабочего процесса c блок-схемой</span><span class="sxs-lookup"><span data-stu-id="79d43-103">How to: Create a Flowchart Workflow</span></span>

<span data-ttu-id="79d43-104">Рабочие процессы могут создаваться как из встроенных, так и из пользовательских действий.</span><span class="sxs-lookup"><span data-stu-id="79d43-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="79d43-105">В этом разделе описывается создание рабочего процесса, который использует как встроенные действия, такие как <xref:System.Activities.Statements.Flowchart> действие, так и пользовательские действия из предыдущего раздела [инструкции. Создание действия](how-to-create-an-activity.md) .</span><span class="sxs-lookup"><span data-stu-id="79d43-105">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="79d43-106">Рабочий процесс моделирует игру по угадыванию числа.</span><span class="sxs-lookup"><span data-stu-id="79d43-106">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79d43-107">Каждый раздел в учебнике «Приступая к работе» построен на основе предыдущих разделов.</span><span class="sxs-lookup"><span data-stu-id="79d43-107">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="79d43-108">Для выполнения этой статьи сначала необходимо выполнить действия [по созданию действия](how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="79d43-108">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="79d43-109">Создание рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="79d43-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="79d43-110">Щелкните правой кнопкой мыши **NumberGuessWorkflowActivities** в **Обозреватель решений** и выберите **добавить**, **новый элемент**.</span><span class="sxs-lookup"><span data-stu-id="79d43-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="79d43-111">В узле **установленные** **Общие элементы** выберите **Рабочий процесс**.</span><span class="sxs-lookup"><span data-stu-id="79d43-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="79d43-112">В списке **Рабочий процесс** выберите пункт **Действие**.</span><span class="sxs-lookup"><span data-stu-id="79d43-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="79d43-113">Введите `FlowchartNumberGuessWorkflow` в поле **имя** и нажмите кнопку **добавить**.</span><span class="sxs-lookup"><span data-stu-id="79d43-113">Type `FlowchartNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="79d43-114">Перетащите действие **блок-схема** из **раздела блок** -схема **области элементов** и поместите его в метку **Перетащите сюда действие** в рабочей области конструктора рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="79d43-114">Drag a **Flowchart** activity from the **Flowchart** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="79d43-115">Создание переменных и аргументов рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="79d43-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="79d43-116">Дважды щелкните **FlowchartNumberGuessWorkflow. XAML** в **Обозреватель решений** , чтобы отобразить рабочий процесс в конструкторе, если он еще не отображается.</span><span class="sxs-lookup"><span data-stu-id="79d43-116">Double-click **FlowchartNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="79d43-117">Щелкните **аргументы** в левой нижней части конструктора рабочих процессов, чтобы отобразить панель **аргументы** .</span><span class="sxs-lookup"><span data-stu-id="79d43-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="79d43-118">Нажмите кнопку **Создать аргумент**.</span><span class="sxs-lookup"><span data-stu-id="79d43-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="79d43-119">Введите в `MaxNumber` поле **имя** , выберите **в** раскрывающемся списке **направление** значение **Int32** , а затем нажмите клавишу ВВОД  , чтобы сохранить аргумент.</span><span class="sxs-lookup"><span data-stu-id="79d43-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="79d43-120">Нажмите кнопку **Создать аргумент**.</span><span class="sxs-lookup"><span data-stu-id="79d43-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="79d43-121">Введите `Turns` в поле **имя** , которое находится ниже вновь добавленного `MaxNumber` аргумента,  выберите из раскрывающегося списка **направление** , выберите **Int32** из раскрывающегося списка **тип аргумента** и нажмите клавишу ВВОД.</span><span class="sxs-lookup"><span data-stu-id="79d43-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="79d43-122">В левом нижнем углу конструктора действий нажмите кнопку **Аргументы**, чтобы закрыть панель **Аргументы**.</span><span class="sxs-lookup"><span data-stu-id="79d43-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="79d43-123">Щелкните **переменные** в левой нижней части конструктора рабочих процессов, чтобы отобразить панель **переменные** .</span><span class="sxs-lookup"><span data-stu-id="79d43-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="79d43-124">Нажмите кнопку **Создать переменную**.</span><span class="sxs-lookup"><span data-stu-id="79d43-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="79d43-125">Если поле **создать переменную** не отображается, щелкните <xref:System.Activities.Statements.Flowchart> действие в области конструктора рабочих процессов, чтобы выбрать его.</span><span class="sxs-lookup"><span data-stu-id="79d43-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.Flowchart> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="79d43-126">Введите `Guess` в поле **имя** , выберите **Int32** в раскрывающемся списке **тип переменной** и нажмите клавишу ВВОД, чтобы сохранить переменную.</span><span class="sxs-lookup"><span data-stu-id="79d43-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="79d43-127">Нажмите кнопку **Создать переменную**.</span><span class="sxs-lookup"><span data-stu-id="79d43-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="79d43-128">Введите `Target` в поле **имя** , выберите **Int32** в раскрывающемся списке **тип переменной** и нажмите клавишу ВВОД, чтобы сохранить переменную.</span><span class="sxs-lookup"><span data-stu-id="79d43-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="79d43-129">В левом нижнем углу конструктора действий нажмите кнопку **Переменные**, чтобы закрыть панель **Переменные**.</span><span class="sxs-lookup"><span data-stu-id="79d43-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="79d43-130">Добавление действий рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="79d43-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="79d43-131">Перетащите действие **Assign (назначение** ) из раздела **примитивы** **области элементов** и наведите его на **начальный** узел, расположенный в верхней части блок-схемы.</span><span class="sxs-lookup"><span data-stu-id="79d43-131">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and hover it over the **Start** node, which is at the top of the flowchart.</span></span> <span data-ttu-id="79d43-132">Когда действие **Assign** находится над **начальным** узлом, вокруг **начального** узла появятся три треугольника.</span><span class="sxs-lookup"><span data-stu-id="79d43-132">When the **Assign** activity is over the **Start** node, three triangles will appear around the **Start** node.</span></span> <span data-ttu-id="79d43-133">Удалите действие **Assign** на треугольнике, расположенном непосредственно под **начальным** узлом.</span><span class="sxs-lookup"><span data-stu-id="79d43-133">Drop the **Assign** activity on the triangle that is directly below the **Start** node.</span></span> <span data-ttu-id="79d43-134">Это позволит связать два элемента вместе и назначить действие **Assign** в качестве первого действия в блок-схеме.</span><span class="sxs-lookup"><span data-stu-id="79d43-134">This will link the two items together and designates the **Assign** activity as the first activity in the flowchart.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="79d43-135">Действия можно также указывать в качестве начального действия в рабочем процессе, вручную связав их с действием в начальном узле.</span><span class="sxs-lookup"><span data-stu-id="79d43-135">Activities can also be indicated as the starting activity in the workflow by manually linking them activity to the start node.</span></span> <span data-ttu-id="79d43-136">Для этого наведите указатель мыши на **начальный** узел, щелкните один из прямоугольников, отображаемых при наведении указателя мыши на **начальный** узел, и перетащите строку подключения вниз к нужному действию и поместите ее на один из отображаемых прямоугольников.</span><span class="sxs-lookup"><span data-stu-id="79d43-136">To do this, hover the mouse over the **Start** node, click one of the rectangles that appear when the mouse is over the **Start** node, and drag the connecting line down to the desired activity and drop it on one of the rectangles that appear.</span></span> <span data-ttu-id="79d43-137">Вы также можете назначить действие в качестве начального действия, щелкнув его правой кнопкой мыши и выбрав пункт **задать в качестве начального узла**.</span><span class="sxs-lookup"><span data-stu-id="79d43-137">You can also designate an activity as the starting activity by right-clicking the it and choosing **Set as Start Node**.</span></span>  
  
2. <span data-ttu-id="79d43-138">Введите `Target` в поле **to** и следующее выражение в поле **введите выражение C#** или **введите выражение VB** .</span><span class="sxs-lookup"><span data-stu-id="79d43-138">Type `Target` into the **To** box and the following expression into the **Enter a C# Expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="79d43-139">Если окно **Панель элементов** не отображается, выберите пункт **Панель элементов** в меню **Вид**.</span><span class="sxs-lookup"><span data-stu-id="79d43-139">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
3. <span data-ttu-id="79d43-140">Перетащите действие **запрос** из раздела **NumberGuessWorkflowActivities** на **панели элементов**, поместите его под действием **Assign (назначение** ) из предыдущего шага и подключите действие **Prompt** к действию **Assign** .</span><span class="sxs-lookup"><span data-stu-id="79d43-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox**, drop it below the **Assign** activity from the previous step, and connect the **Prompt** activity to the **Assign** activity.</span></span> <span data-ttu-id="79d43-141">Соединить два действия можно тремя способами.</span><span class="sxs-lookup"><span data-stu-id="79d43-141">There are three ways to connect the two activities.</span></span> <span data-ttu-id="79d43-142">Первый способ — подключить их по мере удаления действия **Prompt** в рабочем процессе.</span><span class="sxs-lookup"><span data-stu-id="79d43-142">The first way is to connect them as you drop the **Prompt** activity on the workflow.</span></span> <span data-ttu-id="79d43-143">При перетаскивании действия **Prompt** в рабочий процесс наведите его на действие Assign ( **назначить** ) и поместите его на один из четырех треугольников, отображаемых, когда действие **запроса** находится над действием **Assign (назначить** ).</span><span class="sxs-lookup"><span data-stu-id="79d43-143">As you are dragging the **Prompt** activity to the workflow, hover it over the **Assign** activity and drop it onto one of the four triangles that appear when the **Prompt** activity is over the **Assign** activity.</span></span> <span data-ttu-id="79d43-144">Второй способ — удалить действие **Prompt** в рабочем процессе в нужном месте.</span><span class="sxs-lookup"><span data-stu-id="79d43-144">The second way is to drop the **Prompt** activity onto the workflow at the desired location.</span></span> <span data-ttu-id="79d43-145">Затем наведите указатель мыши на действие **Assign (назначение** ) и перетащите один из прямоугольников, отображаемых в действие **Prompt** .</span><span class="sxs-lookup"><span data-stu-id="79d43-145">Then, hover the mouse over the **Assign** activity and drag one of the rectangles that appears down to the **Prompt** activity.</span></span> <span data-ttu-id="79d43-146">Перетащите указатель мыши, чтобы соединяющая линия из действия **назначить** подключаться к одному из прямоугольников действия **запроса** , а затем отпустите кнопку мыши.</span><span class="sxs-lookup"><span data-stu-id="79d43-146">Drag the mouse so that the connecting line from the **Assign** activity connects to one of the rectangles of the **Prompt** activity, and then release the mouse button.</span></span> <span data-ttu-id="79d43-147">Третий способ очень похож на первый, за исключением того, что вместо того, чтобы перетаскивать действие **Prompt** из **панели элементов**, перетащите его из своего расположения в рабочей области конструктора рабочих процессов, наведите его на действие **Assign (назначить** ) и поместите его на один из появившихся треугольников.</span><span class="sxs-lookup"><span data-stu-id="79d43-147">The third way is very similar to the first way, except that instead of dragging the **Prompt** activity from the **Toolbox**, you drag it from its location on the workflow design surface, hover it over the **Assign** activity, and drop it onto one of the triangles that appears.</span></span>  
  
4. <span data-ttu-id="79d43-148">В **окне Свойства** действия **Prompt** введите, `"EnterGuess"` включая кавычки, в поле значение свойства **BookmarkName** .</span><span class="sxs-lookup"><span data-stu-id="79d43-148">In the **Properties Window** for the **Prompt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box.</span></span> <span data-ttu-id="79d43-149">Введите `Guess` в поле значение свойства **результата** и введите следующее выражение в поле свойства **текста** .</span><span class="sxs-lookup"><span data-stu-id="79d43-149">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="79d43-150">Если **окно Свойства** не отображается, в меню **вид** выберите пункт **окно свойств** .</span><span class="sxs-lookup"><span data-stu-id="79d43-150">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
5. <span data-ttu-id="79d43-151">Перетащите действие **Assign (назначение** ) из раздела **примитивы** **области элементов** и подключите его с помощью одного из методов, описанных в предыдущем шаге, чтобы он был ниже действия **Prompt** .</span><span class="sxs-lookup"><span data-stu-id="79d43-151">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and connect it using one of the methods described in the previous step so that it is below the **Prompt** activity.</span></span>  
  
6. <span data-ttu-id="79d43-152">Введите `Turns` в поле **Кому** и `Turns + 1` в поле **введите выражение C#**  или **введите выражение VB** .</span><span class="sxs-lookup"><span data-stu-id="79d43-152">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression**  or **Enter a VB expression** box.</span></span>  
  
7. <span data-ttu-id="79d43-153">Перетащите **FlowDecision** из раздела **блок-схема** области **элементов** и подключите его под действием **Assign (назначение** ).</span><span class="sxs-lookup"><span data-stu-id="79d43-153">Drag a **FlowDecision** from the **Flowchart** section of the **Toolbox** and connect it below the **Assign** activity.</span></span> <span data-ttu-id="79d43-154">В **окне Свойства** введите следующее выражение в поле значение свойства **Condition** .</span><span class="sxs-lookup"><span data-stu-id="79d43-154">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
8. <span data-ttu-id="79d43-155">Перетащите еще одно действие **FlowDecision** из **области элементов** и поместите его под первым.</span><span class="sxs-lookup"><span data-stu-id="79d43-155">Drag another **FlowDecision** activity from the **Toolbox** and drop it below the first one.</span></span> <span data-ttu-id="79d43-156">Соедините два действия, перетащив прямоугольник, помеченный как " **ложь** ", в верхнем действии **FlowDecision** на прямоугольник в верхней части второго действия **FlowDecision** .</span><span class="sxs-lookup"><span data-stu-id="79d43-156">Connect the two activities by dragging from the rectangle that is labeled **False** on the top **FlowDecision** activity to the rectangle at the top of the second **FlowDecision** activity.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="79d43-157">Если вы не видите метки **true** и **false** в **FlowDecision**, наведите указатель мыши на **FlowDecision**.</span><span class="sxs-lookup"><span data-stu-id="79d43-157">If you do not see the **True** and **False** labels on the **FlowDecision**, hover the mouse over the **FlowDecision**.</span></span>  
  
9. <span data-ttu-id="79d43-158">Щелкните второе действие **FlowDecision** , чтобы выбрать его.</span><span class="sxs-lookup"><span data-stu-id="79d43-158">Click the second **FlowDecision** activity to select it.</span></span> <span data-ttu-id="79d43-159">В **окне Свойства** введите следующее выражение в поле значение свойства **Condition** .</span><span class="sxs-lookup"><span data-stu-id="79d43-159">In the **Properties Window**, type the following expression into the **Condition** property value box.</span></span>  
  
    ```text
    Guess < Target
    ```  
  
10. <span data-ttu-id="79d43-160">Перетащите два действия **WriteLine** из раздела **примитивы** на **панели элементов** и расположите их так, чтобы они были параллельно под двумя действиями **FlowDecision** .</span><span class="sxs-lookup"><span data-stu-id="79d43-160">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that they are side by side below the two **FlowDecision** activities.</span></span> <span data-ttu-id="79d43-161">Соедините **истинное** действие нижнего действия **FlowDecision** с левым действием **WriteLine** и действием **false** с крайним правым действием **WriteLine** .</span><span class="sxs-lookup"><span data-stu-id="79d43-161">Connect the **True** action of the bottom **FlowDecision** activity to the leftmost **WriteLine** activity, and the **False** action to the rightmost **WriteLine** activity.</span></span>  
  
11. <span data-ttu-id="79d43-162">Щелкните левое действие **WriteLine** , чтобы выбрать его, и введите следующее выражение в поле значение свойства **текста** в **окне Свойства**.</span><span class="sxs-lookup"><span data-stu-id="79d43-162">Click the leftmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
12. <span data-ttu-id="79d43-163">Соедините команду **WriteLine** с левой стороной действия **Prompt** , находящейся над ним.</span><span class="sxs-lookup"><span data-stu-id="79d43-163">Connect the **WriteLine** to the left side of the **Prompt** activity that is above it.</span></span>  
  
13. <span data-ttu-id="79d43-164">Щелкните правой кнопкой мыши действие **WriteLine** , чтобы выбрать его, и введите следующее выражение в поле значение свойства **текста** в **окне Свойства**.</span><span class="sxs-lookup"><span data-stu-id="79d43-164">Click the rightmost **WriteLine** activity to select it, and type the following expression into the **Text** property value box in the **Properties Window**.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
14. <span data-ttu-id="79d43-165">Соедините действие **WriteLine** с правой стороны действия **Prompt** над ним.</span><span class="sxs-lookup"><span data-stu-id="79d43-165">Connect the **WriteLine** activity to the right side of the **Prompt** activity above it.</span></span>  
  
     <span data-ttu-id="79d43-166">В следующем примере показан завершенный рабочий процесс.</span><span class="sxs-lookup"><span data-stu-id="79d43-166">The following example illustrates the completed workflow.</span></span>  
  
     ![Схема, на которой показана завершенная блок-схема Windows Workflow Foundation.](./media/how-to-create-a-flowchart-workflow/completed-windows-workflow-flowchart.png)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="79d43-168">Построение рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="79d43-168">To build the workflow</span></span>  
  
1. <span data-ttu-id="79d43-169">Чтобы построить решение, нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="79d43-169">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="79d43-170">Инструкции по запуску рабочего процесса см. в следующем разделе [: запуск рабочего процесса](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="79d43-170">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="79d43-171">Если вы уже выполнили [инструкции](how-to-run-a-workflow.md) по выполнению шага рабочего процесса с другим стилем рабочего процесса и хотите запустить его с помощью рабочего процесса блок-схемы из этого шага, перейдите к разделу [Создание и запуск приложения](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) , [посвященного запуску рабочего процесса](how-to-run-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="79d43-171">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the flowchart workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79d43-172">См. также</span><span class="sxs-lookup"><span data-stu-id="79d43-172">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="79d43-173">Программирование в Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="79d43-173">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="79d43-174">Разработка рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="79d43-174">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="79d43-175">Учебник по началу работы</span><span class="sxs-lookup"><span data-stu-id="79d43-175">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="79d43-176">Практическое руководство. Создание действия</span><span class="sxs-lookup"><span data-stu-id="79d43-176">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="79d43-177">Практическое руководство. Запуск рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="79d43-177">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
