---
description: 'Дополнительные сведения: задача 3. Создание панели элементов и панелей PropertyGrid'
title: Задача 3. Создание области элементов и сетки свойств
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: c07bfc2f974018cb0d789a6cc1181f9bed861382
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755167"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a><span data-ttu-id="6f94a-103">Задача 3. Создание области элементов и сетки свойств</span><span class="sxs-lookup"><span data-stu-id="6f94a-103">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>

<span data-ttu-id="6f94a-104">В этой задаче вы создадите панели **элементов** и **PropertyGrid** и добавите их в переразмещенную конструктор рабочих процессов Windows.</span><span class="sxs-lookup"><span data-stu-id="6f94a-104">In this task, you will create the **Toolbox** and **PropertyGrid** panes and add them to the rehosted Windows Workflow Designer.</span></span>

<span data-ttu-id="6f94a-105">Для справки код, который должен находиться в файле MainWindow.xaml.cs после выполнения трех задач в процессе повторного [размещения Конструктор рабочих процессов](rehosting-the-workflow-designer.md) ряд разделов, приведен в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="6f94a-105">For reference, the code that should be in the MainWindow.xaml.cs file after completing the three tasks in the [Rehosting the Workflow Designer](rehosting-the-workflow-designer.md) series of topics is provided at the end of this topic.</span></span>

## <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a><span data-ttu-id="6f94a-106">Создание области элементов и ее добавление к сетке.</span><span class="sxs-lookup"><span data-stu-id="6f94a-106">To create the Toolbox and add it to the grid</span></span>

1. <span data-ttu-id="6f94a-107">Откройте полученный проект Хостингаппликатион, выполнив процедуру, описанную в разделе [Задача 2. размещение конструктор рабочих процессов](task-2-host-the-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="6f94a-107">Open the HostingApplication project you obtained by following the procedure described in [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md).</span></span>

2. <span data-ttu-id="6f94a-108">В области **Обозреватель решений** щелкните правой кнопкой мыши файл *MainWindow. XAML* и выберите **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="6f94a-108">In the **Solution Explorer** pane, right-click the *MainWindow.xaml* file and select **View Code**.</span></span>

3. <span data-ttu-id="6f94a-109">Добавьте `GetToolboxControl` метод в `MainWindow` класс, который создает <xref:System.Activities.Presentation.Toolbox.ToolboxControl> , добавляет новую категорию **панели** элементов в **область элементов** и присваивает <xref:System.Activities.Statements.Assign> <xref:System.Activities.Statements.Sequence> этой категории типы действий и.</span><span class="sxs-lookup"><span data-stu-id="6f94a-109">Add a `GetToolboxControl` method to the `MainWindow` class that creates a <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adds a new **Toolbox** category to the **Toolbox**, and assigns the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activity types to that category.</span></span>

    ```csharp
    private ToolboxControl GetToolboxControl()
    {
        // Create the ToolBoxControl.
        var ctrl = new ToolboxControl();

        // Create a category.
        var category = new ToolboxCategory("category1");

        // Create Toolbox items.
        var tool1 =
            new ToolboxItemWrapper("System.Activities.Statements.Assign",
            typeof(Assign).Assembly.FullName, null, "Assign");

        var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
            typeof(Sequence).Assembly.FullName, null, "Sequence");

        // Add the Toolbox items to the category.
        category.Add(tool1);
        category.Add(tool2);

        // Add the category to the ToolBox control.
        ctrl.Categories.Add(category);
        return ctrl;
    }
    ```

4. <span data-ttu-id="6f94a-110">Добавьте в `AddToolbox` класс закрытый метод `MainWindow` , поместив **область элементов** в левый столбец сетки.</span><span class="sxs-lookup"><span data-stu-id="6f94a-110">Add a private `AddToolbox` method to the `MainWindow` class that places the **Toolbox** in the left column on the grid.</span></span>

    ```csharp
    private void AddToolBox()
    {
        ToolboxControl tc = GetToolboxControl();
        Grid.SetColumn(tc, 0);
        grid1.Children.Add(tc);
    }
    ```

5. <span data-ttu-id="6f94a-111">Добавьте вызов `AddToolBox` метода в `MainWindow()` конструктор класса, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="6f94a-111">Add a call to the `AddToolBox` method in the `MainWindow()` class constructor as shown in the following code:</span></span>

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();

        this.AddToolBox();
    }
    ```

6. <span data-ttu-id="6f94a-112">Нажмите клавишу <kbd>F5</kbd> , чтобы создать и запустить решение.</span><span class="sxs-lookup"><span data-stu-id="6f94a-112">Press <kbd>F5</kbd> to build and run your solution.</span></span> <span data-ttu-id="6f94a-113">Должна отобразиться **панель элементов** , содержащая <xref:System.Activities.Statements.Assign> <xref:System.Activities.Statements.Sequence> действия и.</span><span class="sxs-lookup"><span data-stu-id="6f94a-113">The **Toolbox** containing the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activities should be displayed.</span></span>

## <a name="to-create-the-propertygrid"></a><span data-ttu-id="6f94a-114">Создание области PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="6f94a-114">To create the PropertyGrid</span></span>

1. <span data-ttu-id="6f94a-115">В области **Обозреватель решений** щелкните правой кнопкой мыши файл *MainWindow. XAML* и выберите **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="6f94a-115">In the **Solution Explorer** pane, right-click the *MainWindow.xaml* file and select **View Code**.</span></span>

2. <span data-ttu-id="6f94a-116">Добавьте `AddPropertyInspector` метод в класс, `MainWindow` чтобы разместить панель **PropertyGrid** в крайнем правом столбце сетки:</span><span class="sxs-lookup"><span data-stu-id="6f94a-116">Add the `AddPropertyInspector` method to the `MainWindow` class to place the **PropertyGrid** pane in the rightmost column on the grid:</span></span>

    ```csharp
    private void AddPropertyInspector()
    {
        Grid.SetColumn(wd.PropertyInspectorView, 2);
        grid1.Children.Add(wd.PropertyInspectorView);
    }
    ```

3. <span data-ttu-id="6f94a-117">Добавьте вызов `AddPropertyInspector` метода в `MainWindow()` конструктор класса, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="6f94a-117">Add a call to the `AddPropertyInspector` method in the `MainWindow()` class constructor as shown in the following code:</span></span>

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();
        this.AddToolBox();

        this.AddPropertyInspector();
    }
    ```

4. <span data-ttu-id="6f94a-118">Нажмите клавишу <kbd>F5</kbd> , чтобы создать и запустить решение.</span><span class="sxs-lookup"><span data-stu-id="6f94a-118">Press <kbd>F5</kbd> to build and run the solution.</span></span> <span data-ttu-id="6f94a-119">Все области **элементов**, конструктор рабочих процессов и панели **PropertyGrid** должны отображаться, а при перетаскивании <xref:System.Activities.Statements.Assign> действия или <xref:System.Activities.Statements.Sequence> действия на холст конструктора сетка свойств должна обновляться в зависимости от выделенного действия.</span><span class="sxs-lookup"><span data-stu-id="6f94a-119">The **Toolbox**, workflow design canvas, and **PropertyGrid** panes should all be displayed, and when you drag an <xref:System.Activities.Statements.Assign> activity or a <xref:System.Activities.Statements.Sequence> activity onto the design canvas, the property grid should update depending on the highlighted activity.</span></span>

## <a name="example"></a><span data-ttu-id="6f94a-120">Пример</span><span class="sxs-lookup"><span data-stu-id="6f94a-120">Example</span></span>

<span data-ttu-id="6f94a-121">Файл *MainWindow.XAML.CS* теперь должен содержать следующий код:</span><span class="sxs-lookup"><span data-stu-id="6f94a-121">The *MainWindow.xaml.cs* file should now contain the following code:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;
// dlls added.
using System.Activities;
using System.Activities.Core.Presentation;
using System.Activities.Presentation;
using System.Activities.Presentation.Metadata;
using System.Activities.Presentation.Toolbox;
using System.Activities.Statements;
using System.ComponentModel;

namespace HostingApplication
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        private WorkflowDesigner wd;

        public MainWindow()
        {
            InitializeComponent();
            RegisterMetadata();
            AddDesigner();
            this.AddToolBox();
            this.AddPropertyInspector();
        }

        private void AddDesigner()
        {
            // Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            // Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            // Load a new Sequence as default.
            this.wd.Load(new Sequence());

            // Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }

        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }

        private ToolboxControl GetToolboxControl()
        {
            // Create the ToolBoxControl.
            var ctrl = new ToolboxControl();

            // Create a category.
            var category = new ToolboxCategory("category1");

            // Create Toolbox items.
            var tool1 =
                new ToolboxItemWrapper("System.Activities.Statements.Assign",
                typeof(Assign).Assembly.FullName, null, "Assign");

            var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
                typeof(Sequence).Assembly.FullName, null, "Sequence");

            // Add the Toolbox items to the category.
            category.Add(tool1);
            category.Add(tool2);

            // Add the category to the ToolBox control.
            ctrl.Categories.Add(category);
            return ctrl;
        }

        private void AddToolBox()
        {
            ToolboxControl tc = GetToolboxControl();
            Grid.SetColumn(tc, 0);
            grid1.Children.Add(tc);
        }

        private void AddPropertyInspector()
        {
            Grid.SetColumn(wd.PropertyInspectorView, 2);
            grid1.Children.Add(wd.PropertyInspectorView);
        }

    }
}
```

## <a name="see-also"></a><span data-ttu-id="6f94a-122">См. также</span><span class="sxs-lookup"><span data-stu-id="6f94a-122">See also</span></span>

- [<span data-ttu-id="6f94a-123">Повторное размещение конструктора рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="6f94a-123">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="6f94a-124">Задача 1. Создание нового приложения Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="6f94a-124">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="6f94a-125">Задача 2. Размещение конструктора рабочих процессов</span><span class="sxs-lookup"><span data-stu-id="6f94a-125">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
