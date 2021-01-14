---
title: Практическое руководство. Создание действия
description: 'В этой статье показано, как создать два действия в Workflow Foundation: один, использующий код для реализации его логики и другой, определенный с помощью других действий.'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: c7610d8612eb944afa9c23e1bf2abceeb3a6d38b
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190771"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="ec634-103">Практическое руководство. Создание действия</span><span class="sxs-lookup"><span data-stu-id="ec634-103">How to: Create an Activity</span></span>

<span data-ttu-id="ec634-104">Действия являются базовой единицей режима работы в [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ec634-104">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="ec634-105">Логика выполнения действия может быть реализована в управляемом коде или с помощью других действий.</span><span class="sxs-lookup"><span data-stu-id="ec634-105">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="ec634-106">В этом разделе показано создание двух действий.</span><span class="sxs-lookup"><span data-stu-id="ec634-106">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="ec634-107">Первое действие - простое действие с использованием кода для реализации логики выполнения.</span><span class="sxs-lookup"><span data-stu-id="ec634-107">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="ec634-108">Реализация второго действия определяется с помощью других действий.</span><span class="sxs-lookup"><span data-stu-id="ec634-108">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="ec634-109">Эти действия используются в следующих шагах учебника.</span><span class="sxs-lookup"><span data-stu-id="ec634-109">These activities are used in following steps in the tutorial.</span></span>

## <a name="create-the-activity-library-project"></a><span data-ttu-id="ec634-110">Создание проекта библиотеки действий</span><span class="sxs-lookup"><span data-stu-id="ec634-110">Create the activity library project</span></span>

1. <span data-ttu-id="ec634-111">Откройте Visual Studio и выберите   >  в меню **файл** пункт создать **проект** .</span><span class="sxs-lookup"><span data-stu-id="ec634-111">Open Visual Studio and choose **New** > **Project** from the **File** menu.</span></span>

2. <span data-ttu-id="ec634-112">В диалоговом окне **Новый проект** в разделе **установленная** Категория выберите   >  **Рабочий процесс** Visual C# (или **Visual Basic**  >  **Рабочий процесс**).</span><span class="sxs-lookup"><span data-stu-id="ec634-112">In the **New Project** dialog, under the **Installed** category, select **Visual C#** > **Workflow** (or **Visual Basic** > **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ec634-113">Если категория шаблон **рабочего процесса** не отображается, может потребоваться установить компонент **Windows Workflow Foundation** Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ec634-113">If you don't see the **Workflow** template category, you may need to install the **Windows Workflow Foundation** component of Visual Studio.</span></span> <span data-ttu-id="ec634-114">Выберите ссылку **открыть Visual Studio Installer** в левой части диалогового окна **Новый проект** .</span><span class="sxs-lookup"><span data-stu-id="ec634-114">Choose the **Open Visual Studio Installer** link on the left-hand side of the **New Project** dialog.</span></span> <span data-ttu-id="ec634-115">В Visual Studio Installer выберите вкладку **отдельные компоненты** . Затем в категории **действия разработки** выберите компонент **Windows Workflow Foundation** .</span><span class="sxs-lookup"><span data-stu-id="ec634-115">In Visual Studio Installer, select the **Individual components** tab. Then, under the **Development activities** category, select the **Windows Workflow Foundation** component.</span></span> <span data-ttu-id="ec634-116">Нажмите кнопку **изменить** , чтобы установить компонент.</span><span class="sxs-lookup"><span data-stu-id="ec634-116">Choose **Modify** to install the component.</span></span>

3. <span data-ttu-id="ec634-117">Выберите шаблон проекта **Библиотека действий** .</span><span class="sxs-lookup"><span data-stu-id="ec634-117">Select the **Activity Library** project template.</span></span> <span data-ttu-id="ec634-118">Введите `NumberGuessWorkflowActivities` в поле **Имя** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="ec634-118">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>

4. <span data-ttu-id="ec634-119">В **обозревателе решений** щелкните правой кнопкой мыши файл **Activity1.xaml** и выберите пункт **Удалить**.</span><span class="sxs-lookup"><span data-stu-id="ec634-119">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="ec634-120">Нажмите кнопку **ОК** для подтверждения.</span><span class="sxs-lookup"><span data-stu-id="ec634-120">Click **OK** to confirm.</span></span>

## <a name="create-the-readint-activity"></a><span data-ttu-id="ec634-121">Создание действия ReadInt</span><span class="sxs-lookup"><span data-stu-id="ec634-121">Create the ReadInt activity</span></span>

1. <span data-ttu-id="ec634-122">В меню **проект** выберите команду **Добавить новый элемент** .</span><span class="sxs-lookup"><span data-stu-id="ec634-122">Choose **Add New Item** from the **Project** menu.</span></span>

2. <span data-ttu-id="ec634-123">В узле **установленные**  >  **Общие элементы** выберите **Рабочий процесс**.</span><span class="sxs-lookup"><span data-stu-id="ec634-123">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="ec634-124">Выберите **действие код** в списке **Рабочий процесс** .</span><span class="sxs-lookup"><span data-stu-id="ec634-124">Select **Code Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="ec634-125">Введите `ReadInt` в поле **Имя** и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="ec634-125">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>

4. <span data-ttu-id="ec634-126">Замените существующее определение `ReadInt` следующим определением.</span><span class="sxs-lookup"><span data-stu-id="ec634-126">Replace the existing `ReadInt` definition with the following definition.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > <span data-ttu-id="ec634-127">Действие `ReadInt` является производным от <xref:System.Activities.NativeActivity%601>, а не от <xref:System.Activities.CodeActivity>, которое задается по умолчанию для шаблона действия кода.</span><span class="sxs-lookup"><span data-stu-id="ec634-127">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="ec634-128"><xref:System.Activities.CodeActivity%601> можно использовать, если действие возвращает один результат, который предоставляется с помощью аргумента <xref:System.Activities.Activity%601.Result%2A>. Однако <xref:System.Activities.CodeActivity%601> не поддерживает использование закладок, поэтому используется <xref:System.Activities.NativeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="ec634-128"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>

## <a name="create-the-prompt-activity"></a><span data-ttu-id="ec634-129">Создание действия Prompt</span><span class="sxs-lookup"><span data-stu-id="ec634-129">Create the Prompt activity</span></span>

1. <span data-ttu-id="ec634-130">Нажмите клавиши **CTRL** + **SHIFT** + **B** , чтобы построить проект.</span><span class="sxs-lookup"><span data-stu-id="ec634-130">Press **Ctrl**+**Shift**+**B** to build the project.</span></span> <span data-ttu-id="ec634-131">При сборке проекта включается действие `ReadInt`, которое будет использоваться для построения пользовательского действия, начиная с этого шага.</span><span class="sxs-lookup"><span data-stu-id="ec634-131">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>

2. <span data-ttu-id="ec634-132">В меню **проект** выберите команду **Добавить новый элемент** .</span><span class="sxs-lookup"><span data-stu-id="ec634-132">Choose **Add New Item** from the **Project** menu.</span></span>

3. <span data-ttu-id="ec634-133">В узле **установленные**  >  **Общие элементы** выберите **Рабочий процесс**.</span><span class="sxs-lookup"><span data-stu-id="ec634-133">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="ec634-134">В списке **Рабочий процесс** выберите пункт **Действие**.</span><span class="sxs-lookup"><span data-stu-id="ec634-134">Select **Activity** from the **Workflow** list.</span></span>

4. <span data-ttu-id="ec634-135">Введите `Prompt` в поле **Имя** и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="ec634-135">Type `Prompt` into the **Name** box and then click **Add**.</span></span>

5. <span data-ttu-id="ec634-136">Дважды щелкните **Prompt. XAML** в **Обозреватель решений** , чтобы отобразить его в конструкторе, если он еще не отображается.</span><span class="sxs-lookup"><span data-stu-id="ec634-136">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>

6. <span data-ttu-id="ec634-137">В левом нижнем углу конструктора действий нажмите кнопку **Аргументы** для отображения панели **Аргументы**.</span><span class="sxs-lookup"><span data-stu-id="ec634-137">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>

7. <span data-ttu-id="ec634-138">Нажмите кнопку **Создать аргумент**.</span><span class="sxs-lookup"><span data-stu-id="ec634-138">Click **Create Argument**.</span></span>

8. <span data-ttu-id="ec634-139">Введите в `BookmarkName` поле **имя** , выберите **в** раскрывающемся списке **направление** пункт **строка** из раскрывающегося списка **тип аргумента** и нажмите клавишу **Ввод** , чтобы сохранить аргумент.</span><span class="sxs-lookup"><span data-stu-id="ec634-139">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

9. <span data-ttu-id="ec634-140">Нажмите кнопку **Создать аргумент**.</span><span class="sxs-lookup"><span data-stu-id="ec634-140">Click **Create Argument**.</span></span>

10. <span data-ttu-id="ec634-141">Введите `Result` в поле **имя** , которое находится под только что добавленным `BookmarkName` аргументом, выберите пункт **выход** из раскрывающегося списка **направление** , выберите **Int32** из раскрывающегося списка **тип аргумента** и нажмите клавишу **Ввод**.</span><span class="sxs-lookup"><span data-stu-id="ec634-141">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press **Enter**.</span></span>

11. <span data-ttu-id="ec634-142">Нажмите кнопку **Создать аргумент**.</span><span class="sxs-lookup"><span data-stu-id="ec634-142">Click **Create Argument**.</span></span>

12. <span data-ttu-id="ec634-143">Введите в `Text` поле **имя** , выберите **в** раскрывающемся списке **направление** пункт **строка** из раскрывающегося списка **тип аргумента** и нажмите клавишу **Ввод** , чтобы сохранить аргумент.</span><span class="sxs-lookup"><span data-stu-id="ec634-143">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

     <span data-ttu-id="ec634-144">Эти три аргумента связаны с соответствующими аргументами действий <xref:System.Activities.Statements.WriteLine> и `ReadInt`, которые добавляются к действию `Prompt` на следующих этапах.</span><span class="sxs-lookup"><span data-stu-id="ec634-144">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>

13. <span data-ttu-id="ec634-145">В левом нижнем углу конструктора действий нажмите кнопку **Аргументы**, чтобы закрыть панель **Аргументы**.</span><span class="sxs-lookup"><span data-stu-id="ec634-145">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

14. <span data-ttu-id="ec634-146">Перетащите действие **Sequence** из раздела **поток управления** на **панели элементов** и поместите его в метку **перетащите действие** в конструктор действий с **приглашением** .</span><span class="sxs-lookup"><span data-stu-id="ec634-146">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>

    > [!TIP]
    > <span data-ttu-id="ec634-147">Если окно **Панель элементов** не отображается, выберите пункт **Панель элементов** в меню **Вид**.</span><span class="sxs-lookup"><span data-stu-id="ec634-147">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

15. <span data-ttu-id="ec634-148">Перетащите действие **WriteLine** из раздела **примитивы** на **панели элементов** и поместите его на метку **перетащите действие сюда** действие **последовательность** .</span><span class="sxs-lookup"><span data-stu-id="ec634-148">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>

16. <span data-ttu-id="ec634-149">Привяжите **текстовый** аргумент действия **WriteLine** к **текстовому** аргументу действия **Prompt** . для этого введите `Text` в поле **Ввод выражения C#** или **введите выражение VB** в окне **Свойства** , а затем нажмите клавишу **Tab** два раза.</span><span class="sxs-lookup"><span data-stu-id="ec634-149">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the **Tab** key two times.</span></span> <span data-ttu-id="ec634-150">При этом окно элементов списка технологии IntelliSense закрывается, а значение свойства сохраняется посредством перемещения выбора вне свойства.</span><span class="sxs-lookup"><span data-stu-id="ec634-150">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="ec634-151">Это свойство также может быть установлено путем ввода `Text` в **выражение C#** или **ввода поля выражения VB** для самого действия.</span><span class="sxs-lookup"><span data-stu-id="ec634-151">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>

    > [!TIP]
    > <span data-ttu-id="ec634-152">Если **окно Свойства** не отображается, в меню **вид** выберите пункт **окно свойств** .</span><span class="sxs-lookup"><span data-stu-id="ec634-152">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

17. <span data-ttu-id="ec634-153">Перетащите действие **ReadInt** из раздела **NumberGuessWorkflowActivities** на **панели элементов** и поместите его в действие **Sequence** , чтобы оно состоит из действия **WriteLine** .</span><span class="sxs-lookup"><span data-stu-id="ec634-153">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>

18. <span data-ttu-id="ec634-154">Привяжите аргумент **BookmarkName** действия **ReadInt** к аргументу **BookmarkName** действия **Prompt** , введя `BookmarkName` в поле **введите выражение VB** справа от аргумента **BookmarkName** в **окне свойств**, а затем нажмите клавишу TAB два раза, чтобы закрыть окно **"** список членов IntelliSense" и сохранить свойство.</span><span class="sxs-lookup"><span data-stu-id="ec634-154">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the **Tab** key two times to close the IntelliSense list members window and save the property.</span></span>

19. <span data-ttu-id="ec634-155">Привяжите **результирующий** аргумент действия **ReadInt** к аргументу **result** действия **Prompt** , введя `Result` в поле **введите выражение VB** справа от аргумента **result** в **окне Свойства**, а затем дважды нажмите клавишу **Tab** .</span><span class="sxs-lookup"><span data-stu-id="ec634-155">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the **Tab** key two times.</span></span>

20. <span data-ttu-id="ec634-156">Нажмите клавиши **CTRL** + **SHIFT** + **B** , чтобы построить решение.</span><span class="sxs-lookup"><span data-stu-id="ec634-156">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ec634-157">Дальнейшие действия</span><span class="sxs-lookup"><span data-stu-id="ec634-157">Next steps</span></span>

<span data-ttu-id="ec634-158">Инструкции по созданию рабочего процесса с помощью этих действий см. в следующем шаге руководства, [инструкции. Создание рабочего процесса](how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="ec634-158">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ec634-159">См. также</span><span class="sxs-lookup"><span data-stu-id="ec634-159">See also</span></span>

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [<span data-ttu-id="ec634-160">Разработка и реализация настраиваемых действий</span><span class="sxs-lookup"><span data-stu-id="ec634-160">Designing and Implementing Custom Activities</span></span>](designing-and-implementing-custom-activities.md)
- [<span data-ttu-id="ec634-161">Учебник по началу работы</span><span class="sxs-lookup"><span data-stu-id="ec634-161">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="ec634-162">Практическое руководство. Создание рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="ec634-162">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="ec634-163">Использование ExpressionTextBox в пользовательском конструкторе действия</span><span class="sxs-lookup"><span data-stu-id="ec634-163">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
