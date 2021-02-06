---
description: Дополнительные сведения см. в статье как обновить определение выполняющегося экземпляра рабочего процесса.
title: Практическое руководство. Обновление определения выполняющегося экземпляра рабочего процесса
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
ms.openlocfilehash: a3b1faa933cb79301946427823ef3e9f114823f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631230"
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a><span data-ttu-id="f187e-103">Практическое руководство. Обновление определения выполняющегося экземпляра рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="f187e-103">How to: Update the Definition of a Running Workflow Instance</span></span>

<span data-ttu-id="f187e-104">Динамическое обновление предоставляет разработчикам приложений рабочих процессов механизм обновления определения рабочего процесса для сохраненного экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="f187e-104">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="f187e-105">Это позволяет реализовать исправление ошибки, внедрение новых требований или учет непредвиденных изменений.</span><span class="sxs-lookup"><span data-stu-id="f187e-105">The required change can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="f187e-106">На этом шаге в учебнике показано, как использовать динамическое обновление для изменения сохраненных экземпляров `v1` рабочего процесса подбора номера в соответствии с новыми функциями, представленными в статье [как разместить несколько версий рабочего процесса параллельно](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="f187e-106">This step in the tutorial demonstrates how to use dynamic update to modify  persisted instances of the `v1` number guessing workflow to match the new functionality introduced in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="f187e-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="f187e-107">In this topic</span></span>

- [<span data-ttu-id="f187e-108">Создание проекта CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="f187e-108">To create the CreateUpdateMaps project</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)

- [<span data-ttu-id="f187e-109">Обновление StateMachineNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="f187e-109">To update StateMachineNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)

- [<span data-ttu-id="f187e-110">Обновление FlowchartNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="f187e-110">To update FlowchartNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)

- [<span data-ttu-id="f187e-111">Обновление SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="f187e-111">To update SequentialNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)

- [<span data-ttu-id="f187e-112">Сборка и запуск приложения CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="f187e-112">To build and run the CreateUpdateMaps application</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)

- [<span data-ttu-id="f187e-113">Сборка обновленной сборки рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="f187e-113">To build the updated workflow assembly</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)

- [<span data-ttu-id="f187e-114">Обновление WorkflowVersionMap новыми версиями</span><span class="sxs-lookup"><span data-stu-id="f187e-114">To update WorkflowVersionMap with the new versions</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)

- [<span data-ttu-id="f187e-115">Применение динамических обновлений</span><span class="sxs-lookup"><span data-stu-id="f187e-115">To apply the dynamic updates</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)

- [<span data-ttu-id="f187e-116">Запуск приложения с обновленными рабочими процессами</span><span class="sxs-lookup"><span data-stu-id="f187e-116">To run the application with the updated workflows</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)

- [<span data-ttu-id="f187e-117">Разрешение на запуск предыдущих версий рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="f187e-117">To enable starting previous versions of the workflows</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)

### <a name="to-create-the-createupdatemaps-project"></a><a name="BKMK_CreateProject"></a> <span data-ttu-id="f187e-118">Создание проекта Креатеупдатемапс</span><span class="sxs-lookup"><span data-stu-id="f187e-118">To create the CreateUpdateMaps project</span></span>

1. <span data-ttu-id="f187e-119">Щелкните правой кнопкой мыши **WF45GettingStartedTutorial** в **Обозреватель решений** и выберите **добавить**, **Новый проект**.</span><span class="sxs-lookup"><span data-stu-id="f187e-119">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>

2. <span data-ttu-id="f187e-120">На узле **установленные** выберите **Visual C#**, **Windows** (или **Visual Basic**, **Windows**).</span><span class="sxs-lookup"><span data-stu-id="f187e-120">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="f187e-121">В зависимости от основного используемого языка программирования Visual Studio узел **Visual C#** или **Visual Basic** может располагаться в узле **Другие языки** под узлом **Установлено**.</span><span class="sxs-lookup"><span data-stu-id="f187e-121">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="f187e-122">Убедитесь, что в раскрывающемся списке версий .NET Framework выбран пункт **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="f187e-122">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="f187e-123">Выберите **консольное приложение** в списке **Windows** .</span><span class="sxs-lookup"><span data-stu-id="f187e-123">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="f187e-124">Введите **креатеупдатемапс** в поле **имя** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="f187e-124">Type **CreateUpdateMaps** into the **Name** box and click **OK**.</span></span>

3. <span data-ttu-id="f187e-125">Щелкните правой кнопкой мыши **креатеупдатемапс** в **Обозреватель решений** и выберите команду **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="f187e-125">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Add Reference**.</span></span>

4. <span data-ttu-id="f187e-126">Выберите **платформа** из узла **сборки** в списке **Добавить ссылку** .</span><span class="sxs-lookup"><span data-stu-id="f187e-126">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="f187e-127">Введите **System. activitys** в поле **Поиск сборок** , чтобы отфильтровать сборки и упростить выбор нужных ссылок.</span><span class="sxs-lookup"><span data-stu-id="f187e-127">Type **System.Activities** into the **Search Assemblies** box to filter the assemblies and make the desired references easier to select.</span></span>

5. <span data-ttu-id="f187e-128">Установите флажок рядом с элементом **System. activitys** из списка **результатов поиска** .</span><span class="sxs-lookup"><span data-stu-id="f187e-128">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>

6. <span data-ttu-id="f187e-129">Введите **сериализацию** в поле **Поиск сборок** и установите флажок рядом с элементом **System. Runtime. Serialization** в списке **результатов поиска** .</span><span class="sxs-lookup"><span data-stu-id="f187e-129">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>

7. <span data-ttu-id="f187e-130">Введите **System. XAML** в поле **Поиск сборок** и установите флажок рядом с элементом **System. XAML** из списка **результатов поиска** .</span><span class="sxs-lookup"><span data-stu-id="f187e-130">Type **System.Xaml** into the **Search Assemblies** box, and check the checkbox beside **System.Xaml** from the **Search Results** list.</span></span>

8. <span data-ttu-id="f187e-131">Нажмите кнопку **ОК** , чтобы закрыть **Диспетчер ссылок** и добавить ссылки.</span><span class="sxs-lookup"><span data-stu-id="f187e-131">Click **OK** to close **Reference Manager** and add the references.</span></span>

9. <span data-ttu-id="f187e-132">Добавьте следующие инструкции `using` (или `Imports`) в начало файла с другими инструкциями `using` (или `Imports`).</span><span class="sxs-lookup"><span data-stu-id="f187e-132">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.Statements
    Imports System.Xaml
    Imports System.Reflection
    Imports System.IO
    Imports System.Activities.XamlIntegration
    Imports System.Activities.DynamicUpdate
    Imports System.Runtime.Serialization
    Imports Microsoft.VisualBasic.Activities
    ```

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    using System.IO;
    using System.Xaml;
    using System.Reflection;
    using System.Activities.XamlIntegration;
    using System.Activities.DynamicUpdate;
    using System.Runtime.Serialization;
    using Microsoft.CSharp.Activities;
    ```

10. <span data-ttu-id="f187e-133">Добавьте два следующих строковых члена в класс `Program` (или `Module1`).</span><span class="sxs-lookup"><span data-stu-id="f187e-133">Add the following two string members to the `Program` class (or `Module1`).</span></span>

    ```vb
    Const mapPath = "..\..\..\PreviousVersions"
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"
    ```

    ```csharp
    const string mapPath = @"..\..\..\PreviousVersions";
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";
    ```

11. <span data-ttu-id="f187e-134">Добавьте в класс `StartUpdate` (`Program`) следующий метод `Module1`.</span><span class="sxs-lookup"><span data-stu-id="f187e-134">Add the following `StartUpdate` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="f187e-135">Этот метод загружает указанное определение рабочего процесса языка XAML в `ActivityBuilder`, а затем вызывает `DynamicUpdate.PrepareForUpdate`.</span><span class="sxs-lookup"><span data-stu-id="f187e-135">This method loads up the specified xaml workflow definition into an `ActivityBuilder`, and then calls `DynamicUpdate.PrepareForUpdate`.</span></span> <span data-ttu-id="f187e-136">`PrepareForUpdate` создает копию экземпляра определения рабочего процесса в `ActivityBuilder`.</span><span class="sxs-lookup"><span data-stu-id="f187e-136">`PrepareForUpdate` makes a copy of the workflow definition inside the `ActivityBuilder`.</span></span> <span data-ttu-id="f187e-137">После изменения определения рабочего процесса эта копия используется вместе с измененным определением рабочего процесса для создания схемы обновления.</span><span class="sxs-lookup"><span data-stu-id="f187e-137">After the workflow definition is modified, this copy is used along with the modified workflow definition to create the update map.</span></span>

    ```vb
    Private Function StartUpdate(name As String) As ActivityBuilder
        'Create the XamlXmlReaderSettings.
        Dim readerSettings As XamlReaderSettings = New XamlXmlReaderSettings()
        'In the XAML the "local" namespace refers to artifacts that come from
        'the same project as the XAML. When loading XAML if the currently executing
        'assembly is not the same assembly that was referred to as "local" in the XAML
        'LocalAssembly must be set to the assembly containing the artifacts.
        'Assembly.LoadFile requires an absolute path so convert this relative path
        'to an absolute path.
        readerSettings.LocalAssembly = Assembly.LoadFile(
            Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))

        Dim fullPath As String = Path.Combine(definitionPath, name)
        Dim xamlReader As XamlXmlReader = New XamlXmlReader(fullPath, readerSettings)

        'Load the workflow definition into an ActivityBuilder.
        Dim wf As ActivityBuilder = XamlServices.Load(
            ActivityXamlServices.CreateBuilderReader(xamlReader))

        'PrepareForUpdate makes a copy of the workflow definition in the
        'ActivityBuilder that is used for comparison when the update
        'map is created.
        DynamicUpdateServices.PrepareForUpdate(wf)

        Return wf
    End Function
    ```

    ```csharp
    private static ActivityBuilder StartUpdate(string name)
    {
        // Create the XamlXmlReaderSettings.
        XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
        {
            // In the XAML the "local" namespace refers to artifacts that come from
            // the same project as the XAML. When loading XAML if the currently executing
            // assembly is not the same assembly that was referred to as "local" in the XAML
            // LocalAssembly must be set to the assembly containing the artifacts.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            LocalAssembly = Assembly.LoadFile(
                Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))
        };

        string path = Path.Combine(definitionPath, name);
        XamlXmlReader xamlReader = new XamlXmlReader(path, readerSettings);

        // Load the workflow definition into an ActivityBuilder.
        ActivityBuilder wf = XamlServices.Load(
            ActivityXamlServices.CreateBuilderReader(xamlReader))
            as ActivityBuilder;

        // PrepareForUpdate makes a copy of the workflow definition in the
        // ActivityBuilder that is used for comparison when the update
        // map is created.
        DynamicUpdateServices.PrepareForUpdate(wf);

        return wf;
    }
    ```

12. <span data-ttu-id="f187e-138">Затем добавьте следующий метод `CreateUpdateMethod` в класс `Program` (или `Module1`).</span><span class="sxs-lookup"><span data-stu-id="f187e-138">Next, add the following `CreateUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="f187e-139">При этом создается схема динамического обновления путем вызова DynamicUpdateServices.CreateUpdateMap, а затем схема сохраняется с указанным именем.</span><span class="sxs-lookup"><span data-stu-id="f187e-139">This creates a dynamic update map by calling DynamicUpdateServices.CreateUpdateMap, and then saves the update map using the specified name.</span></span> <span data-ttu-id="f187e-140">Эта схема обновления содержит данные, необходимые среде выполнения для обновления экземпляра сохраненного рабочего процесса, который был запущен с использованием определения, содержащегося в `ActivityBuilder`, чтобы он завершился с использованием обновленного определения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="f187e-140">This update map contains the information needed by the workflow runtime to update a persisted workflow instance that was started using the original workflow definition contained in the `ActivityBuilder` so that it completes using the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateUpdateMaps(wf As ActivityBuilder, name As String)
        'Create the UpdateMap.
        Dim map As DynamicUpdateMap =
            DynamicUpdateServices.CreateUpdateMap(wf)

        'Serialize it to a file.
        Dim mapFullPath As String = Path.Combine(mapPath, name)
        Dim sz As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))
        Using fs As FileStream = File.Open(mapFullPath, FileMode.Create)
            sz.WriteObject(fs, map)
        End Using
    End Sub
    ```

    ```csharp
    private static void CreateUpdateMaps(ActivityBuilder wf, string name)
    {
        // Create the UpdateMap.
        DynamicUpdateMap map =
            DynamicUpdateServices.CreateUpdateMap(wf);

        // Serialize it to a file.
        string path = Path.Combine(mapPath, name);
        DataContractSerializer sz = new DataContractSerializer(typeof(DynamicUpdateMap));
        using (FileStream fs = System.IO.File.Open(path, FileMode.Create))
        {
            sz.WriteObject(fs, map);
        }
    }
    ```

13. <span data-ttu-id="f187e-141">Добавьте в класс `SaveUpdatedDefinition` (`Program`) следующий метод `Module1`.</span><span class="sxs-lookup"><span data-stu-id="f187e-141">Add the following `SaveUpdatedDefinition` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="f187e-142">Этот метод сохраняет новое определение рабочего процесса после создания схемы обновления.</span><span class="sxs-lookup"><span data-stu-id="f187e-142">This method saves the updated workflow definition once the update map is created.</span></span>

    ```vb
    Private Sub SaveUpdatedDefinition(wf As ActivityBuilder, name As String)
        Dim xamlPath As String = Path.Combine(definitionPath, name)
        Dim sw As StreamWriter = File.CreateText(xamlPath)
        Dim xw As XamlWriter = ActivityXamlServices.CreateBuilderWriter(
            New XamlXmlWriter(sw, New XamlSchemaContext()))
        XamlServices.Save(xw, wf)
        sw.Close()
    End Sub
    ```

    ```csharp
    private static void SaveUpdatedDefinition(ActivityBuilder wf, string name)
    {
        string xamlPath = Path.Combine(definitionPath, name);
        StreamWriter sw = File.CreateText(xamlPath);
        XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(
            new XamlXmlWriter(sw, new XamlSchemaContext()));
        XamlServices.Save(xw, wf);
        sw.Close();
    }
    ```

### <a name="to-update-statemachinenumberguessworkflow"></a><a name="BKMK_StateMachine"></a> <span data-ttu-id="f187e-143">Обновление StateMachineNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="f187e-143">To update StateMachineNumberGuessWorkflow</span></span>

1. <span data-ttu-id="f187e-144">Добавьте `CreateStateMachineUpdateMap` в класс `Program` (или `Module1`).</span><span class="sxs-lookup"><span data-stu-id="f187e-144">Add a `CreateStateMachineUpdateMap` to the `Program` class (or `Module1`).</span></span>

    ```vb
    Private Sub CreateStateMachineUpdateMap()

    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
    }
    ```

2. <span data-ttu-id="f187e-145">Вызовите `StartUpdate` и получите ссылку на корневое действие `StateMachine` рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="f187e-145">Make a call to `StartUpdate` and then get a reference to the root `StateMachine` activity of the workflow.</span></span>

    ```vb
    Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")

    'Get a reference to the root StateMachine activity.
    Dim sm As StateMachine = wf.Implementation
    ```

    ```csharp
    ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");

    // Get a reference to the root StateMachine activity.
    StateMachine sm = wf.Implementation as StateMachine;
    ```

3. <span data-ttu-id="f187e-146">Затем обновите выражения двух `WriteLine` действий, которые показывают, слишком большое или слишком низкое значение предположения пользователя, чтобы они совпадали с обновлениями, выполненными в [виде размещения нескольких версий рабочего процесса параллельно](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="f187e-146">Next, update the expressions of the two `WriteLine` activities that display whether the user's guess is too high or too low so that they match the updates made in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    ```vb
    'Update the Text of the two WriteLine activities that write the
    'results of the user's guess. They are contained in the workflow as the
    'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
    Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action

    'Update the "too low" message.
    Dim tooLow As WriteLine = guessLow.Then
    tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

    'Update the "too high" message.
    Dim tooHigh As WriteLine = guessLow.Else
    tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")
    ```

    ```csharp
    // Update the Text of the two WriteLine activities that write the
    // results of the user's guess. They are contained in the workflow as the
    // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
    If guessLow = sm.States[1].Transitions[1].Action as If;

    // Update the "too low" message.
    WriteLine tooLow = guessLow.Then as WriteLine;
    tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

    // Update the "too high" message.
    WriteLine tooHigh = guessLow.Else as WriteLine;
    tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");
    ```

4. <span data-ttu-id="f187e-147">Затем добавьте новое действие `WriteLine`, которое отображает последнее сообщение.</span><span class="sxs-lookup"><span data-stu-id="f187e-147">Next, add the new `WriteLine` activity that displays the closing message.</span></span>

    ```vb
    'Create the new WriteLine that displays the closing message.
    Dim wl As New WriteLine() With
    {
        .Text = New VisualBasicValue(Of String) _
            ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
    }

    'Add it as the Action for the Guess Correct transition. The Guess Correct
    'transition is the first transition of States[1]. The transitions are listed
    'at the bottom of the State activity designer.
    sm.States(1).Transitions(0).Action = wl
    ```

    ```csharp
    // Create the new WriteLine that displays the closing message.
    WriteLine wl = new WriteLine
    {
        Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
    };

    // Add it as the Action for the Guess Correct transition. The Guess Correct
    // transition is the first transition of States[1]. The transitions are listed
    // at the bottom of the State activity designer.
    sm.States[1].Transitions[0].Action = wl;
    ```

5. <span data-ttu-id="f187e-148">После обновления рабочего процесса вызовите `CreateUpdateMaps` и `SaveUpdatedDefinition`.</span><span class="sxs-lookup"><span data-stu-id="f187e-148">After the workflow is updated, call `CreateUpdateMaps` and `SaveUpdatedDefinition`.</span></span> <span data-ttu-id="f187e-149">`CreateUpdateMaps` создает и сохраняет `DynamicUpdateMap`, а `SaveUpdatedDefinition` сохраняет обновленное определение рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="f187e-149">`CreateUpdateMaps` creates and saves the `DynamicUpdateMap`, and `SaveUpdatedDefinition` saves the updated workflow definition.</span></span>

    ```vb
    'Create the update map.
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")

    'Save the updated workflow definition.
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")
    ```

    ```csharp
    // Create the update map.
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");

    // Save the updated workflow definition.
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");
    ```

    <span data-ttu-id="f187e-150">Ниже приведен полный пример метода `CreateStateMachineUpdateMap`.</span><span class="sxs-lookup"><span data-stu-id="f187e-150">The following example is the completed `CreateStateMachineUpdateMap` method.</span></span>

    ```vb
    Private Sub CreateStateMachineUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")

        'Get a reference to the root StateMachine activity.
        Dim sm As StateMachine = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
        Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action

        'Update the "too low" message.
        Dim tooLow As WriteLine = guessLow.Then
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

        'Update the "too high" message.
        Dim tooHigh As WriteLine = guessLow.Else
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Add it as the Action for the Guess Correct transition. The Guess Correct
        'transition is the first transition of States[1]. The transitions are listed
        'at the bottom of the State activity designer.
        sm.States(1).Transitions(0).Action = wl

        'Create the update map.
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");

        // Get a reference to the root StateMachine activity.
        StateMachine sm = wf.Implementation as StateMachine;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
        If guessLow = sm.States[1].Transitions[1].Action as If;

        // Update the "too low" message.
        WriteLine tooLow = guessLow.Then as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

        // Update the "too high" message.
        WriteLine tooHigh = guessLow.Else as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Create the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Add it as the Action for the Guess Correct transition. The Guess Correct
        // transition is the first transition of States[1]. The transitions are listed
        // at the bottom of the State activity designer.
        sm.States[1].Transitions[0].Action = wl;

        // Create the update map.
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");

        // Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="to-update-flowchartnumberguessworkflow"></a><a name="BKMK_Flowchart"></a> <span data-ttu-id="f187e-151">Обновление FlowchartNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="f187e-151">To update FlowchartNumberGuessWorkflow</span></span>

1. <span data-ttu-id="f187e-152">Добавьте следующий метод `CreateFlowchartUpdateMethod` в класс `Program` (или `Module1`).</span><span class="sxs-lookup"><span data-stu-id="f187e-152">Add the following `CreateFlowchartUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="f187e-153">Этот метод аналогичен `CreateStateMachineUpdateMap`.</span><span class="sxs-lookup"><span data-stu-id="f187e-153">This method is similar to `CreateStateMachineUpdateMap`.</span></span> <span data-ttu-id="f187e-154">Он начинается с вызова `StartUpdate`, затем обновляет определение рабочего процесса блок-схемы и завершается сохранением схемы обновления и обновленного определения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="f187e-154">It starts with a call to `StartUpdate`, updates the flowchart workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateFlowchartUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("FlowchartNumberGuessWorkflow.xaml")

        'Get a reference to the root Flowchart activity.
        Dim fc As Flowchart = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'True and False action of the "Guess < Target" FlowDecision, which is
        'Nodes[4].
        Dim guessLow As FlowDecision = fc.Nodes(4)

        'Update the "too low" message.
        Dim trueStep As FlowStep = guessLow.True
        Dim tooLow As WriteLine = trueStep.Action
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

        'Update the "too high" message.
        Dim falseStep As FlowStep = guessLow.False
        Dim tooHigh As WriteLine = falseStep.Action
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Create a FlowStep to hold the WriteLine.
        Dim closingStep As New FlowStep() With
        {
            .Action = wl
        }

        'Add this new FlowStep to the True action of the
        '"Guess = Guess" FlowDecision
        Dim guessCorrect As FlowDecision = fc.Nodes(3)
        guessCorrect.True = closingStep

        'Add the new FlowStep to the Nodes collection.
        'If closingStep was replacing an existing node then
        'we would need to remove that Step from the collection.
        'In this example there was no existing True step to remove.
        fc.Nodes.Add(closingStep)

        'Create the update map.
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateFlowchartUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("FlowchartNumberGuessWorkflow.xaml");

        // Get a reference to the root Flowchart activity.
        Flowchart fc = wf.Implementation as Flowchart;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // True and False action of the "Guess < Target" FlowDecision, which is
        // Nodes[4].
        FlowDecision guessLow = fc.Nodes[4] as FlowDecision;

        // Update the "too low" message.
        FlowStep trueStep = guessLow.True as FlowStep;
        WriteLine tooLow = trueStep.Action as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

        // Update the "too high" message.
        FlowStep falseStep = guessLow.False as FlowStep;
        WriteLine tooHigh = falseStep.Action as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Add the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Create a FlowStep to hold the WriteLine.
        FlowStep closingStep = new FlowStep
        {
            Action = wl
        };

        // Add this new FlowStep to the True action of the
        // "Guess == Guess" FlowDecision
        FlowDecision guessCorrect = fc.Nodes[3] as FlowDecision;
        guessCorrect.True = closingStep;

        // Add the new FlowStep to the Nodes collection.
        // If closingStep was replacing an existing node then
        // we would need to remove that Step from the collection.
        // In this example there was no existing True step to remove.
        fc.Nodes.Add(closingStep);

        // Create the update map.
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map");

        //  Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="to-update-sequentialnumberguessworkflow"></a><a name="BKMK_Sequential"></a> <span data-ttu-id="f187e-155">Обновление SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="f187e-155">To update SequentialNumberGuessWorkflow</span></span>

1. <span data-ttu-id="f187e-156">Добавьте следующий метод `CreateSequentialUpdateMethod` в класс `Program` (или `Module1`).</span><span class="sxs-lookup"><span data-stu-id="f187e-156">Add the following `CreateSequentialUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="f187e-157">Этот метод аналогичен двум другим методам.</span><span class="sxs-lookup"><span data-stu-id="f187e-157">This method is similar to the other two methods.</span></span> <span data-ttu-id="f187e-158">Он начинается с вызова `StartUpdate`, затем обновляет определение рабочего процесса последовательности и завершается сохранением схемы обновления и обновленного определения рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="f187e-158">It starts with a call to `StartUpdate`, updates the sequential workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateSequentialUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("SequentialNumberGuessWorkflow.xaml")

        'Get a reference to the root activity in the workflow.
        Dim rootSequence As Sequence = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'Then and Else action of the "Guess < Target" If activity.
        'Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If
        Dim gameLoop As Statements.DoWhile = rootSequence.Activities(1)
        Dim gameBody As Sequence = gameLoop.Body
        Dim guessCorrect As Statements.If = gameBody.Activities(2)
        Dim guessLow As Statements.If = guessCorrect.Then
        Dim tooLow As WriteLine = guessLow.Then
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")
        Dim tooHigh As WriteLine = guessLow.Else
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Insert it as the third activity in the root sequence
        rootSequence.Activities.Insert(2, wl)

        'Create the update map.
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateSequentialUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("SequentialNumberGuessWorkflow.xaml");

        // Get a reference to the root activity in the workflow.
        Sequence rootSequence = wf.Implementation as Sequence;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // Then and Else action of the "Guess < Target" If activity.
        // Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If
        DoWhile gameLoop = rootSequence.Activities[1] as DoWhile;
        Sequence gameBody = gameLoop.Body as Sequence;
        If guessCorrect = gameBody.Activities[2] as If;
        If guessLow = guessCorrect.Then as If;
        WriteLine tooLow = guessLow.Then as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");
        WriteLine tooHigh = guessLow.Else as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Add the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Insert it as the third activity in the root sequence
        rootSequence.Activities.Insert(2, wl);

        // Create the update map.
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map");

        // Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="to-build-and-run-the-createupdatemaps-application"></a><a name="BKMK_CreateUpdateMaps"></a> <span data-ttu-id="f187e-159">Сборка и запуск приложения Креатеупдатемапс</span><span class="sxs-lookup"><span data-stu-id="f187e-159">To build and run the CreateUpdateMaps application</span></span>

1. <span data-ttu-id="f187e-160">Обновите метод `Main` и добавьте следующие три вызова методов.</span><span class="sxs-lookup"><span data-stu-id="f187e-160">Update the `Main` method and add the following three method calls.</span></span> <span data-ttu-id="f187e-161">Эти методы добавляются в следующие разделы.</span><span class="sxs-lookup"><span data-stu-id="f187e-161">These methods are added in the following sections.</span></span> <span data-ttu-id="f187e-162">Каждый метод обновляет соответствующий рабочий процесс угадывания числа и создает `DynamicUpdateMap`.</span><span class="sxs-lookup"><span data-stu-id="f187e-162">Each method updates the corresponding number guess workflow and creates a `DynamicUpdateMap` that describes the updates.</span></span>

    ```vb
    Sub Main()
        'Create the update maps for the changes needed to the v1 activities
        'so they match the v2 activities.
        CreateSequentialUpdateMap()
        CreateFlowchartUpdateMap()
        CreateStateMachineUpdateMap()
    End Sub
    ```

    ```csharp
    static void Main(string[] args)
    {
        // Create the update maps for the changes needed to the v1 activities
        // so they match the v2 activities.
        CreateSequentialUpdateMap();
        CreateFlowchartUpdateMap();
        CreateStateMachineUpdateMap();
    }
    ```

2. <span data-ttu-id="f187e-163">Щелкните правой кнопкой мыши **креатеупдатемапс** в **Обозреватель решений** и выберите **Назначить запускаемым проектом**.</span><span class="sxs-lookup"><span data-stu-id="f187e-163">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

3. <span data-ttu-id="f187e-164">Нажмите сочетание клавиш CTRL+SHIFT+B для сборки решения, а затем нажмите CTRL+F5, чтобы запустить приложение `CreateUpdateMaps`.</span><span class="sxs-lookup"><span data-stu-id="f187e-164">Press CTRL+SHIFT+B to build the solution, and then CTRL+F5 to run the `CreateUpdateMaps` application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f187e-165">`CreateUpdateMaps`Приложение не отображает сведения о состоянии во время выполнения, но если взглянуть на папку **NumberGuessWorkflowActivities_du** и папку **превиаусверсионс** , вы увидите обновленные файлы определения рабочего процесса и карты обновления.</span><span class="sxs-lookup"><span data-stu-id="f187e-165">The `CreateUpdateMaps` application does not display any status information while running, but if you look in the **NumberGuessWorkflowActivities_du** folder and the **PreviousVersions** folder you will see the updated workflow definition files and the update maps.</span></span>

    <span data-ttu-id="f187e-166">После создания схем обновлений и изменения определений рабочего процесса необходимо построить обновленную сборку рабочих процессов с обновленными определениями.</span><span class="sxs-lookup"><span data-stu-id="f187e-166">Once the update maps are created and the workflow definitions updated, the next step is to build an updated workflow assembly containing the updated definitions.</span></span>

### <a name="to-build-the-updated-workflow-assembly"></a><a name="BKMK_BuildAssembly"></a> <span data-ttu-id="f187e-167">Построение обновленной сборки рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="f187e-167">To build the updated workflow assembly</span></span>

1. <span data-ttu-id="f187e-168">Откройте второй экземпляр Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f187e-168">Open a second instance of Visual Studio 2012.</span></span>

2. <span data-ttu-id="f187e-169">В меню **файл** выберите команду **Открыть**, **проект или решение** .</span><span class="sxs-lookup"><span data-stu-id="f187e-169">Choose **Open**, **Project/Solution** from the **File** menu.</span></span>

3. <span data-ttu-id="f187e-170">Перейдите к папке **NumberGuessWorkflowActivities_du** , созданной в окне ["как разместить несколько версий рабочего процесса одновременно](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)", выберите **NumberGuessWorkflowActivities. csproj** (или **VBPROJ**) и нажмите кнопку " **Открыть**".</span><span class="sxs-lookup"><span data-stu-id="f187e-170">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), select **NumberGuessWorkflowActivities.csproj** (or **vbproj**), and click **Open**.</span></span>

4. <span data-ttu-id="f187e-171">В **Обозреватель решений** щелкните правой кнопкой мыши **SequentialNumberGuessWorkflow. XAML** и выберите **исключить из проекта**.</span><span class="sxs-lookup"><span data-stu-id="f187e-171">In **Solution Explorer**, right click **SequentialNumberGuessWorkflow.xaml** and choose **Exclude From Project**.</span></span> <span data-ttu-id="f187e-172">Сделайте то же самое для **FlowchartNumberGuessWorkflow. XAML** и **StateMachineNumberGuessWorkflow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="f187e-172">Do the same thing for **FlowchartNumberGuessWorkflow.xaml** and **StateMachineNumberGuessWorkflow.xaml**.</span></span> <span data-ttu-id="f187e-173">Эта процедура удаляет предыдущие версии определений рабочих процессов из проекта.</span><span class="sxs-lookup"><span data-stu-id="f187e-173">This step removes the previous versions of the workflow definitions from the project.</span></span>

5. <span data-ttu-id="f187e-174">В меню **проект** выберите команду **Добавить существующий элемент** .</span><span class="sxs-lookup"><span data-stu-id="f187e-174">Choose **Add Existing Item** from the **Project** menu.</span></span>

6. <span data-ttu-id="f187e-175">Перейдите к папке **NumberGuessWorkflowActivities_du** , созданной в окне ["как разместить несколько версий рабочего процесса одновременно"](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="f187e-175">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

7. <span data-ttu-id="f187e-176">Выберите **XAML-файлы ( \* . XAML; \* . XOML)** из раскрывающегося списка **файлы типа** .</span><span class="sxs-lookup"><span data-stu-id="f187e-176">Choose **XAML Files (\*.xaml;\*.xoml)** from the **Files of type** drop-down list.</span></span>

8. <span data-ttu-id="f187e-177">Выберите **SequentialNumberGuessWorkflow_du. XAML**, **FlowchartNumberGuessWorkflow_du. XAML** и **StateMachineNumberGuessWorkflow_du. XAML** и нажмите кнопку **Добавить**.</span><span class="sxs-lookup"><span data-stu-id="f187e-177">Select **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, and **StateMachineNumberGuessWorkflow_du.xaml** and click **Add**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f187e-178">Чтобы выбрать несколько элементов одновременно, при нажатии левой кнопки мыши удерживайте нажатой клавишу CTRL.</span><span class="sxs-lookup"><span data-stu-id="f187e-178">CTRL+Click to select multiple items at a time.</span></span>

    <span data-ttu-id="f187e-179">Это действие добавит обновленные версии определений рабочих процессов в проект.</span><span class="sxs-lookup"><span data-stu-id="f187e-179">This step adds the updated versions of the workflow definitions to the project.</span></span>

9. <span data-ttu-id="f187e-180">Для сборки проекта нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="f187e-180">Press CTRL+SHIFT+B to build the project.</span></span>

10. <span data-ttu-id="f187e-181">В меню **файл** выберите пункт **Закрыть решение** .</span><span class="sxs-lookup"><span data-stu-id="f187e-181">Choose **Close Solution** from the **File** menu.</span></span> <span data-ttu-id="f187e-182">Файл решения для проекта не является обязательным, поэтому нажмите кнопку " **нет** ", чтобы закрыть Visual Studio без сохранения файла решения.</span><span class="sxs-lookup"><span data-stu-id="f187e-182">A solution file for the project is not required, so click **No** to close Visual Studio without saving a solution file.</span></span> <span data-ttu-id="f187e-183">В меню **файл** выберите команду **выход** , чтобы закрыть Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f187e-183">Choose **Exit** from the **File** menu to close Visual Studio.</span></span>

11. <span data-ttu-id="f187e-184">Откройте проводник Windows и перейдите в папку **NumberGuessWorkflowActivities_du \bin\Debug** (или **Bin\Release** в зависимости от параметров проекта).</span><span class="sxs-lookup"><span data-stu-id="f187e-184">Open Windows Explorer and navigate to the **NumberGuessWorkflowActivities_du\bin\Debug** folder (or **bin\Release** depending on your project settings).</span></span>

12. <span data-ttu-id="f187e-185">Переименуйте **NumberGuessWorkflowActivities.dll** в **NumberGuessWorkflowActivities_v15.dll** и скопируйте его в папку **превиаусверсионс** , созданную в окне " [как разместить несколько версий рабочего процесса одновременно"](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="f187e-185">Rename **NumberGuessWorkflowActivities.dll** to **NumberGuessWorkflowActivities_v15.dll**, and copy it to the **PreviousVersions** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

### <a name="to-update-workflowversionmap-with-the-new-versions"></a><a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="f187e-186">Обновление WorkflowVersionMap с использованием новых версий</span><span class="sxs-lookup"><span data-stu-id="f187e-186">To update WorkflowVersionMap with the new versions</span></span>

1. <span data-ttu-id="f187e-187">Вернитесь к первоначальному экземпляру Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f187e-187">Switch back to the initial instance of Visual Studio 2012.</span></span>

2. <span data-ttu-id="f187e-188">Дважды щелкните **WorkflowVersionMap.CS** (или **WorkflowVersionMap. vb**) в проекте **NumberGuessWorkflowHost** , чтобы открыть его.</span><span class="sxs-lookup"><span data-stu-id="f187e-188">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

3. <span data-ttu-id="f187e-189">Добавьте три новых идентификатора рабочих процессов непосредственно под шестью имеющимися объявлениями идентификаторов рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="f187e-189">Add three new workflow identities just below the six existing workflow identity declarations.</span></span> <span data-ttu-id="f187e-190">В данном учебнике `1.5.0.0` используется в качестве `WorkflowIdentity.Version` для идентификаторов динамического обновления.</span><span class="sxs-lookup"><span data-stu-id="f187e-190">In this tutorial, `1.5.0.0` is used as the `WorkflowIdentity.Version` for the dynamic update identities.</span></span> <span data-ttu-id="f187e-191">Эти новые идентификаторы `v15` будут использоваться для указания правильного определения динамически сохраняемых экземпляров рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="f187e-191">These new `v15` workflow identities will be used provide the correct workflow definition for the dynamically updated persisted workflow instances.</span></span>

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

    'v1.5 (Dynamic Update) identities.
    Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity
    ```

    ```csharp
    // Current version identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity;
    static public WorkflowIdentity FlowchartNumberGuessIdentity;
    static public WorkflowIdentity SequentialNumberGuessIdentity;

    // v1 identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

    // v1.5 (Dynamic Update) identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v15;
    ```

4. <span data-ttu-id="f187e-192">В конце конструктора добавьте следующий код.</span><span class="sxs-lookup"><span data-stu-id="f187e-192">Add the following code at the end of the constructor.</span></span> <span data-ttu-id="f187e-193">Этот код инициализирует идентификаторы рабочих процессов с динамическим обновлением, загружает соответствующие определения и добавляет их в словарь версий рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="f187e-193">This code initializes the dynamic update workflow identities, loads the corresponding workflow definitions, and adds them to the workflow version dictionary.</span></span>

    ```vb
    'Initialize the dynamic update workflow identities.
    StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    'Add the dynamic update workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v15 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)
    Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Initialize the dynamic update workflow identities.
    StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    SequentialNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    // Add the dynamic update workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v15 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);
    Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

     <span data-ttu-id="f187e-194">В следующем примере продемонстрирован в завершенном виде класс `WorkflowVersionMap`.</span><span class="sxs-lookup"><span data-stu-id="f187e-194">The following example is the completed `WorkflowVersionMap` class.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        'v1.5 (Dynamic Update) identities.
        Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            'Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())

            'Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            'Add the previous version workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v1 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))

            'Initialize the dynamic update workflow identities.
            StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            'Add the dynamic update workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v15 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)
            Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
        End Sub

        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity
            Return map(identity)
        End Function

        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String
            Return identity.ToString()
        End Function
    End Module
    ```

    ```csharp
    public static class WorkflowVersionMap
    {
        static Dictionary<WorkflowIdentity, Activity> map;

        // Current version identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity;
        static public WorkflowIdentity FlowchartNumberGuessIdentity;
        static public WorkflowIdentity SequentialNumberGuessIdentity;

        // v1 identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

        // v1.5 (Dynamic Update) identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v15;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());

            // Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            // Add the previous version workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v1 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);

            // Initialize the dynamic update workflow identities.
            StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            SequentialNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            // Add the dynamic update workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v15 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);
            Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
        }

        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)
        {
            return map[identity];
        }

        public static string GetIdentityDescription(WorkflowIdentity identity)
        {
            return identity.ToString();
        }
    }
    ```

5. <span data-ttu-id="f187e-195">Для сборки проекта нажмите CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="f187e-195">Press CTRL+SHIFT+B to build the project.</span></span>

### <a name="to-apply-the-dynamic-updates"></a><a name="BKMK_ApplyUpdate"></a> <span data-ttu-id="f187e-196">Применение динамических обновлений</span><span class="sxs-lookup"><span data-stu-id="f187e-196">To apply the dynamic updates</span></span>

1. <span data-ttu-id="f187e-197">Щелкните правой кнопкой мыши **WF45GettingStartedTutorial** в **Обозреватель решений** и выберите **добавить**, **Новый проект**.</span><span class="sxs-lookup"><span data-stu-id="f187e-197">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>

2. <span data-ttu-id="f187e-198">На узле **установленные** выберите **Visual C#**, **Windows** (или **Visual Basic**, **Windows**).</span><span class="sxs-lookup"><span data-stu-id="f187e-198">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="f187e-199">В зависимости от основного используемого языка программирования Visual Studio узел **Visual C#** или **Visual Basic** может располагаться в узле **Другие языки** под узлом **Установлено**.</span><span class="sxs-lookup"><span data-stu-id="f187e-199">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

    <span data-ttu-id="f187e-200">Убедитесь, что в раскрывающемся списке версий .NET Framework выбран пункт **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="f187e-200">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="f187e-201">Выберите **консольное приложение** в списке **Windows** .</span><span class="sxs-lookup"><span data-stu-id="f187e-201">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="f187e-202">Введите **узел applydynamicupdate** в поле **имя** и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="f187e-202">Type **ApplyDynamicUpdate** into the **Name** box and click **OK**.</span></span>

3. <span data-ttu-id="f187e-203">Щелкните правой кнопкой мыши **узел applydynamicupdate** в **Обозреватель решений** и выберите команду **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="f187e-203">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Add Reference**.</span></span>

4. <span data-ttu-id="f187e-204">Щелкните **решение** и установите флажок рядом с **NumberGuessWorkflowHost**.</span><span class="sxs-lookup"><span data-stu-id="f187e-204">Click **Solution** and check the box next to **NumberGuessWorkflowHost**.</span></span> <span data-ttu-id="f187e-205">Эта ссылка не требуется для того, чтобы `ApplyDynamicUpdate` мог использовать класс `NumberGuessWorkflowHost.WorkflowVersionMap`.</span><span class="sxs-lookup"><span data-stu-id="f187e-205">This reference is needed so that `ApplyDynamicUpdate` can use the `NumberGuessWorkflowHost.WorkflowVersionMap` class.</span></span>

5. <span data-ttu-id="f187e-206">Выберите **платформа** из узла **сборки** в списке **Добавить ссылку** .</span><span class="sxs-lookup"><span data-stu-id="f187e-206">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="f187e-207">Введите **System. activitys** в поле **Поиск сборок** .</span><span class="sxs-lookup"><span data-stu-id="f187e-207">Type **System.Activities** into the **Search Assemblies** box.</span></span> <span data-ttu-id="f187e-208">При этом будут отфильтрованы сборки и станет легче выбрать необходимые ссылки.</span><span class="sxs-lookup"><span data-stu-id="f187e-208">This will filter the assemblies and make the desired references easier to select.</span></span>

6. <span data-ttu-id="f187e-209">Установите флажок рядом с элементом **System. activitys** из списка **результатов поиска** .</span><span class="sxs-lookup"><span data-stu-id="f187e-209">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>

7. <span data-ttu-id="f187e-210">Введите **сериализацию** в поле **Поиск сборок** и установите флажок рядом с элементом **System. Runtime. Serialization** в списке **результатов поиска** .</span><span class="sxs-lookup"><span data-stu-id="f187e-210">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>

8. <span data-ttu-id="f187e-211">Введите **DurableInstancing** в поле **Поиск сборок** и установите флажок рядом с элементом **System. activitys. DurableInstancing** и **System. Runtime. DurableInstancing** из списка **результатов поиска** .</span><span class="sxs-lookup"><span data-stu-id="f187e-211">Type **DurableInstancing** into the **Search Assemblies** box, and check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list.</span></span>

9. <span data-ttu-id="f187e-212">Нажмите кнопку **ОК** , чтобы закрыть **Диспетчер ссылок** и добавить ссылки.</span><span class="sxs-lookup"><span data-stu-id="f187e-212">Click **OK** to close **Reference Manager** and add the references.</span></span>

10. <span data-ttu-id="f187e-213">Щелкните правой кнопкой мыши **узел applydynamicupdate** в Обозреватель решений и выберите **Добавить**, **класс**.</span><span class="sxs-lookup"><span data-stu-id="f187e-213">Right-click **ApplyDynamicUpdate** in Solution Explorer and choose **Add**, **Class**.</span></span> <span data-ttu-id="f187e-214">Введите `DynamicUpdateInfo` в поле **имя** и нажмите кнопку **добавить**.</span><span class="sxs-lookup"><span data-stu-id="f187e-214">Type `DynamicUpdateInfo` into the **Name** box and click **Add**.</span></span>

11. <span data-ttu-id="f187e-215">Добавьте следующие два члена в класс `DynamicUpdateInfo`.</span><span class="sxs-lookup"><span data-stu-id="f187e-215">Add the following two members to the `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="f187e-216">В следующем примере продемонстрирован в завершенном виде класс `DynamicUpdateInfo`.</span><span class="sxs-lookup"><span data-stu-id="f187e-216">The following example is the completed `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="f187e-217">Этот класс содержит сведения о схеме обновления и новом идентификаторе, который используется при обновлении экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="f187e-217">This class contains information on the update map and new workflow identity used when a workflow instance is updated.</span></span>

    ```vb
    Public Class DynamicUpdateInfo
        Public updateMap As DynamicUpdateMap
        Public newIdentity As WorkflowIdentity
    End Class
    ```

    ```csharp
    class DynamicUpdateInfo
    {
        public DynamicUpdateMap updateMap;
        public WorkflowIdentity newIdentity;
    }
    ```

12. <span data-ttu-id="f187e-218">Добавьте следующие инструкции `using` (или `Imports`) в начало файла с другими инструкциями `using` (или `Imports`).</span><span class="sxs-lookup"><span data-stu-id="f187e-218">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.DynamicUpdate
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DynamicUpdate;
    ```

13. <span data-ttu-id="f187e-219">Дважды щелкните **Program.CS** (или **Module1. vb**) в Обозреватель решений.</span><span class="sxs-lookup"><span data-stu-id="f187e-219">Double-click **Program.cs** (or **Module1.vb**) in Solution Explorer.</span></span>

14. <span data-ttu-id="f187e-220">Добавьте следующие инструкции `using` (или `Imports`) в начало файла с другими инструкциями `using` (или `Imports`).</span><span class="sxs-lookup"><span data-stu-id="f187e-220">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowHost
    Imports System.Data.SqlClient
    Imports System.Activities.DynamicUpdate
    Imports System.IO
    Imports System.Runtime.Serialization
    Imports System.Activities
    Imports System.Activities.DurableInstancing
    ```

    ```csharp
    using NumberGuessWorkflowHost;
    using System.Data;
    using System.Data.SqlClient;
    using System.Activities;
    using System.Activities.DynamicUpdate;
    using System.IO;
    using System.Runtime.Serialization;
    using System.Activities.DurableInstancing;
    ```

15. <span data-ttu-id="f187e-221">Добавьте следующий член строки подключения в класс `Program` (или `Module1`).</span><span class="sxs-lookup"><span data-stu-id="f187e-221">Add the following connection string member to the `Program` class (or `Module1`).</span></span>

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    ```

    > [!NOTE]
    > <span data-ttu-id="f187e-222">В строке подключения могут указываться различные имена серверов в зависимости от выпуска SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f187e-222">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

16. <span data-ttu-id="f187e-223">Добавьте в класс `GetIDs` (`Program`) следующий метод `Module1`.</span><span class="sxs-lookup"><span data-stu-id="f187e-223">Add the following `GetIDs` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="f187e-224">Этот метод возвращает список сохраненных идентификаторов экземпляров рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="f187e-224">This method returns a list of persisted workflow instance ids.</span></span>

    ```vb
    Function GetIds() As IList(Of Guid)
        Dim Ids As New List(Of Guid)
        Dim localCmd = _
            String.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]")
        Using localCon = New SqlConnection(connectionString)
            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)
                While reader.Read()
                    'Get the InstanceId of the persisted Workflow
                    Dim id As Guid = Guid.Parse(reader(0).ToString())

                    'Add it to the list.
                    Ids.Add(id)
                End While
            End Using
        End Using

        Return Ids
    End Function
    ```

    ```csharp
    static IList<Guid> GetIds()
    {
        List<Guid> Ids = new List<Guid>();
        string localCmd = string.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]");
        using (SqlConnection localCon = new SqlConnection(connectionString))
        {
            SqlCommand cmd = localCon.CreateCommand();
            cmd.CommandText = localCmd;
            localCon.Open();
            using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
            {
                while (reader.Read())
                {
                    // Get the InstanceId of the persisted Workflow
                    Guid id = Guid.Parse(reader[0].ToString());

                    // Add it to the list.
                    Ids.Add(id);
                }
            }
        }

        return Ids;
    }
    ```

17. <span data-ttu-id="f187e-225">Добавьте в класс `LoadMap` (`Program`) следующий метод `Module1`.</span><span class="sxs-lookup"><span data-stu-id="f187e-225">Add the following `LoadMap` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="f187e-226">Этот метод создает словарь, который сопоставляет идентификаторы рабочих процессов `v1` со схемами обновления и новыми идентификаторами, которые используются для обновления соответствующих экземпляров сохраненных рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="f187e-226">This method creates a dictionary that maps `v1` workflow identities to the update maps and new workflow identities used to update the corresponding persisted workflow instances.</span></span>

    ```vb
    Function LoadMap(mapName As String) As DynamicUpdateMap
        Dim mapPath As String = Path.Combine("..\..\..\PreviousVersions", mapName)

        Dim map As DynamicUpdateMap
        Using fs As FileStream = File.Open(mapPath, FileMode.Open)
            Dim serializer As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))
            Dim updateMap = serializer.ReadObject(fs)
            If updateMap Is Nothing Then
                Throw New ApplicationException("DynamicUpdateMap is null.")
            End If

            map = updateMap
        End Using

        Return map
    End Function
    ```

    ```csharp
    static DynamicUpdateMap LoadMap(string mapName)
    {
        string path = Path.Combine(@"..\..\..\PreviousVersions", mapName);

        DynamicUpdateMap map;
        using (FileStream fs = File.Open(path, FileMode.Open))
        {
            DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
            object updateMap = serializer.ReadObject(fs);
            if (updateMap == null)
            {
                throw new ApplicationException("DynamicUpdateMap is null.");
            }

            map = updateMap as DynamicUpdateMap;
        }

        return map;
    }
    ```

18. <span data-ttu-id="f187e-227">Добавьте в класс `LoadMaps` (`Program`) следующий метод `Module1`.</span><span class="sxs-lookup"><span data-stu-id="f187e-227">Add the following `LoadMaps` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="f187e-228">Этот метод загружает три схемы обновления и создает словарь, сопоставляющий идентификаторы рабочего процесса `v1` со схемами обновлений.</span><span class="sxs-lookup"><span data-stu-id="f187e-228">This method loads the three update maps and creates a dictionary that maps `v1` workflow identities to the update maps.</span></span>

    ```vb
    Function LoadMaps() As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo)
        'There are 3 update maps to describe the changes to update v1 workflows,
        'one for reach of the 3 workflow types in the tutorial.
        Dim maps = New Dictionary(Of WorkflowIdentity, DynamicUpdateInfo)()

        Dim sequentialMap As DynamicUpdateMap = LoadMap("SequentialNumberGuessWorkflow.map")
        Dim sequentialInfo = New DynamicUpdateInfo With
        {
            .updateMap = sequentialMap,
            .newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo)

        Dim stateMap As DynamicUpdateMap = LoadMap("StateMachineNumberGuessWorkflow.map")
        Dim stateInfo = New DynamicUpdateInfo With
        {
            .updateMap = stateMap,
            .newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo)

        Dim flowchartMap As DynamicUpdateMap = LoadMap("FlowchartNumberGuessWorkflow.map")
        Dim flowchartInfo = New DynamicUpdateInfo With
        {
            .updateMap = flowchartMap,
            .newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo)

        Return maps
    End Function
    ```

    ```csharp
    static IDictionary<WorkflowIdentity, DynamicUpdateInfo> LoadMaps()
    {
        // There are 3 update maps to describe the changes to update v1 workflows,
        // one for reach of the 3 workflow types in the tutorial.
        Dictionary<WorkflowIdentity, DynamicUpdateInfo> maps =
            new Dictionary<WorkflowIdentity, DynamicUpdateInfo>();

        DynamicUpdateMap sequentialMap = LoadMap("SequentialNumberGuessWorkflow.map");
        DynamicUpdateInfo sequentialInfo = new DynamicUpdateInfo
        {
            updateMap = sequentialMap,
            newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo);

        DynamicUpdateMap stateMap = LoadMap("StateMachineNumberGuessWorkflow.map");
        DynamicUpdateInfo stateInfo = new DynamicUpdateInfo
        {
            updateMap = stateMap,
            newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo);

        DynamicUpdateMap flowchartMap = LoadMap("FlowchartNumberGuessWorkflow.map");
        DynamicUpdateInfo flowchartInfo = new DynamicUpdateInfo
        {
            updateMap = flowchartMap,
            newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo);

        return maps;
    }
    ```

19. <span data-ttu-id="f187e-229">Добавьте в раздел `Main` следующий код.</span><span class="sxs-lookup"><span data-stu-id="f187e-229">Add the following code to `Main`.</span></span> <span data-ttu-id="f187e-230">Этот код выполняет итерацию по сохраненным экземплярам рабочих процессов и проверяет каждый идентификатор `WorkflowIdentity`.</span><span class="sxs-lookup"><span data-stu-id="f187e-230">This code iterates the persisted workflow instances and examines each `WorkflowIdentity`.</span></span> <span data-ttu-id="f187e-231">Если `WorkflowIdentity` сопоставляется с экземпляром рабочего процесса `v1`, к `WorkflowApplication` применяются обновленное определение рабочего процесса и обновленный идентификатор.</span><span class="sxs-lookup"><span data-stu-id="f187e-231">If the `WorkflowIdentity` maps to a `v1` workflow instance, a `WorkflowApplication` is configured with the updated workflow definition and an updated workflow identity.</span></span> <span data-ttu-id="f187e-232">Затем вызывается метод `WorkflowApplication.Load` с экземпляром и схемой обновления, который применяет схему.</span><span class="sxs-lookup"><span data-stu-id="f187e-232">Next, `WorkflowApplication.Load` is called with the instance and the update map, which applies the dynamic update map.</span></span> <span data-ttu-id="f187e-233">После обновления измененный экземпляр сохраняется методом `Unload`.</span><span class="sxs-lookup"><span data-stu-id="f187e-233">Once the update is applied, the updated instance is persisted with a call to `Unload`.</span></span>

    ```vb
    Dim store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    Dim updateMaps As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo) = LoadMaps()

    For Each id As Guid In GetIds()
        'Get a proxy to the instance.
        Dim instance As WorkflowApplicationInstance = WorkflowApplication.GetInstance(id, store)

        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity)

        'Only update v1 workflows.
        If Not instance.DefinitionIdentity Is Nothing AndAlso _
            instance.DefinitionIdentity.Version.Equals(New Version(1, 0, 0, 0)) Then

            Dim info As DynamicUpdateInfo = updateMaps(instance.DefinitionIdentity)

            'Associate the persisted WorkflowApplicationInstance with
            'a WorkflowApplication that is configured with the updated
            'definition and updated WorkflowIdentity.
            Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity)
            Dim wfApp = New WorkflowApplication(wf, info.newIdentity)

            'Apply the Dynamic Update.
            wfApp.Load(instance, info.updateMap)

            'Persist the updated instance.
            wfApp.Unload()

            Console.WriteLine("Updated to: {0}", info.newIdentity)
        Else
            'Not updating this instance, so unload it.
            instance.Abandon()
        End If
    Next
    ```

    ```csharp
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);

    IDictionary<WorkflowIdentity, DynamicUpdateInfo> updateMaps = LoadMaps();

    foreach (Guid id in GetIds())
    {
        // Get a proxy to the instance.
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(id, store);

        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity);

        // Only update v1 workflows.
        if (instance.DefinitionIdentity != null &&
            instance.DefinitionIdentity.Version.Equals(new Version(1, 0, 0, 0)))
        {
            DynamicUpdateInfo info = updateMaps[instance.DefinitionIdentity];

            // Associate the persisted WorkflowApplicationInstance with
            // a WorkflowApplication that is configured with the updated
            // definition and updated WorkflowIdentity.
            Activity wf = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity);
            WorkflowApplication wfApp =
                new WorkflowApplication(wf, info.newIdentity);

            // Apply the Dynamic Update.
            wfApp.Load(instance, info.updateMap);

            // Persist the updated instance.
            wfApp.Unload();

            Console.WriteLine("Updated to: {0}", info.newIdentity);
        }
        else
        {
            // Not updating this instance, so unload it.
            instance.Abandon();
        }
    }
    ```

20. <span data-ttu-id="f187e-234">Щелкните правой кнопкой мыши **узел applydynamicupdate** в **Обозреватель решений** и выберите **Назначить запускаемым проектом**.</span><span class="sxs-lookup"><span data-stu-id="f187e-234">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

21. <span data-ttu-id="f187e-235">Нажмите сочетание клавиш CTRL+SHIFT+B для сборки решения, затем сочетание клавиш Ctrl+F5 для запуска приложения `ApplyDynamicUpdate` и обновления экземпляров сохраненных рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="f187e-235">Press CTRL+SHIFT+B to build the solution, and then press CTRL+F5 to run the `ApplyDynamicUpdate` application and update the persisted workflow instances.</span></span> <span data-ttu-id="f187e-236">Вы должны увидеть результат, аналогичный приведенному ниже.</span><span class="sxs-lookup"><span data-stu-id="f187e-236">You should see output similar to the following.</span></span> <span data-ttu-id="f187e-237">Рабочие процессы версии 1.0.0.0 обновлены до версии 1.5.0.0, а рабочие процессы версии 2.0.0.0 не обновлены.</span><span class="sxs-lookup"><span data-stu-id="f187e-237">The version 1.0.0.0 workflows are updated to version 1.5.0.0, while the version 2.0.0.0 workflows are not updated.</span></span>

    <span data-ttu-id="f187e-238">**Проверка: StateMachineNumberGuessWorkflow; Версия = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-238">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="f187e-239">**Обновлено на: StateMachineNumberGuessWorkflow; Версия = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-239">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="f187e-240">**Проверка: StateMachineNumberGuessWorkflow; Версия = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-240">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="f187e-241">**Обновлено на: StateMachineNumberGuessWorkflow; Версия = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-241">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="f187e-242">**Проверка: FlowchartNumberGuessWorkflow; Версия = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-242">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="f187e-243">**Обновлено на: FlowchartNumberGuessWorkflow; Версия = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-243">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="f187e-244">**Проверка: FlowchartNumberGuessWorkflow; Версия = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-244">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="f187e-245">**Обновлено на: FlowchartNumberGuessWorkflow; Версия = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-245">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="f187e-246">**Проверка: SequentialNumberGuessWorkflow; Версия = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-246">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="f187e-247">**Обновлено на: SequentialNumberGuessWorkflow; Версия = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-247">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="f187e-248">**Проверка: SequentialNumberGuessWorkflow; Версия = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-248">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="f187e-249">**Обновлено на: SequentialNumberGuessWorkflow; Версия = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-249">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="f187e-250">**Проверка: SequentialNumberGuessWorkflow; Версия = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-250">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="f187e-251">**Обновлено на: SequentialNumberGuessWorkflow; Версия = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-251">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="f187e-252">**Проверка: StateMachineNumberGuessWorkflow; Версия = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-252">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="f187e-253">**Обновлено на: StateMachineNumberGuessWorkflow; Версия = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-253">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="f187e-254">**Проверка: FlowchartNumberGuessWorkflow; Версия = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-254">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="f187e-255">**Обновлено на: FlowchartNumberGuessWorkflow; Версия = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-255">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="f187e-256">**Проверка: StateMachineNumberGuessWorkflow; Версия = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-256">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="f187e-257">**Проверка: StateMachineNumberGuessWorkflow; Версия = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-257">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="f187e-258">**Проверка: FlowchartNumberGuessWorkflow; Версия = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-258">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="f187e-259">**Проверка: FlowchartNumberGuessWorkflow; Версия = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-259">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="f187e-260">**Проверка: SequentialNumberGuessWorkflow; Версия = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-260">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="f187e-261">**Проверка: SequentialNumberGuessWorkflow; Версия = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="f187e-261">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="f187e-262">**Чтобы продолжить, нажмите любую клавишу...**</span><span class="sxs-lookup"><span data-stu-id="f187e-262">**Press any key to continue . . .**</span></span>

### <a name="to-run-the-application-with-the-updated-workflows"></a><a name="BKMK_BuildAndRun"></a> <span data-ttu-id="f187e-263">Запуск приложения с обновленными рабочими процессами</span><span class="sxs-lookup"><span data-stu-id="f187e-263">To run the application with the updated workflows</span></span>

1. <span data-ttu-id="f187e-264">Щелкните правой кнопкой мыши **NumberGuessWorkflowHost** в **Обозреватель решений** и выберите **Назначить запускаемым проектом**.</span><span class="sxs-lookup"><span data-stu-id="f187e-264">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

2. <span data-ttu-id="f187e-265">Для запуска приложения нажмите сочетание клавиш CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="f187e-265">Press CTRL+F5 to run the application.</span></span>

3. <span data-ttu-id="f187e-266">Щелкните **Новая игра** , чтобы запустить новый рабочий процесс, и обратите внимание на сведения о версии в окне состояния, которое указывает, что рабочий процесс является `v2` рабочим процессом.</span><span class="sxs-lookup"><span data-stu-id="f187e-266">Click **New Game** to start a new workflow and note the version information below the status window that indicates the workflow is a `v2` workflow.</span></span>

4. <span data-ttu-id="f187e-267">Выберите один из `v1` рабочих процессов, которые вы начали в начале статьи [как разместить несколько версий рабочего процесса параллельно](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) .</span><span class="sxs-lookup"><span data-stu-id="f187e-267">Select one of the `v1` workflows you started at the beginning of the [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) topic.</span></span> <span data-ttu-id="f187e-268">Обратите внимание, что сведения о версии в окне состояния указывают на то, что рабочий процесс является рабочим процессом **1.5.0.0** версии.</span><span class="sxs-lookup"><span data-stu-id="f187e-268">Note that the version information under the status window indicates that the workflow is a version **1.5.0.0** workflow.</span></span> <span data-ttu-id="f187e-269">Следует отметить, что сведения о предыдущих догадках не отображаются; показано только то, оказались они больше или меньше нужного значения.</span><span class="sxs-lookup"><span data-stu-id="f187e-269">Note that there is no information indicated about previous guesses other than whether they were too high or too low.</span></span>

    <span data-ttu-id="f187e-270">**Введите число от 1 до 10**</span><span class="sxs-lookup"><span data-stu-id="f187e-270">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="f187e-271">**Загаданное число больше.**</span><span class="sxs-lookup"><span data-stu-id="f187e-271">**Your guess is too low.**</span></span>

5. <span data-ttu-id="f187e-272">Запишите `InstanceId`, затем вводите догадки, пока рабочий процесс не будет завершен.</span><span class="sxs-lookup"><span data-stu-id="f187e-272">Make a note of the `InstanceId` and then enter guesses until the workflow completes.</span></span> <span data-ttu-id="f187e-273">В окне состояния отображаются сведения о содержимом догадок, поскольку действия `WriteLine` были обновлены с помощью динамического обновления.</span><span class="sxs-lookup"><span data-stu-id="f187e-273">The status window displays information about the content of the guess because the `WriteLine` activities were updated by the dynamic update.</span></span>

    <span data-ttu-id="f187e-274">**Введите число от 1 до 10**</span><span class="sxs-lookup"><span data-stu-id="f187e-274">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="f187e-275">**Предполагаемое предположение слишком мало.**</span><span class="sxs-lookup"><span data-stu-id="f187e-275">**Your guess is too low.**</span></span>\
    <span data-ttu-id="f187e-276">**Введите число от 1 до 10**</span><span class="sxs-lookup"><span data-stu-id="f187e-276">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="f187e-277">**5 является слишком низким.**</span><span class="sxs-lookup"><span data-stu-id="f187e-277">**5 is too low.**</span></span>\
    <span data-ttu-id="f187e-278">**Введите число от 1 до 10**</span><span class="sxs-lookup"><span data-stu-id="f187e-278">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="f187e-279">**7 слишком высокий.**</span><span class="sxs-lookup"><span data-stu-id="f187e-279">**7 is too high.**</span></span>\
    <span data-ttu-id="f187e-280">**Введите число от 1 до 10**</span><span class="sxs-lookup"><span data-stu-id="f187e-280">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="f187e-281">**Поздравляем! Вы угадали число за 4 попытки.**</span><span class="sxs-lookup"><span data-stu-id="f187e-281">**Congratulations, you guessed the number in 4 turns.**</span></span>

6. <span data-ttu-id="f187e-282">Откройте проводник Windows и перейдите в папку **нумбергуессворкфловхост\бин\дебуг** (или **Bin\Release** в зависимости от параметров проекта) и откройте файл отслеживания с помощью блокнота, который соответствует завершенному рабочему процессу.</span><span class="sxs-lookup"><span data-stu-id="f187e-282">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="f187e-283">Если вы не запустили заметку, `InstanceId` вы можете найти правильный файл отслеживания, используя сведения об **изменении даты** в проводнике Windows.</span><span class="sxs-lookup"><span data-stu-id="f187e-283">If you did not make a note of the `InstanceId` you may be able to identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span> <span data-ttu-id="f187e-284">Последняя строка данных отслеживания содержит данные только что добавленного действия `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="f187e-284">The last line of the tracking information contains the output of the newly added `WriteLine` activity.</span></span>

    <span data-ttu-id="f187e-285">**Введите число от 1 до 10**</span><span class="sxs-lookup"><span data-stu-id="f187e-285">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="f187e-286">**Предполагаемое предположение слишком мало.**</span><span class="sxs-lookup"><span data-stu-id="f187e-286">**Your guess is too low.**</span></span>\
    <span data-ttu-id="f187e-287">**Введите число от 1 до 10**</span><span class="sxs-lookup"><span data-stu-id="f187e-287">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="f187e-288">**5 является слишком низким.**</span><span class="sxs-lookup"><span data-stu-id="f187e-288">**5 is too low.**</span></span>\
    <span data-ttu-id="f187e-289">**Введите число от 1 до 10**</span><span class="sxs-lookup"><span data-stu-id="f187e-289">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="f187e-290">**7 слишком высокий.**</span><span class="sxs-lookup"><span data-stu-id="f187e-290">**7 is too high.**</span></span>\
    <span data-ttu-id="f187e-291">**Введите число от 1 до 10**</span><span class="sxs-lookup"><span data-stu-id="f187e-291">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="f187e-292">**6 является правильным. Вы догадались его в 4.**</span><span class="sxs-lookup"><span data-stu-id="f187e-292">**6 is correct. You guessed it in 4 turns.**</span></span>

### <a name="to-enable-starting-previous-versions-of-the-workflows"></a><a name="BKMK_StartPreviousVersions"></a> <span data-ttu-id="f187e-293">Включение запуска предыдущих версий рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="f187e-293">To enable starting previous versions of the workflows</span></span>

<span data-ttu-id="f187e-294">Если больше нет рабочих процессов для обновления, можно изменить приложение `NumberGuessWorkflowHost`, чтобы разрешить запуск предыдущих версий рабочих процессов.</span><span class="sxs-lookup"><span data-stu-id="f187e-294">If you run out of workflows to update, you can modify the `NumberGuessWorkflowHost` application to enable starting previous versions of the workflows.</span></span>

1. <span data-ttu-id="f187e-295">Дважды щелкните **воркфловхостформ** в **Обозреватель решений** и выберите поле со списком **воркфловтипе** .</span><span class="sxs-lookup"><span data-stu-id="f187e-295">Double-click **WorkflowHostForm** in **Solution Explorer**, and select the **WorkflowType** combo box.</span></span>

2. <span data-ttu-id="f187e-296">В окне **Свойства** выберите свойство **Items** и нажмите кнопку с многоточием, чтобы изменить коллекцию **Items** .</span><span class="sxs-lookup"><span data-stu-id="f187e-296">In the **Properties** window, select the **Items** property and click the ellipsis button to edit the **Items** collection.</span></span>

3. <span data-ttu-id="f187e-297">Добавьте в коллекцию следующие три элемента.</span><span class="sxs-lookup"><span data-stu-id="f187e-297">Add the following three items to the collection.</span></span>

    ```
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

    <span data-ttu-id="f187e-298">Коллекция `Items` будет иметь шесть элементов.</span><span class="sxs-lookup"><span data-stu-id="f187e-298">The completed `Items` collection will have six items.</span></span>

    ```
    StateMachineNumberGuessWorkflow
    FlowchartNumberGuessWorkflow
    SequentialNumberGuessWorkflow
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

4. <span data-ttu-id="f187e-299">Дважды щелкните **воркфловхостформ** в **Обозреватель решений** и выберите **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="f187e-299">Double-click **WorkflowHostForm** in **Solution Explorer**, and select **View Code**.</span></span>

5. <span data-ttu-id="f187e-300">Добавьте три новых варианта в `switch` оператор (или `Select Case` ) в `NewGame_Click` обработчике, чтобы связать новые элементы в поле со списком **воркфловтипе** с соответствующими идентификаторами рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="f187e-300">Add three new cases to the `switch` (or `Select Case`) statement in the `NewGame_Click` handler to map the new items in the **WorkflowType** combo box to the matching workflow identities.</span></span>

    ```vb
    Case "SequentialNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1

    Case "StateMachineNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1

    Case "FlowchartNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1
    ```

    ```csharp
    case "SequentialNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;
        break;

    case "StateMachineNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;
        break;

    case "FlowchartNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;
        break;
    ```

    <span data-ttu-id="f187e-301">Следующий пример содержит полную инструкцию `switch` (или `Select Case`).</span><span class="sxs-lookup"><span data-stu-id="f187e-301">The following example contains the complete `switch` (or `Select Case`) statement.</span></span>

    ```vb
    Select Case WorkflowType.SelectedItem.ToString()
        Case "SequentialNumberGuessWorkflow"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity

        Case "StateMachineNumberGuessWorkflow"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity

        Case "FlowchartNumberGuessWorkflow"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity

        Case "SequentialNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1

        Case "StateMachineNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1

        Case "FlowchartNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1
    End Select
    ```

    ```csharp
    switch (WorkflowType.SelectedItem.ToString())
    {
        case "SequentialNumberGuessWorkflow":
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;
            break;

        case "StateMachineNumberGuessWorkflow":
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;
            break;

        case "FlowchartNumberGuessWorkflow":
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;
            break;

        case "SequentialNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;
            break;

        case "StateMachineNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;
            break;

        case "FlowchartNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;
            break;
    };
    ```

6. <span data-ttu-id="f187e-302">Нажмите клавиши CTRL+F5 для сборки и запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="f187e-302">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="f187e-303">Теперь можно запустить версии `v1` рабочего процесса, так же как и текущие версии.</span><span class="sxs-lookup"><span data-stu-id="f187e-303">You can now start the `v1` versions of the workflow as well as the current versions.</span></span> <span data-ttu-id="f187e-304">Для динамического обновления этих новых экземпляров запустите приложение **узел applydynamicupdate** .</span><span class="sxs-lookup"><span data-stu-id="f187e-304">To dynamically update these new instances, run the **ApplyDynamicUpdate** application.</span></span>
